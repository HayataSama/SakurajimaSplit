# SakurajimaSplit

SakurajimaSplit is a 6x3 column stagger split mechanical keyboard. It's inspired by [Corne](https://github.com/foostan/crkbd), [Kyria](https://github.com/splitkb/kyria) and [Elephant42](https://github.com/illness072/elephant42).

![SakurajimaSplit Fully Built](./pics/built1.jpg)

> [!NOTE]
> The master branch contains the most recent commits and is not meant for production. Gerbers and production files will be available as a github release.
>
> This project was was made in KiCad 9.0 and FreeCAD 1.0. In addition to KiCad's default libraries, I used the [ebastler's marbastlib](https://github.com/ebastler/marbastlib) footprint and symbol library and [zykrah's kicad-kle-placer](https://github.com/zykrah/kicad-kle-placer) plugin. Using other versions may introduce bugs and/or inconsistencies therefore is discouraged.

## Features

- QMK compatible
- Cherry MX switch profile
- 3-Key thumb cluster
- 10-Degree sideways tilt
- SSD1305 OLED display
- W25Q Flash Storage for storing animations
- USB-C connector

## Motivation

I've been interested in mechanical keyboard for a few years now. I got my endgame keyboard (Mode Envoy) a while back and it's been my daily driver since. A while agoI suddenly became interested in split mechanical keyboards. Something about them being tiny and portable, also having this cyberpunky feeling to the made them appealing to me.
Apparently ortholinear keyboards are also more comfortable to type on. (not sure how true this is but now that I've built this keyboard and am using it on daily basis, I should say it feels so damn nice to type on!)
I'm also an electrical engineering student and I have some experience designing PCBs. With all these in mind I thought to myself why not? why not build a fully custom keyboard, tailored to my needs? And here we are!

## Why Sakurajima?

Because Mai Sakurajima is the best girl.

## The Journey and Some Notes

This was my first experience designing a keyboard (and a handheld device in general). My approach for designing the layout was to put my fingers on a piece of paper (in the supposedly most comfortable position) and mark under each fingertip to find the best home row position. Then I measured the distance between keys and rounded them up to the closest standard value. (keyboard "u" units).
For the thumb cluster in addition to the fingertip, I also marked my thumb joint (MCP joint?) on the paper to find the center of the circle where the thumb keys would be placed. Then I did some basic geometry to find the angle and distance of each key with respect to the center.
I don't know if this is the best approach or even a good approach, but it was fairly easy to do and the end result is great.

Let's talk about electronics. I know I've used a lot a questionable components in this keyboard, one's that are not generally common in keyboards or are not easily found. Believe me, I asked myself this question so many times too! Jokes aside, there were 3 main factors contributing to the component selection. First, this is a one off keyboard that I'm making for myself, so price doesn't matter. Second, I want to try using different components in my board from what I usually use, to gain more experience about electronics and get a feeling for different components. And third, I live in a heavily sanctioned country, so I don't have easy access to many electronic components, and I have to work with what is available on the market.
This lead to some weird and frustrating design decisions that I'll soon regret.

The first mistake was choosing an SSD1305 OLED display. I chose this specific display because the panel was much larger than most common OLED displays. The OLED driver is very similar to SSD1306 but is not officially supported by QMK. This is not a big problem by itself as QMK is an open-source firmware and you're free to modify to OLED codes to add support for your display. The main problem is that this OLED module is 128x33 pixels and not 128x32 pixels like most OLED modules are! This creates many memory related issues and incompatibility with QMK which I have yet to solve!

The next not so great decision was using a WSON package for hand soldering! The voltage regulator IC is very very tiny and without proper tools (like a microscope and a hotplate) is very difficult to hand solder. I don't know what I was thinking when picking parts, but now I've learned (the hard way!) to pay more attention to choosing component packages.

A big missed opportunity was not making this keyboard wireless. I could probably use an STM32 W-series MCU to make this keyboard Bluetooth-enabled. At the time, I chose to not go this route mainly because I wanted to keep it simple and build something that actually works. I might create a new revision for this keyboard, fix the stated issues and add new features like wireless connectivity in the future.

## Limitations

QMK doesn't currently support W25Q flash storages. I will write a driver for these ICs and add it to QMK in the future, but for now this chip is basically useless.

## Acknowledgements

I have to say a big thank you to [Joe Scotto](https://youtube.com/@joe_scotto) for his YouTube channel which was big source of motivation and guidance in this project and [ebastler](https://github.com/ebastler) for his great KiCad library which made my life a lot easier! Also a big thank you to all the people active in the mechanical keyboard community, open-source contributors and the QMK team!
