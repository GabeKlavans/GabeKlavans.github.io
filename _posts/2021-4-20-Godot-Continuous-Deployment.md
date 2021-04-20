---
layout: post
title: Godot Continuous Deployment from GitHub to Itch.io 
---

#### Automatically build and upload your GitHub-hosted game to Itch.io!

For context, Tanner and I have been working on a 2D game using [Godot](https://godotengine.org/), a game engine that is just a pleasure to work in.

## TL;DR: Here's the [workflow file](https://github.com/SuGar33-Coding/The-Grand-Battle-Arena/blob/working/.github/workflows/deploy_game.yml)
```
# Whenever a push is made to the branch then run the job
on: 
  push:
    branches:
      - main # Replace with whatever branch you want

env:
  GODOT_VERSION: 3.2.3 # Replace with your version
  EXPORT_NAME: game-name

jobs:
  export-windows:
    name: Windows
    runs-on: ubuntu-latest
    container:
      image: barichello/godot-ci:mono-3.2.3
    steps:
      - name: Checkout
        uses: actions/checkout@v2
        with:
          lfs: true
      - name: Setup
        run: |
          mkdir -v -p ~/.local/share/godot/templates
          mv /root/.local/share/godot/templates/${GODOT_VERSION}.stable.mono ~/.local/share/godot/templates/${GODOT_VERSION}.stable.mono
      - name: Windows Build
        run: |
          mkdir -v -p build/windows
          godot -v --export "Windows" ./build/windows/$EXPORT_NAME.exe
      - name: Upload Artifact
        uses: actions/upload-artifact@v1
        with:
          name: windows
          path: build/windows
      - name: Upload to Itch.io
        uses: josephbmanley/butler-publish-itchio-action@master
        env:
          BUTLER_CREDENTIALS: ${{ secrets.BUTLER_CREDENTIALS }}
          CHANNEL: windows
          ITCH_GAME: game-name # Name of your game on Itch.io
          ITCH_USER: itch-user # Your Itch.io account name
          PACKAGE: build/windows
          
  export-html5:
    name: HTML5
    runs-on: ubuntu-latest
    container:
      image: barichello/godot-ci:mono-3.2.3
    steps:
      - name: Checkout
        uses: actions/checkout@v2
        with:
          lfs: true
      - name: Setup
        run: |
          mkdir -v -p ~/.local/share/godot/templates
          mv /root/.local/share/godot/templates/${GODOT_VERSION}.stable.mono ~/.local/share/godot/templates/${GODOT_VERSION}.stable.mono
      - name: HTML5 Build
        run: |
          mkdir -v -p build/html5
          godot -v --export "HTML5" ./build/html5/index.html
        # cd $EXPORT_NAME
      - name: Upload Artifact
        uses: actions/upload-artifact@v1
        with:
          name: html5
          path: build/html5
      - name: Upload to Itch.io
        uses: josephbmanley/butler-publish-itchio-action@master
        env:
          BUTLER_CREDENTIALS: ${{ secrets.BUTLER_CREDENTIALS }}
          CHANNEL: html5
          ITCH_GAME: game-name # Name of your game on Itch.io
          ITCH_USER: itch-user # Your Itch.io account name
          PACKAGE: build/html5
```
Some important steps to get this working:
1. You have to use butler to [push a build to a channel](https://itch.io/docs/butler/pushing.html) before the automatic Itch.io upload will work. Make sure to use the channel name set in the workflow.
2. You need to add BUTLER_CREDENTIALS containing an [API key from your account](https://itch.io/user/settings/api-keys) to your repository secrets (Repo $\rightarrow$ Settings $\rightarrow$ Secrets)

Throw that code into a workflow file and replace the necessary fields to get up and running quick! 
This particular setup is for exporting and uploading a Windows build for download and an HTML5 build for running in the game's Itch.io page (which may not be exactly optimal depending on the kind of game you're making).

# Exporting the game
The first step is to automatically export the game. You can export from the godot cli with the `godot --export` command. Here we use [godot-ci](https://github.com/marketplace/actions/godot-ci) to achieve this. It runs a docker container with links pointing to the proper Godot builds and uses them to export the game in a headless instance of Godot. It also has support for automatically publishing an HTML5 build to GitHub pages, and if you're using GitLab it can even publish straight to Itch.io (but I'm not ¯\\\_(ツ)\_/¯ )!

The exported artifact is then uploaded to the action's local store, allowing you to download and inspect the contents of the export zip files in the action output on GitHub. These can also be used for further processing in another workflow, if desired.

## Alternative action
An alternative action for exporting would be [Godot Export](https://github.com/marketplace/actions/godot-export), which is probably a bit lighter and supports automatically creating releases as well, which is cool.

# Uploading the game
The next step is simply to use the [Butler Push](https://github.com/marketplace/actions/butler-push) action to upload the zips to Itch.io. This one's as straightforward as it seems. You fill in the proper values in the env attribute and it will read in from the repo secret and push to the channel you set up earlier (you set all that up, right).

Viola! Automatic Itch.io builds and uploads. Now it'll be much easier to haphazardly share your incremental progress with friends and Internet strangers.