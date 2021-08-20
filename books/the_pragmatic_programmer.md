# The Pragmatic Programmer 20th Anniversary Edition (Dave Thomas & Andy Hunt)


## 1 A Pragmatic Philosophy

- an attitude, style or philosophy of approaching problems and their solutions; placing them in their larger context
- taking responsibility for everything one does
=> need for a broad knowledge base => a "knowledge portfolio" to organize continuous learning
- a pragmatic programmer is
	- an early adopter/fast adapter
	- inquisitive
	- critical thinker
	- realistic
	- jack of all trades

**tip 1**: Care about your craft

**tip 2**: Think about your work

**tip 3**: You have agency

**tip 4**: Provide options, don't make lame excuses

- software entropy / software rot / technical debt
	- **tip 5**: Don't live with broken windows

**tip 6**: Be a catalyst for change

**tip 7**: Remember the big picture

**tip 8**: Make quality a requirements issue

**tip 9**: Invest regularly in your knowledge portfolio

- building a portfolio
	- invest regularly
	- diversify
	- manage risk
	- buy low, sell high
	- review and rebalance

**tip 10** Critically analyze what you read and hear

**tip 11** English is just another programming language

**tip 12** It's both what you say and the way you say it

**tip 13** Build documentation in, don't bolt it on


## 2 A Pragmatic Approach

- essense of good design: the ETC principle (easier to change)
	- ... involves educated guessing
	- **tip 14** Good design is easier to change than bad design

