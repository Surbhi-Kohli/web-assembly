# web-assembly
https://young.github.io/intro-to-web-assembly/intro-to-wasm

why do we need web assembly?Is it java script? No, it's not JavaScript.Can I use on JavaScript?Absolutely.You're supposed to, you have to.Is it going to replace JavaScript?No, it is not a replacement for JavaScript.

Web assembly is designed to work in tandem with JavaScript.It's an entirely different language running an entirely different process in the browser.The main point of confusion that people get is should I use web assembly ora web worker?And again, those are two different concepts.
They're both different processes running in the browser.

But web assembly has its own environment, its **sandbox, is memory safe**.And the main point of web assembly is that other engineers can write code that runs on browser.And this is the part that always gets me it's kind of a misnomer because people are like, yeah, it must be something that frontend engineers do.But most of the people writing web assembly are not front end engineers.They are people that write C.They're people to write rust or C++.
There are people who want to do video processing, image processing, games,because web assembly works with binary data.That is super low level ones and zeros and you're moving them around.

But really the advantages of web assembly are, 
1.it's fast.And I know you're thinking, is it faster than JavaScript?It depends.
That's not really the use case .But it really depends on the use case on whether or not you should use web assembly or JavaScript for particular for solving a particular problem.

2.you cantake a high level language like rust or C, it compiles down to web assembly.
3.It runs on more than just browsers.Right now, there's not a really broad use case forwriting desktop apps with web assembly, but that's coming in the future.The whole reason why web assembly exists is to have a portable,memory safe, consistent environment, to write a language.

And if you're thinking, Well, that sounds a lot like the old days,like where we wrote desktop apps, and then we ship them constantly.And the idea is the same.The power of a desktop app is that it runs natively on a computer.

controversial point of the day : No matter what you write,a JavaScript is never going to be as fast as a native desktop application.

That's because a native application written in C sharp or Java oranything like that is always going to use the low levelmemory instructions of the computer that it's on.So if it's using Windows or Linux or an arm system oran x86 system, a desktop application can take advantage of that because itcan reach down into low level instruction code and just be more efficient.

Whereas JavaScript no matter what Always has to be interpreted first and then compiled.And so you're always going to get this idea that it's running in a sandbox environment.So it's never gonna be as fast, versus now we can write web assembly,we can get that sort of speed in a browser.And then we can take that code and move it to a Linux machine or Windows machine and run it natively on the desktop.That's pretty cool.Alright, but mainly I'm trying to set context here and it's not a silver bullet,it's not gonna solve all of your performance issues or things like that.

That's not what web assembly is for.**It's for this portability and the ability to take complex programs that you've already written in C, like a video encoder or decoder, and thenbring them to the web and then use that power in a safe, memory efficient manner**.

Q Compare Java has byte codewhat it compiles versus web assembly, like how are they different? Are there similarities?
There are similarities because Java andI want to say Python also compiles down to bytecode or some form of it.
There's similarities there but web assembly ultimately is going to compile down to assembly .Web assembly not the lowest level of programming. We can finally compile to asembly language.
Web assembly is right above assembly.

Now Java is still going to compile to, or Python is still doing part of bytecode which has to compile down again into assembly instructions, and then it runs natively.So, in terms of performance, I would say Java is still gonna be faster,not due to anything like input or architecture or how it's written.It's just the more mature platform.There are more optimizations in compiler.There are more tips and tricks we know for optimizing all that code.Web assembly is the newest kid on the block.It's been around for a few years, but it really gained popularity once all the browser's decided that this was the thing.

Q.is web assembly similar to programming inassembly itself as an x86 instructions or arm orwhatever micro architecture of the system they programming on?
Ans: Yes and no
Yes, in that the principles are the same. We're actually just taking bits and we're moving them around.We're applying low level instructions called opcodes to all of these bits.But it's a step above assembly and that we have nice things like four loops,and dealing with arrays, and if statements that aren't completelyridiculous to read, so I'd say it's somewhere in the middle.It's definitely more approachable than trying to learn assembly.But for now think of it as the middle ground between assembly anda high level language

The power we get right now with web assembly is the ability to take,let's say a video decoder.It's written in C, which is a time tested, very old language.Very efficient.We can compile that to web assembly and we take all those efficiencies we got from C.And then we run them as we run those in the browser.So yes, that's what it's designed to do is to create packages ofreally complex imputing and then bring that to the browser.

Whereas if we try to do this in JavaScript, it would be very clunky and very onerous.JavaScript isn't really designed to work at a low level,the way that we would need to be as optimal and as efficient as possible.

Q.When we import that web assembly, is it going to be a pain to debug?And the answer is, yes, it is, that debugging story on web assembly isprobably not as strong as other languages that we have right now.
Because again, this isn't as mature as even JavaScript where we have amazing debugging tool skills.

Q. can we reuse things like fetch andother browser API's or do we have to rewrite them from scratch?
The answer is yes, we will use fetch.We will use some browser API's.But the surface area is pretty minimal.And it's gonna come down to moving memory back and forth andthe tooling that we're going to use later built by using assembly scripts andthings like binary and things like that.But good question we will get there.


Binary:
1024= 1kB
Endian:When computers interpret instructions they need to know the byte order known as endianness. When the leftmost bit represents the largest value this is known as little endian. When the rightmost bit is the largest value is known as big endian.Web Assembly reads and writes instructions in little endian byte order.
Mac os also follows little endian


Web Assembly (wasm) is a powerful low-level language that is meant to be a compile target for high-level languages. It is designed to be portable and ran in many different environments. It is designed to compliment JavaScript, not replace it.

 Web Assembly is the secure sandbox area that runs in near native speed,almost runs at the speed of a program that is written on the desktop itself.But it's running in the browser, which is pretty phenomenal cuz the browser actually is a pretty high level abstraction over the operating system itself,Which is a high level abstraction over accessing the memory and CPU,the registers and all that.So the fact that Web Assembly can run it almost that speed of application written natively for a particular platform, is pretty impressive.

 The difference in, I know this is gonna come up, and someone will ask you this,so, why Web Assembly and not a web worker.There's probably two main things.
 One is Web Assembly can be cached, so we can fetch our wasm file from the server.It's instantiated and then it's cached in memory,versus a worker which has to be instantiated every single time.And as you know, Web Worker is a way of spinning up a separate thread away from the UI thread in JavaScript.It's generally how we were doing heavy computation before.And there are pros and cons to a worker versus Web Assembly.But at the end of the day, remember Web Assembly isn't necessarily written for JavaScript engineers to make our lives easier,it's written for other types of languages that compile down into Web Assembly.

 And that is one of the bigger, points of contention, and points that people miss about what Web Assembly is,they're like, why wouldn't you use a Web Worker, you can offload.You can do a lot of the same things in Web Worker.You can do it in Web Assembly.
 well, not same things, butyou can perform heavy calculations.You don't block the UI thread.You can pass information back and forth.Yeah, there's definitely use case for workers.
 But Web Assembly isn't designed to compete with workers.It's designed for other languages compiled down and we have this shared platform.



 Q.Why does computer use binary instead of decimal
 Q.Why does assembly lang use hex instead of decimal
