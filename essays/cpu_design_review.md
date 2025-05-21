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

If I had to tell anyone about an experience during my time in college where I felt like a Computer Engineer, this would have to be it.

Not necessarily because the project itself involved designing and a direct application of what we have learned in class...  
but more so because of the issues, horrors, time spent — and the amount of time involved trying to figure out what exactly we had to do.

---

### The Setup

Let me give a bit of background so we can relate a bit.

This project started with a 50-page PDF.  
Five different files talking about instructions.  
A ton of reading that felt completely alien to me.

The lab was proctored by a TA — who, mind you, was not a Computer or Electrical Engineer.  
I remember asking for help and seeing my TA’s utterly confused face as they told me:

> "I have no idea what to do or how to start this..."

Imagine my concern...  
This was literally the final project for my Computer Architecture class — and the TA had absolutely no idea what was going on.

---

I tried to make sense of all the tasks being described.  
SystemVerilog at this time isn’t something I can say I’m terribly comfortable with either...

Then I started realizing issues — in the logic and in the PDF.  
I challenged the TA about them, and they just shrugged and told me:

> “Just put the wrong answer.”

This, to me, isn’t a very engineering mentality.  
So I decided to ignore that advice.

---

### The First Red Flag

We were asked to implement a set of instructions that add...  
Only — there were some weird issues.

The PDF said to add `1 + 3`, which should equal `4`...  
Except it said:

> `1 + 3 = 10`

Okay. If this alone doesn’t scream “serious issues in the instructions,” I don’t know what does.

There were many other errors in the instructions. So I went to the professor’s office hours to challenge the project directly.

They agreed — the material seemed wrong — and told me:

> “Just focus on what you can implement.”

---

### The Real Project Begins

Most of my classmates just made an adder.  
But the original project was to make a 5-stage processor that could execute specific instructions.

So when the professor said “do what you can,” I took it as:  
**make it happen**.

And that kicked off 3 beautiful weeks of:

- a complete lack of sleep,
- a healthy dose of stress until 4am,
- and me pulling my hair out trying to understand how to make a pipeline.

---

I figured jumping in from a blank slate with zero direction probably wasn’t the best idea...  
So what did I do?

I drew. I read. I learned.  
Because I like simple things, I chose to draw as I learned them.

<p align="center">
  <img width="300px" src="../img/PipeLine.png">
</p>

---

### What Even _Is_ a Pipeline?

I asked myself:

> “What exactly is a pipeline?”

No, not the book definition filled with jargon no one really understands.  
But in human terms.

To me:  
A pipeline is a sequence of steps in a guided order — going through stages, where instructions get to move forward, step by step, until they reach the end and fully execute.  
Each section of the pipeline is working _concurrently_.

<p align="center">
  <img width="300px" src="../img/In_Pipe.png">
</p>

---

I decided to ignore addresses and logic for a moment and just focus on the architecture.

I knew there were five stages — but is that really it?  
Can knowing there are five stages make me a good engineer ready to tackle this?

Absolutely not.

---

### Feeding Instructions

I needed to understand how instructions _even enter_ the pipeline.

In class, we learned about cache and RAM.  
But here’s my issue — how do I simulate a cache in EDAPlayground?

Then I realized something:  
I could create a fixed order of instructions in a testbench.  
Basically, the testbench could act as my main memory.

Awesome — one problem solved.

Now... how do I do that?

---

### What Is an Instruction?

Instructions have different parts.  
Each instruction has a different format.  
Okay, this is not as simple as I thought.

I picked three basic ones:

- `ADD`
- `BRANCH`
- `LOAD`

Each one has a unique layout.  
First thing I tackled was the **opcode** — the value that tells the pipeline what the instruction is trying to do.

Is it an add?  
A load?  
A jump?

For `ADD`, which is a register-to-register operation, I needed to reserve bits for the opcode, Register1, Register2 — so I ended up using a 16-bit format.

I followed the same process for the other instructions.

---

Funny thing: I ended up building my testbench _before_ the pipeline.  
Which reminded me of what one of my favorite professors once said:

> “Start with testing!”

Sounds weird — writing tests for a program you haven’t even made.  
But honestly, it’s a super helpful mindset.

Tests are the cornerstones.  
As programmers, we know what outputs we expect.  
If we test for those ideas early, we can align the rest of the code to them.

<p align="center">
  <img width="300px" src="../img/Spec_Ex.png">
</p>

---

### Hazards, Bubbles, and `NOP`s

After I finalized the formats, I realized something else...  
A proper pipeline needs to handle hazards — like _read-after-write_.  
It also needs to handle _branches_.

In class, the easy way to deal with this was to add **bubbles**, or `NOP`s.  
That gives time for operations to complete before a new one interferes.

`ADD` is one of those risky instructions. So is `BRANCH`.

If a branch instruction is mid-pipeline, and something else is queued right behind it — you could jump somewhere else and still execute the following instruction.  
That’s bad.

So I knew I had to catch branch instructions early — at fetch.

<p align="center">
  <img width="300px" src="../img/Brach.png">
</p>

---

Since I built branch handling early, expanding to things like `CBZ` or `BL` was relatively smooth.

Okay... I say _easy_ — but let’s be honest.  
It wasn’t.

I had never used `struct` or `package` in SystemVerilog.

So I did what any resourceful engineering student does...

> TO YOUTUBE ACADEMY!!!!

I went through so many videos. But I had a system — something a classmate once told me:

> “The best videos are the ones with super thick accents you can’t understand at first.”

Turns out that was true. lol.  
After enough time, the accents became trivial.

<p align="center">
  <img width="300px" src="../img/Ex_or.png">
</p>

---

### What I Couldn't Finish

One of my goals was to implement **out-of-order execution**.  
I couldn’t finish that part — ran out of time. But I still want to add it in the future.

I got the concepts, but building them in practice was another beast entirely.

Still, despite all the chaos, I made something.  
It wasn’t perfect. It wasn’t revolutionary.  
But it was my own, hard-earned work.

---

### The Ending...

Here’s the kicker.

I turned in my project... and the TA marked me wrong.  
Why?

Because I didn’t submit the _wrong_ answer — which was what he had on the answer sheet.

I laughed.

This is how letter-grade education works sometimes.  
I challenged the grade. Went to the professor.  
Showed them my work. Explained everything I did.

They were shocked.

Turns out, the TA had **never even taken** the class.  
He was randomly assigned by the school — not his fault, really.

I got full marks in the end.

But I did feel bad for the others...  
They got marked down for submitting the wrong answer. _facepalm_

Oops. Sorry...

The good news?  
The course got revised the next semester.

And I walked away with more knowledge and experience than I ever expected.

---
