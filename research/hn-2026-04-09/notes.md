# HN Notes — 2026-04-09

## Git commands I run before reading any code
**URL**: https://piechowski.io/post/git-commands-before-reading-code/  
**Score**: 2001 points

Five git commands that tell you where a codebase hurts before you open a single file. Churn hotspots, bus factor, bug clusters, and crisis patterns. The first thing I usually do when I pick up a new codebase isn&rsquo;t opening the code. It&rsquo;s opening a terminal and running a handful of git commands. Before I look at a single file, the commit history gives me a diagnostic picture of the project: who built it, where the problems cluster, whether the team is shipping with confidence or tiptoeing around land mines. git log --format = format: --name-only --since = &#34;1 year ago&#34; | sort | uniq -c | sort -nr | head -20 The 20 most-changed files in the last year. The file at the top is almost always the one people warn me about. &ldquo;Oh yeah, that file. Everyone&rsquo;s afraid to touch it.&rdquo; High churn on a file doesn&rsquo;t mean it&rsquo;s bad. Sometimes it&rsquo;s just active development. But high churn on a file that nobody wants to own is the clearest signal of codebase drag I know. That&rsquo;s the file where every change is a patch on a patch. The blast radius of a small edit is unpredictable. The team pads their estimates because they know it&rsquo;s going to fight back. A 2005 Microsoft Research study found churn-based metrics predicted defects more reliably than complexity metrics alone. I take the top 5 files from this list and cross-reference them against the bug hotspot command below.

---

## I ported Mac OS X to the Nintendo Wii
**URL**: https://bryankeller.github.io/2026/04/08/porting-mac-os-x-nintendo-wii.html  
**Score**: 1515 points

Porting Mac OS X to the Nintendo Wii | Bryan Keller’s Dev Blog Since its launch in 2007, the Wii has seen several operating systems ported to it: Linux, NetBSD, and most-recently, Windows NT. Today, Mac OS X joins that list. In this post, I’ll share how I ported the first version of Mac OS X, 10.0 Cheetah, to the Nintendo Wii. If you’re not an operating systems expert or low-level engineer, you’re in good company; this project was all about learning and navigating countless “unknown unknowns”. Join me as we explore the Wii’s hardware, bootloader development, kernel patching, and writing drivers - and give the PowerPC versions of Mac OS X a new life on the Nintendo Wii. Visit the wiiMac bootloader repository for instructions on how to try this project yourself. Before figuring out how to tackle this project, I needed to know whether it would even be possible. According to a 2021 Reddit comment : Feeling encouraged, I started with the basics: what hardware is in the Wii, and how does it compare to the hardware used in real Macs from the era. The Wii uses a PowerPC 750CL processor - an evolution of the PowerPC 750CXe that was used in G3 iBooks and some G3 iMacs. Given this close lineage, I felt confident that the CPU wouldn’t be a blocker.

---

## Veracrypt project update
**URL**: https://sourceforge.net/p/veracrypt/discussion/general/thread/9620d7a4b3/  
**Score**: 1205 points

Open source disk encryption with strong security for the Paranoid I want to share an update following my absence over the past few months. I have encountered some challenges but the most serious one is that Microsoft terminated the account I have used for years to sign Windows drivers and the bootloader. You can see below a screenshot of the message shown when I tried to sign in. Microsoft did not send me any emails or prior warnings. I have received no explanation for the termination and their message indicates that no appeal is possible. I have tried to contact Microsoft through various channels but I have only received automated replies and bots. I was unable to reach a human. This termination impacts my work beyond VeraCrypt and has consequences for my daily job. Regarding VeraCrypt, I cannot publish Windows updates. Linux and macOS updates can still be done but Windows is the platform used by the majority of users and so the inability to deliver Windows releases is a major blow to the project. If you would like to refer to this comment somewhere else in this project, copy and paste the following link: Some practical questions about the most current Windows release, until this situation can be resolved: The current version 1.26.24 is signed with the 2011 CA, which is soon to expire. This will certainly affect secureboot....

---

## US cities are axing Flock Safety surveillance technology
**URL**: https://www.cnet.com/home/security/when-flock-comes-to-town-why-cities-are-axing-the-controversial-surveillance-technology/  
**Score**: 700 points

