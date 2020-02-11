---
title: Stretch Yourself
date: 2016-04-11 12:00:00
excerpt: Lately, I’ve been trying to be a bit better about my posture and at work.
type: post
blog: true
tags:
    - Tech
---

Lately, I’ve been trying to be a bit better about my posture and at work. As many know, working hunched over in front of a computer all day can take a toll after awhile. To combat this, I decided to make it a habit to stretch at least a little bit every 30 minutes.

I also wouldn’t mind gaining some skill with Python, and I thought Python seemed like a fair tool to help me set a reminder to stretch. Certainly there are other ways to set reminders on your computer, but this is the cool way to do it (maybe). First things first, I had to [download](https://www.python.org/downloads/) and install Python on my Windows computer. With that done, I went ahead and opened up a simple text editor (I like [Sublime](https://www.sublimetext.com/3)) to create my little Python script.

The first thing I needed to figure out with Python was how to make an alert of some sort pop up to remind me to stretch. A tad of time with Mr. Google led me to use the `ctypes` library that comes with the installation of Python.

```python
import ctypes

ctypes.windll.user32.MessageBoxW(0, "Time to stretch", "Message", 1)
```

Awesome. That works. But how do I get it to remind me every thirty minutes? A little more searching online led me to the `sched` and `time` libraries. I then mixed in the `datetime` library to log the time when the alert appears and I had my final solution.

```python
import ctypes
import sched, time from datetime
import datetime

s = sched.scheduler(time.time, time.sleep)

def do_something(sc):
    print("It's " + datetime.now().time().strftime("%H:%M:%S") + "! Time to stretch!")
    ctypes.windll.user32.MessageBoxW(0, "Time to stretch", "Message", 1)
    
    sc.enter(60*30, 1, do_something, (sc,))
    
s.enter(60*30, 1, do_something, (s,))
s.run()
```

I assume this is where Python-studs yell in frustration. I would guess this could be even more minimal and cleaned up some, but it’s working for now. If you’re that Python-stud, I’d love to know how you would clean it up.

Finally, I made a small batch file to start the script and put it in my startup folder. And there you have it. I was able to stretch some Python skills as well as my stagnant muscles. I hope this helps you with your posture and maybe even your computer skills too!
