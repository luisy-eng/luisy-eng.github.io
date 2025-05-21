---
layout: essay
type: essay
title: "Surviving My First Real CPU Design Project"
date: 2025-01-17
published: true
labels:
  - Review
  - Computer Engineering
  - MIPS
---

> _Note:_ This is not a formal report — it’s my personal reflection on a chaotic and memorable CPU design project.

If I had to tell anyone about an experience during my time in college where I felt like a Computer Engineer, this would have to be it.  
Not necessarily because the project itself involved designing and a direct application of what we have learned in class...  
but... more so the issues, horrors, time spent, and the amount of time involved trying to figure out what exactly we had to do.

Let me give a bit of background so that we can relate a bit.  
This project started with a 50-page PDF, five different files talking about instructions, a ton of reading that felt completely alien to me.  
The lab was proctored by a TA, who, mind you, was not a computer or electrical engineer.  
I remember asking for help and looking at my TA's utterly confused face as they moved on to tell me:

> "I have no idea what to do or how to start this..."

Imagine my concerns... This is literally the final project for my Computer Architecture class and the TA has absolutely no idea what is going on.  
I proceeded to make the best sense out of all the tasks being described. SystemVerilog at this time isn’t something I can say I’m terribly comfortable with either...

I realized a few issues with some of the logic, and also issues with the PDF and tasks.  
I challenged the TA about these issues and they shrugged and told me to just place the wrong answer.  
This, to me, isn’t a very engineering mentality — so I decided to ignore that statement.

The first issue I found was in the instructions being asked to implement.  
We were asked to implement a set of instructions that add... only that there were some weird issues.  
The PDF was asking to add 1 + 3, which would equal 4...  
It’s simple, right? Except the PDF said 1 + 3 = 10...

Okay, if this alone doesn’t say there are some serious issues in the instructions, I don’t know exactly what else does.  
There were many other issues in the PDF highlighting instructions to this task, so I decided to go to the professor’s office hours and challenge this project.

The professor agreed that the material seemed wrong. So they told me to implement what I can and focus on what I can get done.

A lot of my peers decided to make an adder instead of what the instructions said to do, which was a 5-stage processor that can execute specific instructions.  
The way I took the professor’s words was to basically _make it happen_, and this started the beautiful 3 weeks of amazing lack of sleep, a healthy dose of stress till 4am, and pulling my hair out trying to understand how to make a pipeline.

I figured jumping into the task from a blank slate with literally no idea where to start was probably not the best approach...  
So what did I do? Draw and read!  
Yes, I needed to genuinely understand what a pipeline was, how things work — and because I like simple things, I chose to draw as I learn it.

<p align="center">
    <img width="300px" src="../img/PipeLine.png">
</p>

I asked myself, "What exactly is a pipeline?"  
No, not the book definition that uses a bunch of jargon no one really understands. But in human terms...  
Well to me this came as: a sequence of steps in a guided order, going through stages where the instructions get to each go step-by-step until it reaches the end and executes the operation fully.  
Where in each section of the stages, there are concurrent working mechanisms.

<p align="center">
    <img width="300px" src="../img/In_Pipe.png">
</p>

My visual representation of it...  
I decided to leave the idea of addresses and logic to the side and focus on the actual architecture first.  
I knew that there is a five-stage process — but is that really it?  
Can just knowing there are five stages make me a good engineer ready to tackle this project?  
Absolutely not...

I needed to understand how the instructions even come into this pipeline.  
This is great — well in class we learned about the cache and RAM. But... I have an issue...  
How do I simulate a cache in EDAPlayground?

So I realized I can just create a fixed order of instructions in a testbench.  
In other words, other than testing my code, the testbench can act as my main memory. Great, that’s one problem solved!  
Now how do I do that? What is part of an instruction?

In an instruction we have a few parts, and each instruction has a different format.  
Okay, this is not so simple like I initially thought.

I wrote the three simple instructions:  
Add  
Branch  
Load