When Flock Comes to Town: Why Cities Are Axing the Controversial Surveillance Technology - CNET Apple&apos;s 50-Year Legacy of Product Innovation, Through CNET&apos;s Lens Why Your AT&T Unlimited Plan Could Cost $20 More Each Month Starting in April 2026 Top 100 Channels on Live TV Streaming Services: YouTube TV, Hulu Live and More Still Haven&apos;t Gotten Into the Viral Sora 2 App? The Key To Getting a Code If You&apos;re Using ChatGPT For Any of These 11 Tasks, You Need to Stop All Gemini Users Can Now Use the Viral Nano Banana AI Image Generator. Here&apos;s How Apple Cider Vinegar: Here&apos;s What to Know About Health Benefits, Proper Dosage and More Tech Whatever tech you&apos;re after, we&apos;ll help you save on it. Home Give your home an upgrade or snag some everyday essentials without breaking the bank. Wellness Focus on you with these health and wellness savings. Cover Stories These deep dives offer unique and expert perspectives on tech and other topics that matter most in our daily lives. AI Slop Is Destroying the Internet. These Are the People Fighting to Save It PDAs, Tube TVs and $13,000 VCRs: How CES Jump-Starts the Tech of Tomorrow Yes, Electric Cars Are Good in Winter, and I Drove in the Arctic to Prove It Smart Glasses Are Coming for Your Face, With Wild Options for 2026 The Air Fryer Is a Once-in-a-Lifetime Kitchen Craze.

---

## LittleSnitch for Linux
**URL**: https://obdev.at/products/littlesnitch-linux/index.html  
**Score**: 614 points

Every time an application on your computer opens a network connection, it does so quietly, without asking. Little Snitch for Linux makes that activity visible and gives you the option to do something about it. You can see exactly which applications are talking to which servers, block the ones you didn't invite, and keep an eye on traffic history and data volumes over time. Compatible with Linux kernel 6.12 or higher, requires BTF kernel support Once installed, open the user interface by running littlesnitch in a terminal, or go straight to http://localhost:3031/ . You can bookmark that URL, or install it as a Progressive Web App. Any Chromium-based browser supports this natively, and Firefox users can do the same with the Progressive Web Apps extension. The connections view is where most of the action is. It lists current and past network activity by application, shows you what's being blocked by your rules and blocklists, and tracks data volumes and traffic history. Sorting by last activity, data volume, or name, and filtering the list to what's relevant, makes it easy to spot anything unexpected. Blocking a connection takes a single click. The traffic diagram at the bottom shows data volume over time. You can drag to select a time range, which zooms in and filters the connection list to show only activity from that period. Blocklists let you cut off whole categories of unwanted traffic at once.

---

## They're made out of meat (1991)
**URL**: http://www.terrybisson.com/theyre-made-out-of-meat-2/  
**Score**: 519 points

NEW: The Outspoken and the Incendiary 	 TOMORROWING, June 2024 NEW VIDEO: A Literary Celebration of Terry Bisson 	 Meg Elison Remembers TB 	 Tachyon Press Remembers TB 	 Publishers &#038; Colleagues Remember TB Terry Bisson Reads Billy’s Book Stories 	 “HAWK” DEBATE HEATS UP  	 They’re Made Out of Meat 	 Carapans: First Photos of Earth’s Enigmatic “Aliens” 	 “Monster Project” 	 Writing &#038; Race 	 Rules for Writers 	 DOCK OF THE WHAT 	 Cap ’n’ Trade 	 R.A. LAFFERTY 	 John Brown 	 FRED POHL 	 Bill Ayers 	 E. R. Burroughs 	 Peter Coyote 	 Billy Graham 	 Edward Abbey 	 Walter Miller 	 Helpful Hints 	 The Singularity 	 RSVP to the FBI 	 CARS 	 GREET THE PRESS 	 $10 a Day 	 Cover Copy 	 THE BLACK PATCH WAR 	 “DOWN BY THE BANKS OF THE OHIO” 	 The Ballantines of Kentucky Originally published in OMNI, 1991, and featured in HARPER’S and around the internet since. It has even made its way into several books on consciousness and brain science. I’m surprised, pleased, and proud. But please do not reprint, perform, alter or adapt in any way without first checking with the author. Thanks. “There’s no doubt about it. We picked up several from different parts of the planet, took them aboard our recon vessels, and probed them all the way through. They’re completely meat.” “That’s impossible. What about the radio signals? The messages to the stars?” “They use the radio waves to talk, but the signals don’t come from them. The signals come from machines.” “They made the machines.

---
