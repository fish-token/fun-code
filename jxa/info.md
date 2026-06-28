# JXA Script Info

JXA stands for JavaScript for Automation. JXA let's you automate long or repetitive tasks using extended JavaScript. The limitations of this language include:

- Only works on macOS 10.10 Yosemite or later
- Heavily restricted by security (like many other scripting tools provided by Apple, requires explicit permission to run)
- Doesn't have the greatest documentation (sorta 'deserted' by Apple, still very powerful however)

JavaScript for Automation can still do many powerful things however, including:

- Full disk access
- Send keystrokes and mouse events
- Integrate with native and 3rd party apps like Google Chrome or Photoshop

## Keep in mind

There are some important things to remember with thsee kinds of scripts.

- Always check the contents before granting sudo access
- Some scripts may work on certain macOS versions and not on others
    - All the scripts in this repository will only work for macOS 10.12 Sierra or higher due to the use of ES6+ JavaScript
- Apple makes it a bit hard to run these things without technical knowledge, for good reason. If you encounter difficulties, thats to be expected