All three have a different format.  
First thing I decided to start with was the op-code.  
In simple terms, it’s the value that tells the pipeline what operation the instruction is trying to execute — whether it's to add or load or jump to another instruction.

Next part I needed to identify was the components of `ADD`.  
This is a register-to-register addition, so I need to reserve bits for the op-code, Register1, Register2 — hence I ended with a 16-bit format.

I proceeded with the same mentality for the rest of the instructions.  
Hence, I actually ended up making a testbench before even working on the pipeline.

This sort of reminded me of what one of my favorite coding professors mentioned to me:

> "Start with testing!"

Sounds weird to think that starting with tests for the program you haven’t made is a practical approach — but in reality, it’s an amazing and helpful mindset.

Tests are like cornerstones to the project.  
As a programmer, we know what certain parts of the program should execute and how it should perform.  
By making a test based on these ideas, we can ensure that as we program, we are aligning to the proper outputs and executions.

<p align="center">
    <img width="300px" src="../img/Spec_Ex.png">
</p>

After all the formatting, I realized that a proper pipeline has ways to handle data hazards — such as read-after-write — and it also needs a way to handle branch jumps.

In class, the simplest way we learned to handle these is by introducing bubbles or `NOP`s.  
This creates a bubble in the pipeline for instructions in case the operation needs to be executed first before the next instruction enters certain sections of the pipeline.

The `ADD` instruction just so happens to be one of those instructions — as well as `Branch Jump`.

Last thing we want is for the branch to be in the pipeline and another instruction is a stage behind it.  
That means we jump, but the instruction behind it still executes.

Hence, I realized I needed a way to tell if a branch instruction was fetched.  
Taking care of this early actually helped a lot in setting up the rest of my project.

<p align="center">
    <img width="300px" src="../img/Brach.png">
</p>

Since I decided to handle branch early in the project, I simply expanded on this for the other categories of branch — whether it was `Compare and Branch if Zero (CBZ)` or `Branch Link`.

The background to expand and take care of any branch instruction was implemented early, making expanding to other types pretty easy.

Okay... I say easy — but let me be honest.  
It wasn’t.

I had no idea how to program this in SystemVerilog.  
Never worked with struct packages before — so I did what any good engineering student in my position would do...

> TO YOUTUBE ACADEMY!!!!

Sooo many videos to sort through. But I had a great strategy to know how to pick a good learning video. I was taught this by a fellow engineering student:

> The best videos are the ones that, when you listen to them, you can’t understand what the person is saying because the foreign accent is so thick...

Crazy enough, after watching so many of these videos, accents became a trivial issue. lol...

<p align="center">
    <img width="300px" src="../img/Ex_or.png">
</p>

One of my goals was to expand my project to do **out-of-order execution**.  
Although I wasn’t able to implement this, I feel like it’s a good future expansion to my project.

Although I understood some of the theories behind it, putting it into practice is a completely different challenge.  
I had to drop this since I was running low on time and my project was due.

But as crazy of an experience this project was, I managed to create something.  
It wasn’t perfect, and it wasn’t revolutionary — but it was my own hard-earned work.

### The Ending...

Let’s get to the funny part: I turned this in, and my TA actually marked me wrong...  
Because I didn’t submit the wrong answer — which is what _he_ had in his answer sheet.

I couldn’t help but laugh.  
I mean... this is how letter-grade education often works.

I obviously decided to challenge this grade and went to the professor’s office, showed them all my work, how I actually revamped the whole project to get a proper working pipeline.

The professor was shocked I was marked wrong.

But we came to find out the TA had never taken that class.  
Apparently, TAs come from a pool of grads and the school assigns them to a class. In this case, I can’t really blame them.

End of story — I got full marks for the project.

Although I felt bad for everyone else... they got marked down for turning in the wrong answer. _facepalm_ Oops... Sorry...

All ends well. At the end, the course material got reworked for the next semester, thankfully —  
and I got to learn a lot more than any other student through this experience.

---
