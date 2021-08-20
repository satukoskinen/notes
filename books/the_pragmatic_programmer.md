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

## 4 Pragmatic Paranoia



## 5 Bend, or Break



## 6 Concurrency



## 7 While You Are Coding



## 8 Before the Project



## 9 Pragmatic Projects


