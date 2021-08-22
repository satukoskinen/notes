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

- how to write flexible and adaptable code that bends rather than breaks
- decoupling
	- coupling is transitive and an enemy of change
	- **tip 44**: Decoupled code is easier to change
	- symptoms of coupling: dependencies between unrelated modules or libraries, "simple" changes to one module that propagate through unrelated modules in the system, developers afraid to do changes because of uncertainty of what might be affected, meetings where everyone has to attend just in case because no one's sure who will be affected by a change 
	- train wrecks (chains of method calls)
		- **tip 45**: Tell, don't ask
		- Law of Demeter: set of guidelines written by Ian Holland in the late 80s
			- a method defined in a class C should only call other instance methods in C, its parameters, methods in objects that it creates (on the stack and in the heap), and global variables
		- ... **tip 46**: Don't chain method calls (that rely on implementation details)
	- globalization
		- **tip 47**: Avoid global data
		- global data includes singletons and external resources => wrap these behind code that you control
		- **tip 48** If it's important enough to be global, wrap it in an API
	- inheritance (subclassing)

- juggling the real world
	- events
		- an event represents the availability of information
		- four strategies:
			1) finite state machines
			- a specification of how to handle events, consists of a set of states, one of which is the current state
			- for each state, we list events that are significant to that state, and for each event, we define the new current state of the system (see page 138 for an example)
			- a pure FSM is an event stream parser, and its only output is the final state; actions can be added that are triggered on certain transitions
			2) the observer pattern
			- we have a source of events, the obesrvable, and a list of clients, the observers, who are interested in those events
			- an observer registers its interest with the observable and typically passes a reference to a function to be called; when an event occurs, the observable iterates down its list of observers and calls the passed functions with the event as the parameter
			- ... introduces coupling between observers and observable, and can introduce performance bottlenecks (typically callbacks are handled inline by the observable, synchronously)
			3) publish/subscribe
			- pubsub generalizes the observer pattern: in the pubsub model, we have publishers and subscribers connected via channels that are implemented in a separate body of code
			- every channel has a name, subscribers register interest in one or more of them, and publishers write events to them => communication between the publisher and subscriber is handled outside your code
			- most cloud service providers have pubsub offerings (and popular languages their own libraries)
			- decouples the handling of asynchronous events; as a downside, it's not easy to immediately see which subscribers are involved with a particular message
			4) reactive programming and streams
			- how a spreadsheet operates: updating a cell causes all other cells that refer to that cell to update as well => the values react as the values they use change
			- streams let us treat events as if they were a collection of data
			- reactive event handling: see [reactivex.io](http://reactivex.io)

- transforming programming
	- all programs transform data by converting an input into an output
	- example: write a program that lists the five longest files in a directory tree => ``$ find . -type f | xargs wc -l | sort -n | tail -6 | head -5``
	- **tip 49**: Programming is about code, but programs are about data
	- some languages implement pipelines; in others, code can be constructed as transformations by a series of assignments
	- **tip 50**: Don't hoard state, pass it around => data as a flow

- inheritance tax
	- problems using inheritance to share code: inheritance is coupling
	- **tip 51**: Don't pay inheritance tax
	- three alternative techniques:
	1) interfaces and protocols
	- interface defines a set of methods that a class implementing it must implement also; interfaces can then be used as types, and any class that implements the interface will be compatible with that type => polymorphism without inheritance
	- **tip 52**: Prefer interfaces to express polymorphism
	2) delegation
	- **tip 53**: Delegate to services: has-a trumps is-a
	3) mixins and traits
	- merge functionality "between existing things and new things"
	- **tip 54**: Use mixins to share functionality

- configuration
	- **tip 55**: Parameterize your app using external configuration
	- common things to put in configuration data include credentials for external services, logging levels and destinations, port, IP address, machine, and cluster names the app uses, environment-specific validation parameters, externally set parameters, site-specific formatting details, license keys
	- static configuration: in plain-text formatted files (such as yaml or json) or database tables, read into the application as a data structure, normally when the application starts and commonly made global => instead, wrap the configuration information behind a "thin" API, so that your code is decoupled from the details of the presentation of configuration
	- configuration-as-a-service: store configuration behind a service API
		- multiple applications can share configuration information with authentication and access control limiting what each can see
		- configuration changes can be made globally
		- configuration data can be maintained via a specialized UI
		- configuration data becomes dynamic => no need to rebuild the code

## 6 Concurrency

- concurrency: execution of two or more pieces of code act as if they run at the same time
	- need for an environment that can switch execution between different parts of your code when it is running, often implemented with fibers, threads, and processes
- parallelism: they _do_ run at the same time
	- need for hardware that can do two things at once; multiple cores in a CPU, multiple CPUs in a computer, or multiple computers connected together
- everything is concurrent
	- in the real world, things are asynchronous
	- temporal coupling: your code imposes a sequence on things that is not required to solve the problem at hand

- breaking temporal coupling
	- two important aspects of time: concurrency and ordering
	- looking for concurrency
		- **tip 56**: Analyze workflow to improve concurrency
		- activity diagrams

