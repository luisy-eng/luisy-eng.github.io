---
layout: essay
type: essay
title: "My thoughts on simple CPU Design Project"
# All dates must be YYYY-MM-DD format!
date: 2025-01-17
published: false
labels:
  - Review
  - Computer Engineering
  - MIPS
---

If I had to tell anyone about an experience during my time in college where I felt like a Computer Engineer this would have to be it.
Not necessarily because the project itself involved designing and a direct application of what we have learned in class..
but.... more so the issues, horrors, time spent and the samount of time involved trying to foigure out what exactly we had to do.

Let me give a bit of background so that we can relate a bit.
This project started with a 50 page pdf, five different files talking about instructions, a ton of reading that felt completely alien to me.
The lab was proctored by a TA, who mind you was not a computer or electrical engineer.
I remember asking for help and looking at my TA's utterly confused face as they moved on to tell me
"I have no idea what to do or how to start this.."
Imgine my concerns... this is literally the final project to my Computer Architecture class and the TA has absolutely no idea what is going on.
I proceeded to make the best sense out of all the tasks being described, System Verilog at this time isnt something I can say im terribly comfortable either...
I realized a few issues with some of the logic, and also issues with the PDF and tasks. I challenged the TA about these issues and they shrugged and told me to just place the wrong answer.
This to me isnt a very engineering mentality so I decided to ignore that statement.
The first issue I found was in the instructions being asked to implement.
We were ask to implement a set of instructions that add... only that there was some weird issues
the pdf was asking to add 1+3 which would equal 4...
Its simple right except the pdf said 1 + 3 = 10...
Ok if this alone doesnt say there are some serious issues in the instructions I dont know exactly what else does.
There were many other issues in the PDF highliting instructions to this task so I decided to go to the Proffesors office hours challenge this project.
The professor agreed that the material seemed wrong. So they told me to implement what I can and focus on the what I can get done.
A lot of my peers decided to make a adder instead of what the instructions said to do which was a 5 stage processor that can execute specific instructions.
The way I took the professors words, was to basically make it happen and this started the beatiful 3 weeks of amazing lack of sleep, healthy dose of stress till 4am and pulling my hairs trying to understand how to make a pipeline.
I figured jumping into the task from a blank slate with literally no idea where to start was probably not the best approach...
So what did I do, draw and read! Yes I needed to genuinely understand what a pipeline was how things work and because I like simple things I choose to draw as I learn it.

<p align="center">
    <img width="300px" src="../img/PipeLine.png">
</p>

I asked myself, "What exactly is a pipeline?"
No not the book definition that uses a bunch jargon no one really understands. But in human terms..
Well to me this came as, a sequence of steps in a guided order going through stages where the instructions get to each go step by step until it reaches the end and executes the operation fully.
Where in each section of the stages there are con current working mechanisms.

<p align="center">
    <img width="300px" src="../img/In_Pipe.png">
</p>

My visual representation of it...
I decided to leave the idea of addresses and logic to decide and focus on the actual architecture first.
I knew that there is a five stage process but is that reallyt it?
Can just knowing there are five stages make me a good engineer ready to takle this project?
Absolutely not...
I needed to understand how the instructions even come into this pipeline.
This great well in class we learned about the cache and RAM. But.. I have an issue...
How do I simulate a cache in EDAPlayground. So I realized I can just create a fixed order of instructions in a testbench.
In other words other than testing my code the testbench can act as my main memory. Great thats one problem solved!
Now how do I do that? What is part of an instruction?

In a instruction we have a few parts and each instruction has a different format.
Ok this is not so simple like I initially thought.
I wrote the three simple instructions:
Add
Branch
Load

All three have a different format, First thing I decided to start with was the op code. In in simple terms the value that tells the Pipeline what operation the instructions are trying to execute, wether its to add or load or jump to another instruction.
Next part I needed to identify the components of ADD, this is a register to register addit

<p align="center">
    <img width="300px" src="../img/Spec_Ex.png">
</p>

<p align="center">
    <img width="300px" src="../img/Brach.png">
</p>

<p align="center">
    <img width="300px" src="../img/Ex_or.png">
</p>

---
