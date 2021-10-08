---
layout: post
title: Ultimate From-Scratch Mechanical Keyboard Build Guide
---

#### For those looking to do the least amount of work possible while maximizing ownership

If you're someone who has garnered enough interest in modern mechanical keyboards to want to build your own with a high degree of thoroughness and control but don't necessarily have the domain knowledge to just jump right in, then you've come to the right place. This guide assumes a generally high comfort-level with technology and a desire to learn. It's gonna be kind of a write-up/build-guide hybrid with some examples from the numberpad I recently built.

Buckle up, cause it's a long one.

# Table of Contents
- [Table of Contents](#table-of-contents)
- [Planning Phase](#planning-phase)
  - [Layout](#layout)
    - [Bells and whistles](#bells-and-whistles)
  - [Keycaps](#keycaps)
  - [Switches](#switches)
- [Design Phase](#design-phase)
- [Build Phase](#build-phase)
  - [Fabrication](#fabrication)
  - [Assembly](#assembly)
    - [Tools](#tools)

# Planning Phase
## Layout
First step is to decide the layout you want. If you haven't thought about it enough yet, Keyboard University has a [great guide](https://keyboard.university/guides/what-size-mechanical-keyboard-should-i-get-g7dbr) for exploring the different common sizes and keyboard layouts. There are also unorthodox layouts like [the split keeb](https://kinesis-ergo.com/split-keyboards/) and [ortho linear](https://www.mechkeybs.com/learn/ortholinear-keyboards-guide/).

![A handy chart](/images/layouts.png "Keyboard layout decision chart")

But that's baby stuff. You're making your own keyboard from scratch. So these common layouts are merely suggestions. Granted, they're very good suggestions, and you should take the time to explore and study what's already been done and what people already like. But if you've got even a little tweak for any of these to make your ideal layout, then that's what you'll want to do.

My build, the [Numpadulator](http://www.keyboard-layout-editor.com/#/gists/76c01d799a5c22b1c113d56c44afb9e6), was a little numpad layout with some extra stuff above the top row.

### Bells and whistles
Extra features that you may want, such as RGB backlighting, rotary encoders (knobs), OLED display panels, and more, can affect your design. Thus, you should decide which of these features you want to end up in your build before you get designing.

## Keycaps
Assuming you aren't also making your own keycaps from scratch (which [you](https://uniqey.zendesk.com/hc/en-us/articles/360008759900-Designing-a-Custom-GMK-Keycap-Set-Guide-) can [do](https://drop.com/talk/475/what-goes-into-creating-a-custom-keycap-set?utm_source=linkshare&referer=5V6HRP)), there are some pretty quick factors you can look at during the search for your desired aesthetic.

Here's a nice little comparison table between the two main types of plastics that keycaps are made from. This comes from a [very good guide](https://switchandclick.com/ultimate-guide-to-picking-a-keycap-set-for-your-mechanical-keyboard/) provided by [switchandclick](https://switchandclick.com/).

| ABS                         | PBT                  |
| --------------------------- | -------------------- |
| Cheaper                     | More expensive       |
| Shiny/Greasy feel over time | Matte, more durable  |
| Smooth                      | Textured             |
| Tend to be thinner          | Tend to be thicker   |
| Quieter, lighter sound      | Louder, deeper sound |

You can decide on the keycaps you want at any point, since you'll very likely end up with MX-style switches so don't fret too much about that.

## Switches
As mentioned, almost all the switches you'll come across are MX-style. That just means they are made using the same profile as the most popular mechanical switch on the market, [Cherry MX](https://cdn.sparkfun.com/datasheets/Components/Switches/MX%20Series.pdf). These switches are generally divided into three categories: Linear, Tactile, and Clicky. Here's another handy table (it is very generalized, there is a lot of variation on the market nowadays).

| Linear                                                             | Tactile                                                | Clicky                                                                            |
| ------------------------------------------------------------------ | ------------------------------------------------------ | --------------------------------------------------------------------------------- |
| No feedback on actuation                                           | Noticeable "bump" (point of resistance) upon actuation | Noticeable bump and click upon actuation                                          |
| Quietest, only the sound of the keycap and stem hitting the bottom | Pretty quiet, bump might add a soft plastic-y sound    | Loud, designed to make an audible click, like a mouse button, for every keystroke |
| Easiest to press (best for touch-typists)                          | Varies widely on how easy to press                     | Medium-to-hardest to press                                                        |
| E.g. Cherry MX Red                                                 | E.g. Cherry MX Brown                                   | E.g. Cherry MX Blue                                                               |


You'll hear talk that the switches actually made by Cherry are among the worst in each category. While this is generally the case for someone seeking an excellent, customized typing experience, it's still a deeply personal/subjective stance and you should never feel like your preference is somehow right or wrong :)

My recommendation is to watch a bunch of comparison videos, get a pick-your-own switch tester like [this one](https://www.ebay.com/itm/383836678335?hash=item595e72e8bf:g:NfUAAOSw9iVhPDTi), push some buttons, and determine which switches to start off with. If you make your keeb hotswappable, (instead of soldering the switches directly on) then you can always go through a few sets of switches on the same board.

I'm a tactile kinda guy, so I put Gateron Kangaroo Ink switches in my main board. They're comparable to the Boba U4Ts, but with a little less pre-travel and a poppier return force/sound. 

To note, you'll see people comparing switches to other switches a lot to describe how something feels. It's unfortunate when you have absolutely nothing to compare to, but after trying a couple switches it can be a very useful way to talk about switches.

# Design Phase
So, you've done a lot of research and thought a lot about what exactly it is that you want to build. Now it's time to start making stuff.

# Build Phase

Great. Now we have everything designed and ready to fabricate, assemble, and use. I'm sure it'll all work perfectly on the first try!

I lied. I don't think it'll work perfectly on the first try. It's actually very normal to have hiccups/oversights for these kinds of things. Your willingness to burn money should dictate how thorough you were in the design phase, as it will cost a lot more to re-fabricate everything for a new design than it will to replace a couple messed up components. If you're very careful and thoughtful, you may be able to scrape by with only a couple minor, mitigable mistakes.

## Fabrication

## Assembly
Now that parts are arriving you can start to put them together.

### Tools
You will need a variety of tools for this kind of work. However, not everyone will end up needing or using the same tools. Instead of buying a bunch of stuff up front that you might not need, if you are patient with the process, you can simply buy as you go to be more efficient.

Here are some things you'll definitely want to consider:
- [TH](## "Through hole") vs [SMD](## "Solder Mount Device") design
  - If you are using all TH components, you will probably get by with just a soldering iron kit
  - If you have some or all SMD components, as I did, then you are DEFINITELY going to want to get a hot air station, like [this one](https://www.amazon.com/YIHUA-959D-Digital-Efficiency-212%C2%B0F-932%C2%B0F-Iron-burn/dp/B08BK3M6YW/), and some [solder paste](https://www.amazon.com/MG-Chemicals-Leaded-Solder-Paste/dp/B00TIC895Y)
    - Using these, you can place down paste where you want to solder on components, affix the component in place, and melt down the solder paste with hot air
    - This creates incredibly clean joints in areas that may be nearly impossible to reach with an iron
    - It also makes removing parts a lot easier
- The size of your screws
  - Some screws that you picked out may be pretty small, or require interesting drivers, like torx
  - Make sure you have a tool that can interface with your screws effectively
- Soldering equipment
  - There's a variety of quality-of-life tools for working with solder, such as fans to suck away the fumes and mats to protect your surfaces
  - Get what will make you feel most comfortable, but I do recommend a fan, as those fumes feel like cancer and it really sucks to have to hold your breath every time you melt solder
- Get flux
  - Just do it (it prevents oxidization which can lead to resistance in solder, bad joints, or other corrosive negative effects)
  - Use it whenever you reflow a joint, or whenever you melt non-flux-core solder
  - It can be in pen form