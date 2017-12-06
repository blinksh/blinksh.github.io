---
layout: post
title: "Navigating the Blink Shell"
description: "Navigating the Blink Shell"
keywords: "blink, shell"
---

# Introduction to Blink

Blink is a shell that allows you to connect to remote machines, use mosh, and has full SSH support.  You can use it to connect to other servers, interface with your Raspberry Pi, or even write code!  The shell is ready to go, blinking with anticipation as you discover its potential.

# Using Blink Shell

Using Blink shell is similar to most other terminals - you simply type commands and hit RETURN.  Just like in Bash or similar UNIX shells, you can press the up arrow to access the history of previous commands.  You can type help to access Blink’s online help, mosh to access the mosh mobile shell, `ssh` to connect via SSH, or `ssh-copy-id` to copy SSH keys.

![]({{ site.baseurl }}/assets/images/posts/2017/navigating-the-blink-shell/image1.gif)

For example, you can type:

```
mosh carlos@192.168.1.5
```

To connect to your desktop computer or Raspberry Pi (assuming 192.168.1.5 is the IP address of the device.).

# Blink Shell Gestures

You can use a variety of finger gestures with Blink Shell.  To create a new shell, use two fingers and tap.  Two finger drag will close a shell, and one finger slide will move between active shells.

![]({{ site.baseurl }}/assets/images/posts/2017/navigating-the-blink-shell/image5.gif)

# Blink Shell SmartKeys

SmartKeys provide special keys to use in your terminal session.  They are hidden when an external keyboard is connected.

- Modifiers (i.e. CTRL, ALT, and ESC) for key combinations like CTRL+C. Alt is ⌥.
 <!-- ![]({{ site.baseurl }}/assets/images/posts/2017/navigating-the-blink-shell/image3.png) -->
- Directional arrows
- Scrollable area in the center with more keys
- Alternate keys after taping ALT (function keys on central area plus cursor keys like Home, End, Page Down and Page Up)
- Holding a modifier instead of taping allows you to chain multiple combinations, which is especially useful in applications like Emacs where you use chains like C-x, C-c.

![]({{ site.baseurl }}/assets/images/posts/2017/navigating-the-blink-shell/image2.gif)

# Configuration

![]({{ site.baseurl }}/assets/images/posts/2017/navigating-the-blink-shell/image4.jpg)

In the configuration section, you can configure the following:

- Hosts: Create hosts in your `~/.ssh/config` and access them just with the hostname. More info...
- Keys: Create SSH key pairs for enhanced security and password-less convenience when accessing your servers.  More info...
- Appearance: Personalize the terminal to your tastes.  You can change themes, fonts, or even upload your own.  More info...

> (To know more... - Each section will contain a “Read more“ section with a list of other articles: “How to use SSH Keys with Blink Shell”, etc…)

# Support and Community

We sincerely appreciate your support and use of Blink.  You can count on us to continue improving Blink.

You can contact us via email, but ideally it is best to file issues on our GitHub so that all of the community is aware of the issue.  Not only does it help make Blink better, but another user may have a resolution to your issue.  When reporting a problem, please give as much detailed information as possible describing what you were doing when the application crashed or acted unexpectedly.  Screenshots usually help when there is a problem with the interface.

**VERY IMPORTANT:  Reporting a problem in your review in the app store will not help us solve issues that you might be experiencing.  Please make sure to contact us, too!**

When a crash occurs in the application, we receive a report.  When this happens, please email us or open an issue on GitHub.

Have an idea for a feature?  Join our community on GitHub to send us your suggestions!  We want to make Blink the most awesome terminal ever!