- **tip 57**: shared state is incorrect state
	- nonatomic updates: processes cannot guarantee that their view of memory is consistent and up-to-date; the concent of the value can change "in the middle"
	- semaphores and other forms of mutual exclusion
		- lock/unlock, claim/release
	- make the resource transactional
	- ...problems can arise anywhere where application code shares mutable resources: files, databases, external services etc
	- **tip 58**: Random failures are often concurrency issues
	- most languages have library support for some kind of exclusive access to shared sources, maybe called mutexes (mutual exclusion), monitors, or semaphores
	- some languages have concurrency support built into the language itself, such as Rust which enforces the concept of data ownership: only one variable or parameter can hold a reference to any particular piece of mutable data at a time

	- actors and processes
		- implementing concurrency without the burden of synchronizing access to shared memory
		- an actor is an independent virtual processor with its own local, private state
			- each actor has a mailbox, and when a message appears there and the actor is idle, it jumps up and processes the message
			- when it's done with processing, it goes to process another message in the mailbox, or if there are none, it goes back to sleep
			- when processing a message, an actor can create other actors, send messages to other actors it knows about, and create a new state that will become the current state when the next message is processed
			- processes each message to completion, one message at a time
		- a process is typically a more general-purpose virtual processor, often implemented by the operating system to facilitate concurrency
			- processes can by constrained to behave like actors
		- "no single _thing_ that's in control"
		- the _only_ state in the system is held in messages and in the local state of each actor
			- all messages are one way (no concept of reply)
		=> actors execute concurrently, asynchronously, and share nothing
		- **tip 59**: Use actors for concurrency without shared state
		- Erlang: processes and a supervision system of the Erlang runtime

	- blackboards
		- detectives using a blackboard to coordinate and solve a murder investigation
			- detectives only watch the board for new information and add their findings, no need for awareness of other agents
			- detectives may come and go during the process and be trained in different disciplines; they only share the desire to solve the case
		- _laissez faire_ concurrency
		- **tip 60**: Use blackboards to coordinate workflow
	
## 7 While You Are Coding

- **tip 61**: Listen to your inner lizard
	- listening to instincts
		- first, notice when they are triggered
		- then work out why: give your brain a little time and space to organize itself
			- if needed, try to externalize the issue: sketch it up, explain it to someone or to your rubber duck
			- if that does not help, it's time for some action: put your existing code aside and make a prototype (which are meant to fail and are to be thrown away)
	- fear of the blank page: your lizard brain may be having some kind of doubt lurking below the surface of perception, and/or you may be afraid of making a mistake (+ imposter syndrome)

- **tip 62**: Don't program by coincidence
	- relying on luck and accidental successes <-> programming deliberately
	- never rely on undocumented behaviour; if you can't, at least document your assumption well
	- "close enough isn't"
	- accidents of context
	- implicit assumptions
	- how to program deliberately?
		- always be aware of what you are doing
		- can you explain the code in detail to a more junior programmer?
		- don't code in the dark: if you're not sure why it works, you won't know why it fails
		- proceed from a plan
		- rely only on reliable things; if you can't tell if something is reliable, assume the worst
		- document your assumptions
		- don't test only your code, but your assumptions as well
		- prioritize your effort on important (and often the hard) parts or aspects => without correct fundamentals and infrastructure, bells and whistles will be irrelevant
		- don't be a slave to history; don't let existing code dictate future code; be ready to refactor (assumption being that impact on schedules will be less than the cost of not making the change)

- algorithm speed
	- most nontrivial algorithms handle some variable input, the size of which will affect the algorithm's performance (resource use, such as running time or memory), with a relationship that is often not linear
	- Big-O notation, O(), is a mathematical way of dealing with approximations; "on the order of"
		- puts an upper bound on the value of the thing that's measured (time, memory, etc)
		- highest-order term will dominate the value as n increases, so the convention is to remove all low-order terms and constant multiplying factors in more complex O() functions
		- see page 205 for example runtimes of different algorithms
	- common sense estimation to determine the order of a basic algorithm
		- simple loops: from 1 to n => O(n)
			- exhaustive searches, finding a max value in an array, generating checksums
		- nested loops: from 1 to n and 1 to m => O(m x n)
			- simple sorting algorithms, such as bubble sort, tend to be O(n^2)
		- binary chop: set of input processed is halved at each iteration of a loop => O(log n)
			- binary search of a sorted list, traversing a binary tree
		- divide and conquer: input is partitioned into to halves to be worked on independently, and then combined to a result => O(n * log n)
			- quicksort (average runtime, worst-case O(n^2) with sorted input)
		- combinatoric: looking at permutations of things involves factorials => quickly gets out of hand...often, heuristics are used to reduce running types of these algorithms in particular problem domains
			- traveling salesman problem, optimally packing things into a container, partitioning a set of numbers so that each set has the same total
	- **tip 63**: Estimate the order of your algorithms
		- try to cover both theoretical and practical bases
	- **tip 64**: Test your estimates
	- the fastest one is not always the best for the job; also be wary of premature optimization
	- recommended books: Robert Sedgewick's Algorithms, An Introduction to the Analysis of Algorithms; Donald Knuth's The Art of Computer Programming books