- DRY (don't repeat yourself): avoid duplicating knowledge (not just source code!)
	- "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system"
	- when some single facet of the code changes, does that change have to be made in multiple places and multiple different formats?
	- ...not all code duplication is knowledge duplication (if they represent different kinds of knowledge!)
	- DRY violations in documentation and data
	- **tip 16**: Make it easy to reuse

- orthogonality: two or more things are orthogonal if changes in one do not affect any of the others
	- avoid splitting one piece of knowledge across multiple system components => prefer loosely coupled, independent components with a single, well-defined purpose
	- **tip 17**: Eliminate effects between unrelated things
	- increases productivity (localized changes reduce development and testing time, and orthogonality promotes reuse)
	- reduces risk (buggy code is more isolated, and the system will be less fragile and less tightly coupled to some particular vendor/product/platform with interfaces isolated to smaller parts of overall development)
	- design: may be called modular, component-based, or layered
	- coding:
		- keep code decoupled and "shy" (modules that only reveals what's necessary and do not reply on other modules' implementations)
		- avoid global data (every time a piece of code references global data, it ties itself to other components sharing that data)
		- avoid similar functions
	- testing:
		- writing unit tests can itself act as a test or orthogonality

- reversibility
	- requirements, users, and hardware change faster than we can develop software
	=> create appropriate abstraction layers, break code into components
	- **tip 18**: There are no final decisions

- tracer bullets
	- tracer bullet development: need for immediate feedback under actual conditions with a moving goal (need to know how the application as a whole hangs together)
	=> look for something that gets you from (important, system-defining) requirements to some aspect of the final system quickly, visibly, and repeatably
	=> tracer code is lean but complete, and forms part of the skeleton of the final system <-> prototyping that generates disposable code
	- an incremental approach <-> "heavy engineering": code divided into modules which are each coded in a vacuum
	- **tip 20**: Use tracer bullets to find the target
	- advantages:
		- users get to see working examples early
		- developers build a structure to work in
		- you have an integration platform (integrate daily rather than on one big bang)
		- you have something to demonstrate
		- you have a better feel for progress

- prototypes and post-it notes: 
	- disposable code to sketch out, identify and correct potential problems early in the development cycle
	- things to investigate with a prototype: anything that carries risk, hasn't been tried before, or is critical to the final system, such as
		- architecture
		- new functionality in an existing system
		- structure or contents of external data
		- third-party tools or components
		- performance issues
		- user interface design
	- prototypes focus on specific aspects and do not concern themselves with irrelevant details
	- **tip 21**: Prototype to learn

- domain languages
	- **tip 22**: Program close to the problem domain
	- internal (RSpec, router library) and external (Cucumber, Ansible) domain languages

- estimating
	- **tip 23**: Estimate to avoid surprises
	- context: how accurate is enough => consider the units used
	- process of deriving estimates:
		- understand what is being asked
		- build a model of the system
		- break the model into components: how components interact, what kind of parameters affect each
		- give each parameter a value
		- calculate answers (maybe over distributions of critical values)
		- keep track of how estimates fared


## 3 The Basic Tools

- the power of plain text
	- **tip 25**: Keep knowledge in plain text

- shell games
	- **tip 26**: Use the power of command shells
	- configure your shell: set color theme, configure the prompt, add often-used commands as simpler aliases, configure command completion

- power editing
	- **tip 27**: Achieve editor fluency
	- the challenge list:
• When editing text, move and make selections by character, word, line, and paragraph.
• When editing code, move by various syntactic units (matching delimiters, functions, modules, ...).
• Reindent code following changes.
• Comment and uncomment blocks of code with a single command.
• Undo and redo changes.
• Split the editor window into multiple panels, and navigate between them.
Power Editing • 81
Tip 27
Achieve Editor Fluency
report erratum • discuss
• Navigate to a particular line number.
• Sort selected lines.
• Search for both strings and regular expressions, and repeat previous searches.
• Temporarily create multiple cursors based on a selection or on a pattern match, and edit the text at each in parallel.
• Display compilation errors in the current project.
• Run the current project’s tests.
	- grow your editor: get familiar with the editor's extension ecosystem

- version control
	- a giant undo key!
	- and so much more: tool for collaboration, deployment pipelines, release tracking, issue tracking, general team interaction, ...
	- **tip 28**: Always use version control
	- a thought experiment: if you spill a cup of tea on your laptop and destroy it, how long would it take to get a new machine back to that state?
	=> store _all_ configuration files, lists of software, scripts, and current projects in a VCS

- debugging
	- debugging is just problem solving
	- **tip 29**: Fix the problem, not the blame
	- a debugging mindset:
		- **tip 30**: Don't panic
		- try to discover the root cause of the problem, not just this particular surfaced appearance of it
	- isolate the bug and write a test to reproduce it: **tip 31**: Failing test before fixing code
	- but first, **tip 32**: Read the damn error message
	- binary chop: employ a binary search strategy in debugging (finding the right stack frame where error occurs, narrowing down what kind of input data causes a problem, determine which release has introduced a bug, etc)
	- process of elimination: start with the assumption that the bug exists in your application code and not on the third-party library, compiler, OS, etc
		- **tip 33**: "select" isn't broken
	- **tip 34**: Don't assume it - prove it
	- a debugging checklist
• Is the problem being reported a direct result of the underlying bug, or merely a symptom?
• Is the bug really in the framework you’re using? Is it in the OS? Or is it in your code?
• If you explained this problem in detail to a coworker, what would you say?
• If the suspect code passes its unit tests, are the tests complete enough? What happens if you run the tests with this data?
• Do the conditions that caused this bug exist anywhere else in the system? Are there other bugs still in the larval stage, just waiting to hatch?

- text manipulation

- engineering daybooks: keeping a journal on what you do, learn, sketches of ideas, notes, debugging values, reminders, doodles
	- a notebook is more reliable than memory
	- place to store ideas
	- acts as a kind of a rubber duck to reflect with


## 4 Pragmatic Paranoia

- **tip 36**: You can't write perfect software
- Bertrand Meyer: Design by Contract, DBC, is a technique that focuses on documenting the rights and responsibilities of software modules to ensure program correctness
	- preconditions: the routine's requirements => what must be true in order for the routine to be called
	- postconditions: what the routine is guaranteed to do => state of the world when the routine is done
	- class invariants: a class ensures that this condition is always true from the perspective of a caller (which means that the class cannot permit unrestricted write access to any data that participates in the invariant); more generally, a state
	=> the contract between a routine and any potential caller can be stated as "If all the routine's preconditions are met by the caller, the routine shall guarantee that all postconditions and invariants will be true when it completes"
	=> if either party fails to live up to this (a bug!), an agreed remedy is invoked (such as an exception, program termination)
	- **tip 37**: Design with contracts
	- implementing DBC
		- document the input domain range, boundary conditions, and what the routine promises to deliver (and what it does not) <-> "programming by coincidence"
		- assertions (runtime checks of logical conditions): make the compiler (partially) check the contract for you
	- crashing early: much easier to find and diagnose the problem

- dead programs tell no lies
	- **tip 38**: Crash early

- assertive programming
	- **tip 39**: Use assertions to prevent the impossible
	- leave assertions turned on

- how to balance resources
	- **tip 40**: Finish what you start
	- a function or object that allocates a resource should be responsible for deallocating it
	- **tip 41**: Act locally
	- nest allocations: deallocate resources in the opposite order to that in which they were allocated, and when allocating the same set of resources in different places, always allocate them in the same order
	- when resources can't be balanced:
		- programs that use dynamic data structures
		=> establish a semantic invariant for memory allocation => who is responsible for data in an aggregate data structure
	- checking the balance: wrappers for each type of resource

- don't outrun your headlights
	- **tip 42**: Take small steps - always
	- small, deliberate tests, checking for feedback and adjusting before proceeding
	- **tip 43**: Avoid fortune-telling


## 5 Bend, or Break



## 6 Concurrency



## 7 While You Are Coding



## 8 Before the Project



## 9 Pragmatic Projects


