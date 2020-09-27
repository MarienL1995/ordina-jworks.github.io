---
layout: post
authors: [bjorn_de_craemer, steve_de_zitter]
title: 'Evolutionary architecture: Protect your agility using fitness functions and appropriate quantum size'
image: /img/2020-09-27-evolutionary-architecture/evolutionary-architecture.jpg
tags: [ARCHITECTURE]
category: Architecture
comments: false
---

# Table of Contents

* [Story Line](#story-line)
* [What do we mean by evolutionary architecture](#what-do-we-mean-by-evolutionary-architecture)
* [What is software architecture](#what-is-software-architecture)
* [How can we prevent an architecture from degrading over time?](#how-can-we-prevent-an-architecture-from-degrading-over-time)
* [Multiple architectural dimensions](#multiple-architectural-dimensions)
* [Conways law](#conways-law)
* [Fitness functions](#fitness-functions)
* [Architectures that support incremental change](#architectures-that-support-incremental-change)
* [Testability of software architecture](#testability-of-software-architecture)
* [Ownership of fitness functions](#ownership-of-fitness-functions)
* [Example fitness functions](#example-fitness-functions)

## STORY LINE

* Architectural characteristics and dimensions
What are some common characteristics and dimensions. Describe an architects responsibility to maintain balance between often orthogonal characteristics.
* What's our definition of evolutionary architecture?
Evolutionary architecture describes some techniques to maintain that balance between characteristics. 
In doing so, we make sure that all future architectural changes and decisions fit into our described characteristics. 
This allows our architecture to NOT degrade over time.
* Fitness functions
Describe fitness functions and their ability to measure how the architecture responds to changes (and how the characteristics respond to changes)
	*  overview of different types of fitness functions (triggered vs continual, static vs dynamic, automated vs manual, temporal, intentional over emergent, domain-specific)
* Quantum size
Describe quantum size (size of deployable unit? etc.) and its relationship to the ability to change, agility, preventing architectural degradation, implementing fitness functions, etc

## What do we mean by evolutionary architecture

Evolutionary architecture is the discipline of software architecture where we try to create and maintain an architecture that is able to respond to change in requirements or change of our understanding of the problem. 
At the beginning of the project as well as five years down the road.

Agile ways of working have thought us to embrace change and work in small iterations. 
With that new way of working has come some sort of movement that states that we shouldn't be doing a lot or even any architecture efforts, because of our agile way of working and thus solving problems when they occur.
That's kind of shortsighted, because of course some architectural work and design efforts are necessary when working in an Agile way.

Since we can't predict what the future will look like, we can't spend too much time on these architecture phases. 
We can however define the abilities that we believe our product should have. 

## What is software architecture

Software architecture begins with thoroughly understanding the business or domain requirements that were the motivation for designing a software solution.
However, understanding the domain requirements alone is not enough and thus there are other factors to be kept in mind. 
Some explicit (non functionals such as performance requirements, security requirements, etc) and other implicit ('The company is embarking on a mergers and acquisitions spree' -> replace with TVH example. Company had shortage of stock to be able to respond to swiftly enough to customer demand)

Definition stolen from Building Evolutionary architectures chapter 1 page 1:
Therefore, the craft of software architecture manifests in the ability of architects to analyze business and domain requirements along with other important factors to find a solution that balances all concerns opti‐ mally. The scope of software architecture is derived from the combination of all these architectural factors,

These additional factors besides the domain requirements are often referred to as ilities.
The below table lists some of them:

accessibility affordability compatibility customizability dependability effectiveness fault tolerance integrity mobility portability provability reproducibility safety securability sustainability
accountability agility composability debugability deployability efficiency fidelity interoperability modifiability precision recoverability resilience scalability simplicity tailorability
accuracy auditability configurability degradability discoverability usability flexibility learnability modularity predictability relevance responsiveness seamlessness stability testability
adaptability autonomy correctness determinability distributability extensibility inspectability maintainability operability
process capabilities reliability
reusability self-sustainability standards compliance timeliness
administrability availability credibility demonstrability durability
failure transparency installability manageability orthogonality producibility repeatability robustness serviceability survivability traceability

Change in technical or domain landscape are inevitable.
Consequently, we should architect our systems knowing the technical landscape will change

## How can we prevent an architecture from degrading over time?

We've all been through this. We build a green-field solution and the first months we're able to quickly implement new features, adapt to changing requirements etc.
The solution manages to hit all performance targets, our apis have been secured etc
But after a while, this progress starts to stagnate. 
And we're hitting certain boundaries to what we can achieve.
It becomes increasingly complex to add new features, you start to get this feeling that making architectural changes becomes hard, and as a result, you start to postpone necessary changes because it's becoming hard to do them and of course you're dealing with the pressure from business who is still expecting a certain amount (inceasingly more, because your velocity is increasing right?) of functionalities to be delivered on time.

At this point, the system is already getting into a degraded state. 
And the vicious circle of postponing necessary architectural changes to support future maintainability and evolvability makes this worse and worse.

The problem is, that while we were making tremendous progress at the beginning of our product lifetime, we forgot to ensure balance between our initially chosen ilities.
We made architectural changes, while at the same time, not making the necessary trade-offs to ensure balance between our ilities. 
We made decisions without validating we weren't breaking any rules (rules that were defined to protect out application's ilities).

Maintaining evolvability in our architectures means we have to closely measure and monitor the set of ilities that are important for our product and make sure that balance is preserved between them.
Evolvability becomes a meta-characteristic, an architectural wrapper that protects all the other architectural characteristics (Quote from evolutionary architectures: How can I prevent my architecture from degrading over time. Paragraph 2. page 6).

Evolutionary Architecture definition (Page 6):
An evolutionary architecture supports guided, incremental change across multiple dimensions.

Continual architecture: Building architectures that have no end-state.

Borrowing a concept from evolutionary computing, called fitness functions, we can protect our most important software architecture characteritics.
Fitness function are objective functions that can determine how "fit" each new variant of our architecture actually is considering the characteristics. 
These fitness functions can be:

* metrics
* tests
* other verification tools

Whenever architects identify an architectural characteristic they wish to protect, they define one or more fitness functions to protect that feature.

Evolutionary architecture is not an unconstrained, irresponsible approach to software development. 
Rather, it is an approach that balances the need for rapid change and the need for rigor around systems and architectural characteristics. 
The fitness function drives architectural decision making, guiding the architecture while allowing the changes needed to support changing business and technology environments

## Multiple architectural dimensions

In the past, architects have focussed largely on the (software)technical dimensions of architecture. However, architecture is a combination of several dimensions that need to be kept in balance. 
So we can't just focus on the (software)technical aspects of architecture but should also keep into account:

* Technical: The implementation parts of the architecture: the frameworks, dependent libra‐ ries, and the implementation language(s).
* Data: Database schemas, table layouts, optimization planning, etc. The database administrator generally handles this type of architecture.
* Security: Defines security policies, guidelines, and specifies tools to help uncover deficien‐ cies.
* Operation/System: Concerns how the architecture maps to existing physical and/or virtual infra‐ structure: servers, machine clusters, switches, cloud resources, and so on.

Several partitioning and modeling techniques exist to support architects in conceptually splitting their architectures.

* 4+1 architecture View Model
* C4 model
* (Others? Wardley maps?)


## Conways law

Describe coupling between organizational/team structure and the resulting architecture.
Also describe the coordination efforts required to implement and release functionality developed by e.g. 3 different teams split acros technical boundaries. (Chap 1, Conways law)

Consider applying inverse conway to mitigate the problems caused by conways law (not evident when needing to apply at enterprise levels).
Inverse conway maneuvre also present on the thoughtworks technology radar.

**Evolutionary = Incremental + (not least) GUIDED!!**


## Fitness functions

* **Explain what fitness functions are**
* Types of fitness functions
	* triggered vs continual
	* static vs dynamic
	* automated vs manual
	* temporal
	* intentional over emergent
	* domain-specific

(COPY PASTE FROM BOOK)Teams that do not identify their fitness functions face the following risks:

* Making the wrong design choices that ultimately lead to building software that fails in its environment
* Making design choices that cost time and/or money but are unnecessary
* Not being able to evolve the system easily in the future when the environment changes

## Architectures that support incremental change

* from dev perspective: How devs build software
* from ops perspective: How teams deploy software

Very important that incremental change is supported by Continuous Delivery and its supporting engineering practices.
These practices alow an architecture and software to be changed and deployed very quickly, allowing the software to evolve in small steps. 

An architecture drawn with boxes and arrows shows only a 2D view of that architecture, while we're living in a 4D World. 
We want our architecture to be able to cope with changes in technology, to be patched in case of security vulnerabilities, etc. 
Basically want to create an architecture that is able to cope with unknown unknowns when they start occuring (Which is inevitable?).

### Testability of software architecture

Since tests are a mechanism used to define fitness functions, we should very much think about how testable our architecture is and even create and design our architectures with testability in mind.
This will prevent us from ending up in scenarios where a given aspect of the software system is very hard to test because we didn't consider it right from the start. (REREAD AND VERIFY THIS STATEMENT)

ArchUnit and JDepend for testing of coupling and dependency directions

Once our fitness functions have 'all' been defined it is important that these functions are evaluated in timely manner. 
Automating most of these in a deployment pipeline is exactly what enables us to verify these functions regularly.


### Ownership of fitness functions

In general, the definition and maintenance of fitness functions is a shared responsibility between architects, developers, and any other role concerned with maintaining architectural integrity

## Example fitness functions:

Automatic fitness functions:

* Automatic cleanup of services and resources that do not receive traffic for certain amount of time (janitor monkey? k8s cleanup of orphaned resources or dangling images/volumes or ...)
* monitoring of routes between services (ms dashboard??? Service meshes? routing proxies? etc...)
* monitoring and logging tools. (Any tool that helps assess some architectureal characteristic qualifies as a fitness function!!!)
* Sonarqube: bugs, coverage, cyclomatic complexity
* Checkstyle: coding standards
* Vulnerability checks (Snyk? others? Automating those with atomist?)
* Dependency Version tracking. Perform aggresive version increments because the longer you wait, the harder version increments get
* Unit tests
* Integration tests
* BDD tests
* contract tests
* ArchUnit or JDepend tests
* performance tests (Gatling?)
* Scalability tests (tool?)
* Resilience tests (tool?)
* Production testing! Smaller quantum sizes, distributed software, cloudnative software enable more sophisticated deployment strategies that allow us to test and verify behaviour in realistic production environments. (refer to test in prod blogpost: https://tersesystems.com/blog/2020/01/22/developing-in-production/ AND refer to quote in book somewhere...)
* refactoring testing (holistic, continual): https://github.com/rawls238/Scientist4J 
* a/b testing
* tracing (performance metrics) icm canarying or blue/green testing
* Choas testing (Chaos monkey, Simian army, choas kube, ...)
* Security testing (Using tools similar to Simian army? continual security stress testing?)

Refer to Observability Driven Development???

NOT all fitness functions can be performed automatically, although our ambition should be to automate them and not jeopardise our agility

Manual fitness functions:

* Exploratory testing?
* Functional testing?
* ???

https://netflixtechblog.com/product-integration-testing-at-the-speed-of-netflix-72e4117734a7

# TODOS
General:

* Make connection to Sam Newman Building microservices (Evolutionary architect)? En evt blog Peter De Kinder (https://evolute.be/reviews/buildms.html)
* Refer to industrialLogic blog on primitive whole?
* Refer to new documentation techniques such as C4 and 4 + 1?
