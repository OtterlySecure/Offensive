---
layout: post
title: "EDR Evasion Lab: Part 1"
Author: Chaos Otter
date: 2021-08-12
categories: EDR, Evasion
tags: implant. edr, evasion, redteam     # TAG names should always be lowercase
# image:
#   src: /assets/img/favicons/eac2.png
#   width: 1200   # in pixels
#   height: 540 # in pixels
#   alt: image alternative text
---

# EDR Evasion Lab: Part 1

## Genesis

In January 2021, I finally passed Offensive Security's OSCE course and exam after a couple of failed attempts for various. While this was super exciting to have tackled this milestone in my personal development, it did leave me wanting more, but I did not know what exactly. Exploit dev was never something that I was really interested in and honestly was scared to tackle for the longest time. While I enjoyed learning the process to be successful in the OSCE exam, I never felt like I would really use the skills in my day job, mostly due to the techniques being very outdated by today's standards. That being said, it did push me down the path I have chosen to take for 2021 in terms of personal skill development.

In late April, I started playing around with some dotNet development, as a result of some training that was offered internally where I work. I was not able to sit in on the training but with a little sneaky social engineering, I asked, I was able to get materials from the workshop to look over. 

The workshop was an introductory look at how to create a basic dropper in C# and I am sure the live version had even more good stuff, but I had enough to start picking things apart and building my own droppers as a result. 

Having never really worked with C# it took me awhile to understand what the provided code was doing and more importantly *why* it was doing what it was. Without any formal programming training or schooling, I have to hack my way through most everything and this was no exception. Within a day or so, I had managed to rework the code in the samples to take advantage of a new C2 channel concept I had worked up the weeks previously. It was crass, but it worked and that was a win for me.
Fast-forward a bit and I had leveraged my new-found skills to create several droppers with different capabilities. Not bad for a workshop I didn't take, right? 

One glaring issue had been staring me in the face the entire time I was starting this development process, and it came time to face it head on. The reality was that my tooling was useless in the real world because it was going to get caught basically every time. Yeah, I could pop calc.exe with no issues but to actually use this tooling in the real world, it was going to get caught...right? 

Sure if I loaded up some meterpreter shellcode as my payload and fired off my dropper, it would get caught right? Well, it depends. With no attempts at obfuscation, most certainly, but with some extra work maybe not.

How much extra work? Hmmm...

...and this is where the rabbit hole started.

## The Needful

Early on in this process I was just testing my work against Windows Defender to see what worked and what didn't and that is an okay place to start, but I don't believe that it will take you very far, nor lead to much success. I knew I needed a better proving ground, if you will, to put my work to the test and see what I could learn from it in the process.

I stated doing cursory research, googling and asking friends their thoughts, on what would some good tools, ideally open source and/or cheap/free (if it's free, It's for me!). I was aware of OSSEC and WAZUH already but wanted to know if there were any other good EDR (Endpoint Detection and Response) tools out there. Sadly the friends I asked did not help much, but Google came through for me. 

Google pointed me to a one-hour webcast put on by Black Hills Information Security on May 14th entitled *[Your Free and Open Source EDR Options!](https://youtu.be/yrFnlbwFG_E)*. BINGO! Great place to start. 

![Google Results](/assets/img/google_edr.png)

In the webcast, there were five different EDR solutions highlighted: OSSEC, WAZUH, Velociraptor, Elastic Endpoint Security (formally Endgame) and Open EDR from Comodo. I knew there had to be some good options, but I honestly did not expect that many. 

While the presenter did a good job of highlighting some benefits and reasons why each solution could be chosen, it did leave me with one question. Which one is the best???

Now, before we go any further, let me be the first to say that no tool makes one secure. There is no "best" for every situation and any tools or solution's effectiveness is ultimately up to the people operating and tuning it. 

*People > Technology*.

I firmly believe that with the right people and processes in place, an organization can secure itself and protect itself extremely well regardless of technology.

With that being said, I wanted to know which solution was better at detecting and preventing execution of the tooling I was creating. 

So the task was simple — start with out-of-the-box implementation and rule sets of each solution and determine which of them was the toughest to evade.

The process looks something like this:
- Build out each solution in one of my labs.
- Document the build outs and publish here — cuz why not?
- Start with publically available tools to baseline what gets caught out of the gate.
- Implement various evasion techniques on said public tools, one technique at a time. 
- Start stacking techniques until evasion is possible across all solutions.
- Then attempt to tune each solution to detect previously successful attempts
- ...
- ...
- tbd?

While I wanted to go all *Mythbusters* on this and turn this into a fully scientific experiment of sorts, I really do not have the cycles to do this, but I want to do my best to do everything in a controlled manner so that others could replicate what I am doing and have similar results/lessons learned.

This is going to be a many part series -- how many I am not sure of. Five at a minimum but more than likely 10 or so parts, since I want to document the build outs as well as the testing for each EDR solution.

So stay tuned for next time when *Elastic Endpoint Security* is first on the chopping block. 
  
![Elastic Endpoint Security](/assets/img/elastic_endpoint.png)
