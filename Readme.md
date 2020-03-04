# 📕 25 most recommended programming books of all-time

## Table of Content

- [Methodology](#methodology)
- [Most recommended programming books](#25-most-recommended-programming-books-of-all-time)
- [Most recommended Python books](#25-most-recommended-programming-books-of-all-time)
- [Most recommended JavaScript books (coming soon)](#25-most-recommended-javascript-books-of-all-time)
- [Most recommended Java books (coming soon)](#25-most-recommended-java-books-of-all-time)

---

There are countless lists on the internet claiming to be **the** list of must-read programming books and it seemed that all those lists always recommended that same books minus two or three odd choices.

Finding good resources for learning programming is always tricky. Every-one has its own opinion about what book is the best to learn, and as we say in french, "Color and tastes should not be argued about".

However I thought it would be interesting to trust the wisdom of the crown and to find the books that appeared the most in those "Best Programming Book" lists.

If you want to jump right on the results go take a look below at the [full results](#25-most-recommended-programming-books-of-all-time). If you want to learn about the methodology, bear with me.

*Disclaimer: I spent countless hours on this article so I've decided to put Amazon affiliation links to see if those kinds of detailed articles could be a viable source of revenue, ... or not 🤷‍♂️.*

## Methodology:

*These methodology was the same for all lists, only sample size changed*

I've simply asked Google for a few queries like "Best Programming Books" and its variations. I have then scrapped all those pages (using ScrapingBee, a web scraping API I'm working on).

I've deduplicated the links and ended up with nearly 150 links. Using the title of the pages I was also able to quickly discards:

- list focussed on one particular technology or platform
- list focussed on one particular year
- list focussed on free books
- Quora and Reddit threads

I ended up with almost 200 HTML files. I went on opening all the files on my browser, open my chrome inspector, found and wrote the CSS selector matching book titles in the article. This took me around 1hours, almost 30 seconds per page. 

This also allowed me to discard even more nonrelevant pages, and I discarded a lot. In the end, I compiled around 70 lists into this one.

At this moment I had this big JSON file referencing the HTML page previously scrapped, and a CSS selector.

![](https://www.daolf.com/images/programming_book_list/rules.png)

Using Python with Beautiful soup, I've extracted every text inside DOM elements that matched the CSS selector. I ended up with a huge list of books, not usable without some post-processing.

![](https://www.daolf.com/images/programming_book_list/links.png)

To find the most quoted startup books I needed to normalize my results. 

I had to play with  all the different variation like "{title} by {author}" or "{title} - {author}".

Or "{title}:{subtitle}" and "{title}", or even all the one containing edition number. 

I ended up doing it using this simple custom Python function:
```python
def clean_link(link):
    link = link.encode().decode('ascii', errors='ignore')
    link = link.replace("'", '')
    link = link.lower()
    link = ' '.join([w for w in link.split(' ') if w not in ['the', 'a']])
    link = link.split('by')[0]
    link = link.split(':')[0]
    link = link.split('(')[0]
    link = ' '.join(link.split())
    link = link.replace('-', '_')
    link = ''.join([c for c in link if c.isalpha() or c == '_' or c == ' '])
    link = link.strip()
    link = link.replace(' ', '_')
    link = ''.join([c for c in link if c.isalpha() or c == '_'])
    return link
```
 and quite a bit of manual cleaning.

My list now looked like this:

![](https://www.daolf.com/images/programming_book_list/clean_links.png)

From there it was easy to compute the most recommended books. You can find all the data used to process this list on this [repo](https://github.com/daolf/Most-recommended-programming-books). Now let's take a look at the list:

## 25 most recommended programming books of all-time

### 25. [Continuous Delivery](https://amzn.to/2OZ9JXS) by Jez Humble & David Farley (8.8% recommended)

![](https://www.daolf.com/images/programming_book_list/25.jpg#center)

"Getting software released to users is often a painful, risky, and time-consuming process. This groundbreaking new book sets out the principles and technical practices that enable rapid, incremental delivery of high quality, valuable new functionality to users. Through automation of the build, deployment, and testing process, and improved collaboration between developers, testers, and operations, delivery teams can get changes released in a matter of hours, sometimes even minutes–no matter what the size of a project or the complexity of its code base.

Jez Humble and David Farley begin by presenting the foundations of a rapid, reliable, low-risk delivery process. Next, they introduce the “deployment pipeline,” an automated process for managing all changes, from check-in to release. Finally, they discuss the “ecosystem” needed to
support continuous delivery, from infrastructure, data and configuration management to governance." [Amazon.com](https://amzn.to/2OZ9JXS)

### 24. [Algorithms](https://amzn.to/2u2vpuG) by Robert Sedgewick & Kevin Wayne (8.8% recommended)
![](https://www.daolf.com/images/programming_book_list/24.jpg#center)
"The algorithms in this book represent a body of knowledge developed over the last 50 years that has become indispensable, not just for professional programmers and computer science students but for any student with interests in science, mathematics, and engineering, not to mention students who use computation in the liberal arts."[Amazon.com](https://amzn.to/2u2vpuG)

### 23. [The Self-Taught Programmer](https://amzn.to/325cN9T) by Cory Althoff (8.8% recommended)
![](https://www.daolf.com/images/programming_book_list/23.jpg#center)
"I am a self-taught programmer. After a year of self-study, I learned to program well enough to land a job as a software engineer II at eBay. 

Once I got there, I realized I was severely under-prepared. I was overwhelmed by the amount of things I needed to know but hadn't learned yet. My journey learning to program, and my experience at my first job as a software engineer were the inspiration for this book. 

This book is not just about learning to program; although you will learn to code. If you want to program professionally, it is not enough to learn to code; that is why, in addition to helping you learn to program, I also cover the rest of the things you need to know to program professionally that classes and books don't teach you. 

"The Self-taught Programmer" is a roadmap, a guide to take you from writing your first Python program, to passing your first technical interview. The path is there. Will you take it?"[Amazon.com](https://amzn.to/325cN9T)

### 22. [Rapid Development](https://amzn.to/2SQLQTn) by Steve McConnell (8.8% recommended)
![](https://www.daolf.com/images/programming_book_list/22.jpg#center)
"Corporate and commercial software-development teams all want solutions for one important problem—how to get their high-pressure development schedules under control. In RAPID DEVELOPMENT, author Steve McConnell addresses that concern head-on with overall strategies, specific best practices, and valuable tips that help shrink and control development schedules and keep projects moving. Inside, you’ll find:
- A rapid-development strategy that can be applied to any project and the best practices to make that strategy work
- Candid discussions of great and not-so-great rapid-development practices—estimation, prototyping, forced overtime, motivation, teamwork, rapid-development languages, risk management, and many others
- A list of classic mistakes to avoid for rapid-development projects, including creeping requirements, shortchanged quality, and silver-bullet syndrome
- Case studies that vividly illustrate what can go wrong, what can go right, and how to tell which direction your project is going
- RAPID DEVELOPMENT is the real-world guide to more efficient applications development."[Amazon.com](https://amzn.to/2SQLQTn)

### 21. [Coders at Work](https://amzn.to/323c5Ki) by Peter Seibel (10.2% recommended)
![](https://www.daolf.com/images/programming_book_list/21.jpg#center)
"This is a who's who in the programming world - a fascinating look at how some of the best in the world do their work. Patterned after the best selling Founders at Work, the book represents two years of interviews with some of the top programmers of our times."[Amazon.com](https://amzn.to/323c5Ki)

### 20. [Domain-Driven Design](https://amzn.to/38BFCxd) by Eric Evans (10.2% recommended)
![](https://www.daolf.com/images/programming_book_list/20.jpg#center)
"Leading software designers have recognized domain modeling and design as critical topics for at least twenty years, yet surprisingly little has been written about what needs to be done or how to do it. Although it has never been clearly formulated, a philosophy has developed as an undercurrent in the object community, which I call "domain-driven design".

I have spent the past decade focused on developing complex systems in several business and technical domains. I've tried best practices in design and development process as they have emerged from the leaders in the object-oriented development community. Some of my projects were very successful; a few failed. A feature common to the successes was a rich domain model that evolved through iterations of design and became part of the fabric of the project.

This book provides a framework for making design decisions and a technical vocabulary for discussing domain design. It is a synthesis of widely accepted best practices along with my own insights and experiences. Projects facing complex domains can use this framework to approach domain-driven design systematically."[Amazon.com](https://amzn.to/38BFCxd)

### 19. [The Art of Computer Programming](https://amzn.to/2SU7N3Q) by Donald E. Knuth(10.2% recommended)
![](https://www.daolf.com/images/programming_book_list/19.jpg#center)
"Countless readers have spoken about the profound personal influence of Knuth’s work. Scientists have marveled at the beauty and elegance of his analysis, while ordinary programmers have successfully applied his “cookbook” solutions to their day-to-day problems. All have admired Knuth for the breadth, clarity, accuracy, and good humor found in his books."[Amazon.com](https://amzn.to/2SU7N3Q)

### 18. [Structure and Interpretation of Computer Programs](https://amzn.to/2HJ7HqR) by Harold Abelson / Gerald Jay Sussman / Julie Sussman (13.2% recommended)
![](https://www.daolf.com/images/programming_book_list/17.jpg#center)
"Structure and Interpretation of Computer Programs has had a dramatic impact on computer science curricula over the past decade. This long-awaited revision contains changes throughout the text. There are new implementations of most of the major programming systems in the book, including the interpreters and compilers, and the authors have incorporated many small changes that reflect their experience teaching the course at MIT since the first edition was published. A new theme has been introduced that emphasizes the central role played by different approaches to dealing with time in computational models: objects with state, concurrent programming, functional programming and lazy evaluation, and nondeterministic programming. There are new example sections on higher-order procedures in graphics and on applications of stream processing in numerical programming, and many new exercises. In addition, all the programs have been reworked to run in any Scheme implementation that adheres to the IEEE standard."[Amazon.com](https://amzn.to/2HJ7HqR)

### 17. [Patterns of Enterprise Application Architecture](https://amzn.to/37xEadR) by Martin Fowler (14.7% recommended)
![](https://www.daolf.com/images/programming_book_list/16.jpg#center)
"The practice of enterprise application development has benefited from the emergence of many new enabling technologies. Multi-tiered object-oriented platforms, such as Java and .NET, have become commonplace. These new tools and technologies are capable of building powerful applications, but they are not easily implemented. Common failures in enterprise applications often occur because their developers do not understand the architectural lessons that experienced object developers have learned."[Amazon.com](https://amzn.to/37xEadR)


### 16. [Programming Pearls](https://amzn.to/2u8cOxo) by  Jon Bentley (16.1% recommended)
![](https://www.daolf.com/images/programming_book_list/16-bis.jpg#center)
"Computer programming has many faces. Fred Brooks paints the big picture in The Mythical Man Month; his essays underscore the crucial role of management in large software projects. At a finer grain, Steve McConnell teaches good programming style in Code Complete. The topics in those books are the key to good software and the hallmark of the professional programmer. Unfortunately, though, the workmanlike application of those sound engineering principles isn't always thrilling -- until the software is completed on time and works without surprise.

The columns in this book are about a more glamorous aspect of the profession: programming pearls whose origins lie beyond solid engineering, in the realm of insight and creativity. Just as natural pearls grow from grains of sand that have irritated oysters, these programming pearls have grown from real problems that have irritated real programmers. The programs are fun, and they teach important programming techniques and fundamental design principles."[Amazon.com](https://amzn.to/2u8cOxo)


### 15. [Peopleware](https://amzn.to/2P2YRIh) by Tom DeMarco & Tim Lister (17.6% recommended)
![](https://www.daolf.com/images/programming_book_list/15.jpg#center)
"Drawing on their software development and management experience, and highlighting the insights and wisdom of other successful managers, Mantle and Lichty provide the rules, tools, and insights you need to manage and understand people and teams in order to deliver software successfully and avoid projects that have run catastrophically over schedule and budget.	The unique insight of this longtime bestseller is that the major issues of software development are human, not technical. They're not easy issues; but solve them, and you'll maximize your chances of success.	With a blend of software engineering facts and thought-provoking opinions, Fred Brooks offers insight for anyone managing complex projects."[Amazon.com](https://amzn.to/2P2YRIh)

### 14. [Introduction to Algorithms](https://amzn.to/2SAdPrt) by Thomas H. Cormen / Charles E. Leiserson / Ronald L. Rivest / Clifford Stein (17.6% recommended)
![](https://www.daolf.com/images/programming_book_list/14.jpg#center)
"Some books on algorithms are rigorous but incomplete; others cover masses of material but lack rigor. Introduction to Algorithms uniquely combines rigor and comprehensiveness. The book covers a broad range of algorithms in depth, yet makes their design and analysis accessible to all levels of readers. Each chapter is relatively self-contained and can be used as a unit of study. The algorithms are described in English and in a pseudocode designed to be readable by anyone who has done a little programming. The explanations have been kept elementary without sacrificing depth of coverage or mathematical rigor.

The first edition became a widely used text in universities worldwide as well as the standard reference for professionals. The second edition featured new chapters on the role of algorithms, probabilistic analysis and randomized algorithms, and linear programming. The third edition has been revised and updated throughout. It includes two completely new chapters, on van Emde Boas trees and multithreaded algorithms, substantial additions to the chapter on recurrence (now called “Divide-and-Conquer”), and an appendix on matrices. It features improved treatment of dynamic programming and greedy algorithms and a new notion of edge-based flow in the material on flow networks. Many exercises and problems have been added for this edition. The international paperback edition is no longer available; the hardcover is available worldwide."[Amazon.com](https://amzn.to/2SAdPrt)

### 13. [Code](https://amzn.to/38zhTOo) by Charles Petzold (19.1% recommended)
![](https://www.daolf.com/images/programming_book_list/13.jpg#center)
"What do flashlights, the British invasion, black cats, and seesaws have to do with computers? In CODE, they show us the ingenious ways we manipulate language and invent new means of communicating with each other. And through CODE, we see how this ingenuity and our very human compulsion to communicate have driven the technological innovations of the past two centuries.

Using everyday objects and familiar language systems such as Braille and Morse code, author Charles Petzold weaves an illuminating narrative for anyone who’s ever wondered about the secret inner life of computers and other smart machines.

It’s a cleverly illustrated and eminently comprehensible story—and along the way, you’ll discover you’ve gained a real context for understanding today’s world of PCs, digital media, and the Internet. No matter what your level of technical savvy, CODE will charm you—and perhaps even awaken the technophile within."[Amazon.com](https://amzn.to/38zhTOo)

### 12. [Don't Make Me Think](https://amzn.to/2UYPsW3) by Steve Krug (19.1% recommended)
![](https://www.daolf.com/images/programming_book_list/12.jpg#center)
"Since Don’t Make Me Think was first published in 2000, hundreds of thousands of Web designers and developers have relied on usability guru Steve Krug’s guide to help them understand the principles of intuitive navigation and information design. Witty, commonsensical, and eminently practical, it’s one of the best-loved and most recommended books on the subject.

Now Steve returns with fresh perspective to reexamine the principles that made Don’t Make Me Think a classic–with updated examples and a new chapter on mobile usability. And it’s still short, profusely illustrated…and best of all–fun to read.

If you’ve read it before, you’ll rediscover what made Don’t Make Me Think so essential to Web designers and developers around the world. If you’ve never read it, you’ll see why so many people have said it should be required reading for anyone working on Web sites."[Amazon.com](https://amzn.to/2UYPsW3)

### 11. [Soft Skills](https://amzn.to/2HziTGl) by John Sonmez  (22% recommended)
![](https://www.daolf.com/images/programming_book_list/11.jpg#center)
"For most software developers, coding is the fun part. The hard bits are dealing with clients, peers, and managers, staying productive, achieving financial security, keeping yourself in shape, and finding true love. This book is here to help.

Soft Skills: The software developer's life manual is a guide to a well-rounded, satisfying life as a technology professional. In it, developer and life coach John Sonmez offers advice to developers on important "soft" subjects like career and productivity, personal finance and investing, and even fitness and relationships. Arranged as a collection of 71 short chapters, this fun-to-read book invites you to dip in wherever you like. A Taking Action section at the end of each chapter shows you how to get quick results. Soft Skills will help make you a better programmer, a more valuable employee, and a happier, healthier person."[Amazon.com](https://amzn.to/2HziTGl)

### 10. [Cracking the Coding Interview](https://amzn.to/37CuhvD) by Gayle Laakmann McDowell (22% recommended)
![](https://www.daolf.com/images/programming_book_list/10.jpg#center)
"I am not a recruiter. I am a software engineer. And as such, I know what it's like to be asked to whip up brilliant algorithms on the spot and then write flawless code on a whiteboard. I've been through this as a candidate and as an interviewer.

Cracking the Coding Interview, 6th Edition is here to help you through this process, teaching you what you need to know and enabling you to perform at your very best. I've coached and interviewed hundreds of software engineers. The result is this book.

Learn how to uncover the hints and hidden details in a question, discover how to break down a problem into manageable chunks, develop techniques to unstick yourself when stuck, learn (or re-learn) core computer science concepts, and practice on 189 interview questions and solutions.

These interview questions are real; they are not pulled out of computer science textbooks. They reflect what's truly being asked at the top companies, so that you can be as prepared as possible. WHAT'S INSIDE?
- 189 programming interview questions, ranging from the basics to the trickiest algorithm problems.
- A walk-through of how to derive each solution, so that you can learn how to get there yourself.
- Hints on how to solve each of the 189 questions, just like what you would get in a real interview.
- Five proven strategies to tackle algorithm questions, so that you can solve questions you haven't seen.
- Extensive coverage of essential topics, such as big O time, data structures, and core algorithms.
- A behind the scenes look at how top companies like Google and Facebook hire developers.
- Techniques to prepare for and ace the soft side of the interview: behavioral questions.
- For interviewers and companies: details on what makes a good interview question and hiring process."[Amazon.com](https://amzn.to/37CuhvD)

### 9. [Design Patterns](https://amzn.to/38Eb9yO) by by Erich Gamma / Richard Helm / Ralph Johnson / John Vlissides (25% recommended)
![](https://www.daolf.com/images/programming_book_list/9.jpg#center)
"Capturing a wealth of experience about the design of object-oriented software, four top-notch designers present a catalog of simple and succinct solutions to commonly occurring design problems. Previously undocumented, these 23 patterns allow designers to create more flexible, elegant, and ultimately reusable designs without having to rediscover the design solutions themselves.

The authors begin by describing what patterns are and how they can help you design object-oriented software. They then go on to systematically name, explain, evaluate, and catalog recurring designs in object-oriented systems. With Design Patterns as your guide, you will learn how these important patterns fit into the software development process, and how you can leverage them to solve your own design problems most efficiently.

Each pattern describes the circumstances in which it is applicable, when it can be applied in view of other design constraints, and the consequences and trade-offs of using the pattern within a larger design. All patterns are compiled from real systems and are based on real-world examples. Each pattern also includes code that demonstrates how it may be implemented in object-oriented programming languages like C++ or Smalltalk."[Amazon.com](https://amzn.to/38Eb9yO)

### 8. [Working Effectively with Legacy Code](https://amzn.to/2P37DWJ) by Michael Feathers (26.4% recommended)
![](https://www.daolf.com/images/programming_book_list/8.jpg#center)
"In this book, Michael Feathers offers start-to-finish strategies for working more effectively with large, untested legacy code bases. This book draws on material Michael created for his own renowned Object Mentor seminars: techniques Michael has used in mentoring to help hundreds of developers, technical managers, and testers bring their legacy systems under control.
This book also includes a catalog of twenty-four dependency-breaking techniques that help you work with program elements in isolation and make safer changes."[Amazon.com](https://amzn.to/2P37DWJ)

### 7. [The Clean Coder](https://amzn.to/2u63SIS) by Robert Martin (27.9% recommended)
![](https://www.daolf.com/images/programming_book_list/7.jpg#center)
"Programmers who endure and succeed amidst swirling uncertainty and nonstop pressure share a common attribute: They care deeply about the practice of creating software. They treat it as a craft. They are professionals.

In The Clean Coder: A Code of Conduct for Professional Programmers, legendary software expert Robert C. Martin introduces the disciplines, techniques, tools, and practices of true software craftsmanship. This book is packed with practical advice–about everything from estimating and coding to refactoring and testing. It covers much more than technique: It is about attitude. Martin shows how to approach software development with honor, self-respect, and pride; work well and work clean; communicate and estimate faithfully; face difficult decisions with clarity and honesty; and understand that deep knowledge comes with a responsibility to act.

Great software is something to marvel at: powerful, elegant, functional, a pleasure to work with as both a developer and as a user. Great software isn’t written by machines. It is written by professionals with an unshakable commitment to craftsmanship. The Clean Coder will help you become one of them–and earn the pride and fulfillment that they alone possess."[Amazon.com](https://amzn.to/2u63SIS)

### 6. [The Mythical Man-Month](https://amzn.to/3bL1lVz) by Frederick P. Brooks Jr (27.9% recommended)
![](https://www.daolf.com/images/programming_book_list/6.jpg#center)
"Few books on software project management have been as influential and timeless as The Mythical Man-Month. With a blend of software engineering facts and thought-provoking opinions, Fred Brooks offers insight for anyone managing complex projects. These essays draw from his experience as project manager for the IBM System/360 computer family and then for OS/360, its massive software system. Now, 20 years after the initial publication of his book, Brooks has revisited his original ideas and added new thoughts and advice, both for readers already familiar with his work and for readers discovering it for the first time."[Amazon.com](https://amzn.to/3bL1lVz)

### 5. [Head First Design Patterns](https://amzn.to/2SUiUtA) by Eric Freeman / Bert Bates / Kathy Sierra / Elisabeth Robson (29.4% recommended)
![](https://www.daolf.com/images/programming_book_list/5.jpg#center)
"What’s so special about design patterns?

At any given moment, someone struggles with the same software design problems you have. And, chances are, someone else has already solved your problem. This edition of Head First Design Patterns—now updated for Java 8—shows you the tried-and-true, road-tested patterns used by developers to create functional, elegant, reusable, and flexible software. By the time you finish this book, you’ll be able to take advantage of the best design practices and experiences of those who have fought the beast of software design and triumphed.

What’s so special about this book?

We think your time is too valuable to spend struggling with new concepts. Using the latest research in cognitive science and learning theory to craft a multi-sensory learning experience, Head First Design Patterns uses a visually rich format designed for the way your brain works, not a text-heavy approach that puts you to sleep."[Amazon.com](https://amzn.to/2SUiUtA)

### 4. [Refactoring](https://amzn.to/2uSs167) by Martin Fowler (35% recommended)
![](https://www.daolf.com/images/programming_book_list/4.jpg#center)
"As the application of object technology--particularly the Java programming language--has become commonplace, a new problem has emerged to confront the software development community. Significant numbers of poorly designed programs have been created by less-experienced developers, resulting in applications that are inefficient and hard to maintain and extend. Increasingly, software system professionals are discovering just how difficult it is to work with these inherited, non-optimal applications. 

For several years, expert-level object programmers have employed a growing collection of techniques to improve the structural integrity and performance of such existing software programs. Referred to as refactoring, these practices have remained in the domain of experts because no attempt has been made to transcribe the lore into a form that all developers could use. . .until now. In Refactoring: Improving the Design of Existing Software, renowned object technology mentor Martin Fowler breaks new ground, demystifying these master practices and demonstrating how software practitioners can realize the significant benefits of this new process. With proper training a skilled system designer" [Amazon.com](https://amzn.to/2uSs167)


### 3. [Code Complete](https://amzn.to/37wO0wR) by Steve McConnell (42% recommended)
![](https://www.daolf.com/images/programming_book_list/3.jpg#center)
"Widely considered one of the best practical guides to programming, Steve McConnell’s original CODE COMPLETE has been helping developers write better software for more than a decade. Now this classic book has been fully updated and revised with leading-edge practices—and hundreds of new code samples—illustrating the art and science of software construction. Capturing the body of knowledge available from research, academia, and everyday commercial practice, McConnell synthesizes the most effective techniques and must-know principles into clear, pragmatic guidance. No matter what your experience level, development environment, or project size, this book will inform and stimulate your thinking—and help you build the highest quality code."[Amazon.com](https://amzn.to/37wO0wR)

### 2. [Clean Code](https://amzn.to/2Hy0n0U) by Robert C. Martin  (66% recommended)
![](https://www.daolf.com/images/programming_book_list/2.jpg#center)
"Clean Code is divided into three parts. The first describes the principles, patterns, and practices of writing clean code. The second part consists of several case studies of increasing complexity. Each case study is an exercise in cleaning up code—of transforming a code base that has some problems into one that is sound and efficient. The third part is the payoff: a single chapter containing a list of heuristics and “smells” gathered while creating the case studies. The result is a knowledge base that describes the way we think when we write, read, and clean code."[Amazon.com](https://amzn.to/2Hy0n0U)

### 1. [The Pragmatic Programmer](https://amzn.to/3bO6Xyb) by David Thomas & Andrew Hunt (67% recommended)
![](https://www.daolf.com/images/programming_book_list/1.jpg#center)
"
The Pragmatic Programmer is one of those rare tech books you’ll read, re-read, and read again over the years. Whether you’re new to the field or an experienced practitioner, you’ll come away with fresh insights each and every time.

Dave Thomas and Andy Hunt wrote the first edition of this influential book in 1999 to help their clients create better software and rediscover the joy of coding. These lessons have helped a generation of programmers examine the very essence of software development, independent of any particular language, framework, or methodology, and the Pragmatic philosophy has spawned hundreds of books, screencasts, and audio books, as well as thousands of careers and success stories.

Now, twenty years later, this new edition re-examines what it means to be a modern programmer. Topics range from personal responsibility and career development to architectural techniques for keeping your code flexible and easy to adapt and reuse."[Amazon.com](https://amzn.to/3bO6Xyb)

## Conclusion

Although the order might suprise some, by definition, most of you must have heard of these books already.

A few additional things I learned making this list: 

- Marting Fowler, Robert C. Martin and Steve McConnell are the only authors with several books in the list.
- Cracking the Coding interview is the most recent book on the list, released in 2015.
- [Python Programming](https://amzn.to/321qbMx), by John Zelle was the most cited book focused on one language. It would have #5 had I taken it into account.

I hope you enjoyed this article. 

I must admit, those lists take a while to make. If you liked this article and feel like Twitter would like it please do not hesitate to love and retweet, it really does help :). 

See also: [Most recommended startup books](https://github.com/daolf/Most-recommended-startup-books)

*Originally publicated on my [personnal blog](https://www.daolf.com/posts/best-programming-books/)*

## 25 most recommended Python books of all-time

Number of lists: 130, number of recommendations: 2200.

#### 25. [Python: Learn Python in One Day and Learn It Well](https://amzn.to/2VFKJcf) by Jamie Chan (7.9% recommended)
![](https://www.daolf.com/images/python_book_list/25.png#center)
"Have you always wanted to learn computer programming but are afraid it'll be too difficult for you? Or perhaps you know other programming languages but are interested in learning the Python language fast?

 This book is for you. You no longer have to waste your time and money learning Python from lengthy books, expensive online courses or complicated Python tutorials." [Amazon.com](https://amzn.to/2VFKJcf)
#### 24. [Deep Learning with Python](https://amzn.to/38jS9V5) by François Chollet (7.9% recommended)
![](https://www.daolf.com/images/python_book_list/24.png#center)
"This book was written for anyone who wishes to explore deep learning from scratch or broaden their understanding of deep learning. Whether you’re a practicing machine-learning engineer, a software developer, or a college student, you’ll find value in these pages. This book offers a practical, hands-on exploration of deep learning. It avoids mathematical notation, preferring instead to explain quantitative concepts via code snippets and to build practical intuition about the core ideas of machine learning and deep learning. 

You’ll learn from more than 30 code examples that include detailed commentary, practical recommendations, and simple high-level explanations of everything you need to know to start using deep learning to solve concrete problems. The code examples use the Python deep-learning framework Keras, with Tensor- Flow as a back-end engine. Keras, one of the most popular and fastest-growing deeplearning frameworks, is widely recommended as the best tool to get started with deep learning." [Amazon.com](https://amzn.to/38jS9V5)
#### 23. [Python Data Science Handbook](https://amzn.to/38gvLw1) by Jake VanderPlas (7.9% recommended)
![](https://www.daolf.com/images/python_book_list/23.png#center)
"For many researchers, Python is a first-class tool mainly because of its libraries for storing, manipulating, and gaining insight from data. Several resources exist for individual pieces of this data science stack, but only with the Python Data Science Handbook do you get them all—IPython, NumPy, Pandas, Matplotlib, Scikit-Learn, and other related tools.

 Working scientists and data crunchers familiar with reading and writing Python code will find this comprehensive desk reference ideal for tackling day-to-day issues: manipulating, transforming, and cleaning data; visualizing different types of data; and using data to build statistical or machine learning models. Quite simply, this is the must-have reference for scientific computing in Python." [Amazon.com](https://amzn.to/38gvLw1)
#### 22. [Violent Python](https://amzn.to/32K1aFW) by TJ O'Connor (8.8% recommended)
![](https://www.daolf.com/images/python_book_list/22.png#center)
"Violent Python shows you how to move from a theoretical understanding of offensive computing concepts to a practical implementation. Instead of relying on another attacker’s tools, this book will teach you to forge your own weapons using the Python programming language. This book demonstrates how to write Python scripts to automate large-scale network attacks, extract metadata, and investigate forensic artifacts. 

It also shows how to write code to intercept and analyze network traffic using Python, craft and spoof wireless frames to attack wireless and Bluetooth devices, and how to data-mine popular social media websites and evade modern anti-virus." [Amazon.com](https://amzn.to/32K1aFW)
#### 21. [Natural Language Processing with Python](https://amzn.to/2vzPcCz) by Steven Bird & Ewan Klein & Edward Loper (9.6% recommended)
![](https://www.daolf.com/images/python_book_list/21.png#center)
"This book offers a highly accessible introduction to natural language processing, the field that supports a variety of language technologies, from predictive text and email filtering to automatic summarization and translation. With it, you'll learn how to write Python programs that work with large collections of unstructured text. You'll access richly annotated datasets using a comprehensive range of linguistic data structures, and you'll understand the main algorithms for analyzing the content and structure of written communication. 

Packed with examples and exercises, Natural Language Processing with Python will help you: Extract information from unstructured text, either to guess the topic or identify 'named entities' Analyze linguistic structure in text, including parsing and semantic analysis Access popular linguistic databases, including WordNet and treebanks Integrate techniques drawn from fields as diverse as linguistics and artificial intelligence This book will help you gain practical skills in natural language processing using the Python programming language and the Natural Language Toolkit (Nltk) open source library. 

If you're interested in developing web applications, analyzing multilingual news sources, or documenting endangered languages - or if you're simply curious to have a programmer's perspective on how human language works - you'll find Natural Language Processing with Python both fascinating and immensely useful." [Amazon.com](https://amzn.to/2vzPcCz)
#### 20. [The Hitchhiker's Guide to Python](https://amzn.to/3cqwH45) by Kenneth Reitz & Tanya Schlusser (9.6% recommended)
![](https://www.daolf.com/images/python_book_list/20.png#center)
"The Hitchhiker's Guide to Python takes the journeyman Pythonista to true expertise. More than any other language, Python was created with the philosophy of simplicity and parsimony. Now 25 years old, Python has become the primary or secondary language (after SQL) for many business users. With popularity comes diversity—and possibly dilution.

 This guide, collaboratively written by over a hundred members of the Python community, describes best practices currently used by package and application developers. Unlike other books for this audience, The Hitchhiker’s Guide is light on reusable code and heavier on design philosophy, directing the reader to excellent sources that already exist." [Amazon.com](https://amzn.to/3cqwH45)
#### 19. [Python Pocket Reference](https://amzn.to/2vzOIML) by Mark Lutz (10.5% recommended)
![](https://www.daolf.com/images/python_book_list/19.png#center)
"This convenient pocket guide is the perfect on-the-job quick reference. You’ll find concise, need-to-know information on Python types and statements, special method names, built-in functions and exceptions, commonly used standard library modules, and other prominent Python tools. The handy index lets you pinpoint exactly what you need.

 Written by Mark Lutz—widely recognized as the world’s leading Python trainer—Python Pocket Reference is an ideal companion to O’Reilly’s classic Python tutorials, Learning Python and Programming Python, also written by Mark." [Amazon.com](https://amzn.to/2vzOIML)
#### 18. [Invent Your Own Computer Games with Python](https://amzn.to/3ao8ucN) by Al Sweigart (10.5% recommended)
![](https://www.daolf.com/images/python_book_list/18.png#center)
"Begin by building classic games like Hangman, Guess the Number, and Tic-Tac-Toe, and then work your way up to more advanced games, like a text-based treasure hunting game and an animated collision-dodging game with sound effects. Along the way, you’ll learn key programming and math concepts that will help you take your game programming to the next level." [Amazon.com](https://amzn.to/3ao8ucN)
#### 17. [Python in a Nutshell](https://amzn.to/2IdkJgr) by Alex Martelli & Anna Ravenscroft & Steve Holden (11.4% recommended)
![](https://www.daolf.com/images/python_book_list/17.png#center)
"Useful in many roles, from design and prototyping to testing, deployment, and maintenance, Python is consistently ranked among today’s most popular programming languages. The third edition of this practical book provides a quick reference to the language—including Python 3.5, 2.7, and highlights of 3.6—commonly used areas of its vast standard library, and some of the most useful third-party modules and packages. 

 Ideal for programmers with some Python experience, and those coming to Python from other programming languages, this book covers a wide range of application areas, including web and network programming, XML handling, database interactions, and high-speed numeric computing. Discover how Python provides a unique mix of elegance, simplicity, practicality, and sheer power." [Amazon.com](https://amzn.to/2IdkJgr)
#### 16. [Introduction to Machine Learning with Python](https://amzn.to/3coXmhI) by  Andreas C. Müller & Sarah Guido (12.3% recommended)
![](https://www.daolf.com/images/python_book_list/16.png#center)
"Machine learning has become an integral part of many commercial applications and research projects, but this field is not exclusive to large companies with extensive research teams. If you use Python, even as a beginner, this book will teach you practical ways to build your own machine learning solutions. With all the data available today, machine learning applications are limited only by your imagination. 

 You’ll learn the steps necessary to create a successful machine-learning application with Python and the scikit-learn library. Authors Andreas Müller and Sarah Guido focus on the practical aspects of using machine learning algorithms, rather than the math behind them. Familiarity with the NumPy and matplotlib libraries will help you get even more from this book." [Amazon.com](https://amzn.to/3coXmhI)
#### 15. [Programming Python](https://amzn.to/3aiYZLY) by Mark Lutz (12.3% recommended)
![](https://www.daolf.com/images/python_book_list/15.png#center)
"If you've mastered Python's fundamentals, you're ready to start using it to get real work done. Programming Python will show you how, with in depth tutorials on the language's primary application domains: system administration, GUIs, and the Web. You'll also explore how Python is used in databases, networking, front end scripting layers, text processing, and more. This book focuses on commonly used tools and libraries to give you a comprehensive understanding of Python’s many roles in practical, real world programming.

 You'll learn language syntax and programming techniques in a clear and concise manner, with lots of examples that illustrate both correct usage and common idioms. Completely updated for version 3.x, Programming Python also delves into the language as a software development tool, with many code examples scaled specifically for that purpose." [Amazon.com](https://amzn.to/3aiYZLY)
#### 14. [David Beazley](https://amzn.to/2VHnI8A) by Python Essential Reference (14.0% recommended)
![](https://www.daolf.com/images/python_book_list/14.png#center)
"Python Essential Reference is the definitive reference guide to the Python programming language — the one authoritative handbook that reliably untangles and explains both the core Python language and the most essential parts of the Python library.

 Designed for the professional programmer, the book is concise, to the point, and highly accessible. It also includes detailed information on the Python library and many advanced subjects that is not available in either the official Python documentation or any other single reference source.

 Thoroughly updated to reflect the significant new programming language features and library modules that have been introduced in Python 2.6 and Python 3, the fourth edition of Python Essential Reference is the definitive guide for programmers who need to modernize existing Python code or who are planning an eventual migration to Python 3. Programmers starting a new Python project will find detailed coverage of contemporary Python programming idioms." [Amazon.com](https://amzn.to/2VHnI8A)
#### 13. [Dive into Python 3](https://amzn.to/38fd8Ze) by  Mark Pilgrim (14.0% recommended)
![](https://www.daolf.com/images/python_book_list/13.png#center)
"There are a huge number of python developers who will need to learn to port their code to python 3, and Dive Into Python 3 is the ideal hands-on introduction to the latest version of python for them. Its unique style of giving a chunk of code first and then picking it apart is ideally suited to existing developers who want to understand the new version of the language quickly." [Amazon.com](https://amzn.to/38fd8Ze)
#### 12. [Python Machine Learning](https://amzn.to/3cta5A0) by Sebastian Raschka & Vahid Mirjalili (14.9% recommended)
![](https://www.daolf.com/images/python_book_list/12.png#center)
"" [Amazon.com](https://amzn.to/3cta5A0)
#### 11. [Python Tricks](https://amzn.to/3crKx6j) by Dan Bader (14.9% recommended)
![](https://www.daolf.com/images/python_book_list/11.png#center)
"With Python Tricks: The Book you’ll discover Python’s best practices and the power of beautiful & Pythonic code with simple examples and a step-by-step narrative. 

 You'll get one step closer to mastering Python, so you can write beautiful and idiomatic code that comes to you naturally. 

 Learning the ins and outs of Python is difficult—and with this book you'll be able to focus on the practical skills that really matter. Discover the “hidden gold” in Python’s standard library and start writing clean and Pythonic code today." [Amazon.com](https://amzn.to/3crKx6j)
#### 10. [Think Python: How to Think Like a Computer Scientist](https://amzn.to/2x2gXnz) by Allen B. Downey  (19.3% recommended)
![](https://www.daolf.com/images/python_book_list/10.png#center)
"If you want to learn how to program, working with Python is an excellent way to start. This hands-on guide takes you through the language a step at a time, beginning with basic programming concepts before moving on to functions, recursion, data structures, and object-oriented design. This second edition and its supporting code have been updated for Python 3. 

 Through exercises in each chapter, you’ll try out programming concepts as you learn them. Think Python is ideal for students at the high school or college level, as well as self-learners, home-schooled students, and professionals who need to learn programming basics. Beginners just getting their feet wet will learn how to start with Python in a browser." [Amazon.com](https://amzn.to/2x2gXnz)
#### 9. [Effective Python](https://amzn.to/3aiXTzQ) by Brett Slatkin (19.3% recommended)
![](https://www.daolf.com/images/python_book_list/9.png#center)
"It’s easy to start developing programs with Python, which is why the language is so popular. However, Python’s unique strengths, charms, and expressiveness can be hard to grasp, and there are hidden pitfalls that can easily trip you up." [Amazon.com](https://amzn.to/3aiXTzQ)
#### 8. [Python for Data Analysis](https://amzn.to/2uQ5p6l) by Wes McKinney (20.2% recommended)
![](https://www.daolf.com/images/python_book_list/8.png#center)
"This book is concerned with the nuts and bolts of manipulating, processing, cleaning, and crunching data in Python. My goal is to offer a guide to the parts of the Python programming language and its data-oriented library ecosystem and tools that will equip you to become an effective data analyst. While 'data analysis' is in the title of the book, the focus is specifically on Python programming, libraries, and tools as opposed to data analysis methodology. This is the Python programming you need for data analysis." [Amazon.com](https://amzn.to/2uQ5p6l)
#### 7. [Learn Python the Hard Way](https://amzn.to/2x9ONY0) by Zed Shaw (21.1% recommended)
![](https://www.daolf.com/images/python_book_list/7.png#center)
"Zed Shaw has perfected the world’s best system for learning Python 3. Follow it and you will succeed—just like the millions of beginners Zed has taught to date! You bring the discipline, commitment, and persistence; the author supplies everything else." [Amazon.com](https://amzn.to/2x9ONY0)
#### 6. [Automate the Boring Stuff with Python](https://amzn.to/2Tj8WDn) by Al Sweigart (23.7% recommended)
![](https://www.daolf.com/images/python_book_list/6.png#center)
"If you've ever spent hours renaming files or updating hundreds of spreadsheet cells, you know how tedious tasks like these can be. But what if you could have your computer do them for you? 

 In this fully revised second edition of the best-selling classic Automate the Boring Stuff with Python, you'll learn how to use Python to write programs that do in minutes what would take you hours to do by hand--no prior programming experience required. You'll learn the basics Python and explore Python's rich library of modules for performing specific tasks, like scraping data off websites, reading PDF and Word documents, and automating clicking and typing tasks." [Amazon.com](https://amzn.to/2Tj8WDn)
#### 5. [Head First Python: A Brain-Friendly Guide](https://amzn.to/2wt9KwQ) by Paul Barry (25.4% recommended)
![](https://www.daolf.com/images/python_book_list/5.png#center)
"Want to learn the Python language without slogging your way through how to manuals? With Head First Python, you’ll quickly grasp Python’s fundamentals, working with the built in data structures and functions. Then you’ll move on to building your very own webapp, exploring database management, exception handling, and data wrangling. If you’re intrigued by what you can do with context managers, decorators, comprehensions, and generators, it’s all here. This second edition is a complete learning experience that will help you become a bonafide Python programmer in no time." [Amazon.com](https://amzn.to/2wt9KwQ)
#### 4. [Python Crash Course](https://amzn.to/2VKa5G0) by Eric Matthes  (33.3% recommended)
![](https://www.daolf.com/images/python_book_list/4.png#center)
"is a straightforward introduction to the core of Python programming. Author Eric Matthes dispenses with the sort of tedious, unnecessary information that can get in the way of learning how to program, choosing instead to provide a foundation in general programming concepts, Python fundamentals, and problem solving. Three real world projects in the second part of the book allow readers to apply their knowledge in useful ways.

 Readers will learn how to create a simple video game, use data visualization techniques to make graphs and charts, and build and deploy an interactive web application. Python Crash Course, 2nd Edition teaches beginners the essentials of Python quickly so that they can build practical programs and develop powerful programming techniques." [Amazon.com](https://amzn.to/2VKa5G0)
#### 3. [Fluent Python](https://amzn.to/2IgGQ5A) by Luciano Ramalho (35.1% recommended)
![](https://www.daolf.com/images/python_book_list/3.png#center)
"Python’s simplicity lets you become productive quickly, but this often means you aren’t using everything it has to offer. With this hands-on guide, you’ll learn how to write effective, idiomatic Python code by leveraging its best—and possibly most neglected—features. Author Luciano Ramalho takes you through Python’s core language features and libraries, and shows you how to make your code shorter, faster, and more readable at the same time. 

 Many experienced programmers try to bend Python to fit patterns they learned from other languages, and never discover Python features outside of their experience. With this book, those Python programmers will thoroughly learn how to become proficient in Python 3." [Amazon.com](https://amzn.to/2IgGQ5A)
#### 2. [Python Cookbook](https://amzn.to/2TCfXhw) by David Beazley & Brian K. Jones (36.0% recommended)
![](https://www.daolf.com/images/python_book_list/2.png#center)
"If you need help writing programs in Python 3, or want to update older Python 2 code, this book is just the ticket. Packed with practical recipes written and tested with Python 3.3, this unique cookbook is for experienced Python programmers who want to focus on modern tools and idioms. 

 Inside, you’ll find complete recipes for more than a dozen topics, covering the core Python language as well as tasks common to a wide variety of application domains. Each recipe contains code samples you can use in your projects right away, along with a discussion about how and why the solution works." [Amazon.com](https://amzn.to/2TCfXhw)
#### 1. [Learning Python](https://amzn.to/3cvghHw) by Mark Lutz (36.0% recommended)
![](https://www.daolf.com/images/python_book_list/1.png#center)
"Get a comprehensive, in-depth introduction to the core Python language with this hands-on book. Based on author Mark Lutz’s popular training course, this updated fifth edition will help you quickly write efficient, high-quality code with Python. It’s an ideal way to begin, whether you’re new to programming or a professional developer versed in other languages. 

 Complete with quizzes, exercises, and helpful illustrations, this easy-to-follow, self-paced tutorial gets you started with both Python 2.7 and 3.3— the latest releases in the 3.X and 2.X lines—plus all other releases in common use today. You’ll also learn some advanced language features that recently have become more common in Python code." [Amazon.com](https://amzn.to/3cvghHw)


## Conclusion

Although the order might suprise some, by definition, most of you must have heard of these books already.

A few additional things I learned making this list: 

- O'Reilly is the big winner of this list with 12 books in the top 25
- I'm happy to see one of my favorite editor, No Starch Press with 4 books in the list
- Mark Lutz it the author of 3 books

I must admit, this one took a while to write. If you liked this article and feel like Twitter would like it please do not hesitate to love and retweet,


it really does help :).  


## 25 most recommended JavaScript books of all-time
(coming soon)

## 25 most recommended Java books of all-time
(coming soon)
