# BL-UsbMach 5 axis USB Stepper controller boards

## Introduction

The primary purpose of this repo is to gather general information regarding these USB CNC 5 axis controllers and, if possible, reverse engineer it for customization. They are widely sold and poopular due to low price, but very little is known about them, and the accompanying documentation is scarce and mostly in chinese.

## History and Motivation

I bought a chinese 5-axis 3020 cnc, and it's pretty awesome. However, installation instructions are only for Windows, and control is aimed only at MACH3. I'm a Linux user, so I tried connecting it to my Linux box, and I came up against the first wall: USB enumerates the device, but there is no driver. Two days googling didn't turn up any driver either.
TL;DR: I ended up having to set up a Windows VM within my Linux box just to make a test installation.
Within the Windows VM the device was immediately recognized, and the drivers were automatically installed. A quick install of MACH3 and the relevant customizations showed the cnc working as expected. But within a Windows VM...

I got more curious, so I opened the stepper controller box to see what the control electronics look like. Surprisingly, the controller board shows an STM32F103 uC. Obviously there's a lot of info about that, but I still couldn't find anything about the USB VID/PID etc. Then, I realized that the controller showed a bunch of unused connectors. That got me more curious, especially for spindle speed control, because out of the box the spindle speed is controlled manually with a potentiometer on the stepper controller box, and not from MACH3.

I started looking for manuals and schematics, and hit the 2nd wall: almost no info is available only beyond some install instructions and pin naming diagrams.

Finally, the obvious questions: what firmware do you get when you buy these boards? A variant of GRBL? Something else?

## Goals

 * Gather manuals, wiring diagrams, schematics, documents, differences between variants and versions, and in general any information about these controller boards
 * Gather information about practical extensions, such as spindle pwm control, connection of a frequency converter, use of the board's IO pins, etc
 * Gather contributed tutorials and how-tos, e.g.: for flashing or implementation of additions usually not included in stock purchases
 * Reverse engineer the board schematics
 * Reverse engineer the firmware, or at least replace it with an alternative
 
Gathering of restricted information, such as uploading the version of MACH3 that usually accompanies these boards, is out of the scope of this repo.

## Contributing

If you have a document or manual or some file that is not in this repo, please make a PR with it. The more information we gather, the better for everyone.
If you find a typo/bug, or some text section that should be added or rewritten, please make a PR with your corrections.
If you think you can investigate some specific part of the board, e.g.: recreate the schematic, get datasheets, figure out how to dump the firmware, flash a different firmware, etc, please open an issue and propose your ideas to pursue. The  board seems great and cheap, but if it could be customized, it would be even better, and in order to do that y

## Issue Policy

I do not provide any kind of service, nor do I intend to explicitly support or help projects or needs from others. Opening of issues is meant primarily for tracking contributions or ongoing investigations from community members, or for pointing out typos and eventual bugs in possible scripts/tools/sources. 
That said, I don't mind discussions, as long as you're polite and respectful of others. However, pleae be explicit and clear with regard to your purpose when opening an issue.

## PR Policy

PRs are meant for uploading files and in general making contributions. General discussions should be held in an issue. Discussions specific to a PR should be held in that PR.
If your PR is accepted and merged, congratulations! You've contributed to the community, and your name was added to the repo history.
If your PR is reviewed, just make the requested corrections to move forward.
If your PR is closed, don't be discouraged. Your motivation is important. Keep looking for other ways to contrubute!

# Useful links

Links to external resources belong here.

https://github.com/mirecta/grbl : Port of grbl to STM32F103. The UsbMach is mentioned, and a 3-wire patch is proposed.
