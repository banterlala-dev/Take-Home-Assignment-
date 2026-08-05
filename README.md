# Contented Engineering Intern Take-Home Assessment

### My actual github is ([GitHub](https://github.com/Andrew-Zhang-Repository))

## Part 1: How you learn

**Show us something you're proud of. A project, a hack, a fix, a thing you built for fun, anything.**

I am proud of an automated pull request checker that I have built  ([PIP  LINK HERE](https://pypi.org/project/ollama-local-reviewer/)) , which is a local multi-agent code review tool I built that uses Ollama-hosted LLMs to analyze git diffs and produce structured PR review, that runs locally completely for free. I have also configured a CI/CD github workflow hook that activates on push and automatically publishes the latest version onto Pip. I engineered this specifically to bypass the limitations of relying on expensive cloud models and the tight resource constraints of GitHub Actions VM.

It works by having a Jinja pipeline acting as a different agent. Each agent evaluates the code and returns a JSON score out of 100, there are agents on scalability,security, codesmells, and readability. If any agent detects a critical flaw, like a security vulnerability or a major architectural issue the commit is blocked with an exit code. However, I designed it with developer flexibility in mind, allowing users to bypass the PR check and commit anyway if needed. Once all agents finish, a synthesized md file is generated right in the execution directory. It supports multiple configurable models (like gemma3:12b, qwen3:4b, and mistral:7b) via a providers.yml file, making it highly adaptable for local machines and can be customarily changed.

---

**Tell us about a time you had to unlearn something. A habit, a technique, an approach you thought was right until it wasn't.**

I had to unlearn the habit of attempting to design the perfect, exhaustive system architecture before writing any code. I used to map out every possible package, database schema, and edge case that I could possibly think of, thinking it would save time later. However, I quickly realized this was actually quite counterproductive as inevitably, conflicting package versions, unforeseen framework limitations, or changing requirements would render the initial plan obsolete.

For example, while building a full-stack application relying on specific cloud APIs and old un-updated packages, my rigid upfront schema didn't account for unexpected permission issues and deployment constraints I only discovered during implementation. Now, I favor a more adaptable approach while retaining heavy planning but less detailed than before. I now favour a more lightweight plan covering the core logic flows, then start building immediately, allowing the architecture to evolve organically as I encounter problems. 

---

**What are you deliberately getting better at right now? Doesn't have to be technical. How are you going about it? What's the actual practice, not just the intention?**

I am improving my proficiency in lower-level languages, specifically C++. While I am comfortable with higher-level languages for full-stack development, I want a deeper, more understanding of memory management and system-level performance. My actual practice to improve upon this involves hands-on building rather than just reading documentation or writing up basic DSA questions. Currently, I am building a BitTorrent client from scratch in C++ without any torrent libraries. This forces me to actively grapple with network protocols, socket programming, and concurrent data handling in a highly practical, unabstracted way. 

## Part 2: How well you know yourself

**Tell us about something that failed, a project, an exam, a build, a team. What actually caused it, and what was your part in it?**

I recently built a personal utility tool designed to capture a screenshot via a custom hotkey set in your environment vars and extract text and data from it. Initially, I used a lightweight OCR library(pytesseract, img2table), but it completely failed to accurately parse structural elements like diagrams and grids. I decided to pivot to a local Vision-Language Models. However, I quickly hit a hardware wall running a sufficiently capable, unquantized VLM was far too straining for my local machine, and the project ultimately stalled and running quantised versions would result in hallucinations of converting the Image to text. My failure here was poor upfront resource planning. I was too focused on the software logic and completely failed to anticipate the hardware bottleneck. I could have circumvented this by renting a cloud server for processing, but a strict requirement of my project was keeping it cost-free. It taught me about validating hardware and infrastructure constraints before committing to a specific architectural path instead of tunnel visioning on the software part. 

---

**What is your favorite movie?**

##### Spider-Man: Into the Spider-Verse (2018)
![Image](https://resizing.flixster.com/xVd9PLVkH69dU3Yo9XLSjdMeu1M=/206x305/v2/https://resizing.flixster.com/_l50Ahm00b-RO9Ao2s3AyMjUWiU=/ems.cHJkLWVtcy1hc3NldHMvbW92aWVzL2ExYTZmMWFkLWViZWItNDNhMS1iZTEwLTcxODk1YTk3NWFhMy53ZWJw)

## Part 3: How you get things done

**Tell us about a time you hacked the system. What was the system, what did you do, and would you do it again? For example: found a loophole in a competition's rules and used it, automated a mind-numbing part of a part-time job without asking, or talked your way into an event, a lab, or a meeting you weren't supposed to be in. Big or small we don’t care!**

In a previous contract based tutoring/teaching role, I was tasked with manually reviewing, cleaning, and merging weekly exported CSV reports from two different legacy tracking tools based on the attendance and performance of multiple classes of students. The headers were inconsistent, formatting was mismatched, and it was wasting a lot of unpaid time manually copying and pasting rows in Excel.

Instead of doing it manually, I wrote a Python script using Pandas, packages available on git. I set up a local script that parsed the raw CSV dumps, normalized the column schemas, automatically filled in missing metadata or dropped them or used appropriate package functions, and generated a unified report. I turned a multi-hour weekly chore into a single terminal command. I even quickly added a barebones streamlit + python combo frontend backend combo that includes a drag and drop input and download cleaned csv option. 

---

**How do you plan a project? Walk us through your actual step-by-step when the brief is ambiguous: how do you decide what to work on first, and how do you know if you're on track?**

When faced with an ambiguous brief, my strategy balances system design with a strong bias toward action, software, and now hardware constraints. I like a decent but lighter planning stage hence I plan outlining the core logic flow and selecting the primary services, frameworks, libraries, packages, choice of services like database depending on what I’m making and the system design aspect too. But I avoid over-engineering the plan because too much upfront planning leads to wasted effort when real-world integration issues arise. If it's a client I make sure the scope is established after multiple meetings, or until they are satisfied with my mock up plans before the implementation phase. 

I know I am on track if I have a functional, albeit bare-bones, prototype running early or if it's a client based project. I know I'm on track for each sprint if my project fits the scope of what they want each meeting. This allows me to adapt and iterate based on tangible results rather than theoretical plans for both individual and professional scenarios.