- refactoring
	- software development != building construction ... more like gardening!
	- Martin Fowler: "disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior"
		- disciplined, targeted activity, not a free-for-all
		- external behaviour does not change (not the time to add features) => need for automated unit testing
		- refactoring is redesign
	- a day-to-day activity to help keep the code easy to change; refactoring is easier to do while the issues are still small
	- when to refactor?
		- duplication
		- nonorthogonal design
		- outdated knowledge
		- understanding gained from usage
		- performance
		- the tests pass
	- **tip 65**: Refactor early, refactor often
	- how to refactor?
		- Martin Fowler: how to refactor without doing more harm than good:
			1) Don't try to refactor and add functionality at the same time
			2) Make sure you have good tests before you begin refactoring and run them often
			3) Take small, deliberate steps

- test to code
	- **tip 66**: Testing is not about finding bugs
	=> major benefits of testing happen when you think about and write the tests, not when you run them
	- **tip 67**: A test is the first user of your code
		- testing is vital feedback tghat guides and drives your coding: writing routines to be testable makes you consider coupling and flexibility
	- test-driven development, TDD
		- basic cycle, intended to be short
			1) decide on a small piece of functionality to add
			2) write a test that will pass once the functionality is implemented
			3) run the tests and check that the only one that fails is the one just written
			4) write the minimum amount of code to get the test to pass
			5) refactor the code, then check that tests still pass
		- pitfalls of TDD
			- getting sidetracked from the real goals by the details
			- spending inordinate amounts of time to ensure a 100% test coverage
			- ending up with lots of redundant tests
			- bottom-up design
				- **tip 68**: Build end-to-end, not top-down or bottom-up => build small pieces of end-to-end functionality incrementally, learning about the problem as you go
		=> with TDD, you need to know where you're going => keep the goal and big picture in mind
	- component-based development: generic software components should  be available and combined just as easily as common integrated circuits (ICs) are combined
		- works only if components are reliable and there are common voltages, interconnect standards, timing, and so on
		- chips are designed to be tested
	=> build testability into the software from the very beginning, and test each piece thoroughly before trying to wire them together
	- unit testing
		- testing each module in isolation to verify its behaviour
		- typically, a unit test establishes some artificial, controlled environment, invokes the routines in the module under testing, and then checks the returned results either against known values or against results from previous runs of the same tests (regression testing)
		- testing against contract
			- check whether code meets the contract and that the contract means what we think it means
			- write test cases that verify that a given unit honours its contract => test that the module delivers the functionality it promises over a range of test cases and boundary conditions
			- **tip 69**: Design to test
	- ad hoc testing: poking around at code manually; if bugs were discovered, add the test to the existing unit tests
	- build a test window for tests in the production environment => provide views into the internal state of a module, such as log files containing trace messages, or more generally, a feature switch to enable extra diagnostics
	- your options: test first, test during, or test never
	- **tip 70**: Test your software, or your users will

- property-based testing
	- **tip 71**: Use property-based tests to validate your assumptions
		- properties (contracts and invariants, such as the size of an array that is sorted) are used to define rules to generate (random) test data for automated testing
	- for example the Hypothesis tool in python: provides a minilanguage to describe the data it should generate, based around calls to functions in the ``hypothesis.strategies`` module
	- test cases that uncover bugs should be added to unit tests

- stay safe out there
	- when you feel you're 90% done, you will have the _other_ 90% to consider: analyze the code for ways it can go wrong and add those to the test suite, things to consider contain passing in bad parameters, leaking or unavailable resources
	- security basic principles
	1) **tip 72**: Keep it simple and minimize attack surfaces
	- sum of all access points where an attacker can enter data, extract data, or invoke execution of a service
	- code complexity leads to attack vectors: more opportunities for unanticipated side effects
	- input data is an attack vector: never trust data from an external entity
	- unauthenticated services are an attack vector
	- authenticated services are an attack vector: minimize number of authorized users
	- output data is an attack vector: make sure the data you report is appropriate for the authorization of that user
	- debugging info is an attack vector
	2) principle of least privilege
	- use the least amount of privilege for the shortest time you can get away with
	3) secure defaults
	- default settings on your app should be the most secure values; let users decide for themselves the trade-offs between security and convenience
	4) encrypt sensitive data
	- and don't check in secrets, API keys, SSH keys, encryption passwords or other credentials alongside your source code in version control (manage separately via config files or environment variables as part of build and deployment)
	5) **tip 72**: Apply security patches quickly
	- common sense may fail you when it comes to cryptography; first rule of crypto is to _never do it yourself_ (unless you have a PhD in cryptography and a budget for long-term maintenance)
		- to implement your own login with password or biometric authentication, you need to understand hashes and salts, how crackers use things like Rainbow tables, why MD5 or SHA1 should not be used, ... let someone else worry about it and use a third-party authentication provider

- naming things
	- things should be named according to the role they play in your code
	- honor the culture of the programming language or environment
	- **tip 74**: Name well, rename when needed


## 8 Before the Project



## 9 Pragmatic Projects


