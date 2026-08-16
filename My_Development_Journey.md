# Development Journey: From Automation Tests to Test Infrastructure

## Why I Built This

I started this project with a simple goal:

> **I wanted to create a testing framework that would make it easier for any tester to learn and start automating.**

I wanted someone who was interested in automation to be able to clone the project, look through the code, and understand:

- Where do I start?
- How is a test structured?
- Where should page interactions live?
- How do I add a new page or component?
- How do I add assertions?
- How do I extend the framework?
- Or, if I don't want to build everything myself, how can I simply use it?

That led me to build `sel-py-template` with an emphasis on **clear structure, reusable methods, and useful failure information**.

For example, I wanted common element interactions and assertions to be built into the framework rather than requiring every test author to reinvent them. I also wanted the `BasePage` methods to be well defined so that when an interaction failed, the logs would clearly identify **what action failed and why**, rather than leaving the tester with an ambiguous Selenium error.

As the project evolved, I became interested in taking the same philosophy further: **could I make other types of testing easier to adopt as well?**

That led to `pytest-a11y`, a pytest plugin that integrates Selenium and axe-core to make accessibility testing easier to add to existing UI automation.

Together, the two projects became an exploration of how to build testing tools that are not only functional, but **easy to understand, easy to extend, and useful to other engineers.**

---

## What I Learned

### 🧩 From Test Scripts to Framework Architecture

As automation grows, duplicated Selenium code becomes difficult to maintain. I explored **Page Object Model, reusable fixtures, configuration, BasePage abstractions, and shared utilities** to separate test intent from implementation.

I also focused on making the framework understandable to someone learning automation for the first time.

With `pytest-a11y`, I took that further by learning how to extend pytest itself through **fixtures, hooks, plugin registration, and custom CLI options**.

**The lesson:** I learned to think about automation as a framework that other engineers can learn from and build on—not just a collection of tests that I need to make pass.

### 🐍 Building a Real Python Package

I wanted `pytest-a11y` to be installable and usable outside of my own repository. This led me to learn **Poetry, `pyproject.toml`, dependency management, packaging, and reproducible environments**.

I also learned about designing public interfaces, using **type hints, dataclasses, TypedDicts, and Protocols**, and keeping implementation details separate from the API exposed to users.

**The lesson:** Turning working code into reusable software requires thinking about installation, dependencies, interfaces, defaults, and maintainability.

### ♿ Making Accessibility Part of Automation

**Problem:** Accessibility testing is often performed manually or as a separate activity late in the development cycle. I wanted to automatically identify common accessibility issues as part of normal UI automation.

**How I solved it / What I learned:** I integrated **axe-core through Selenium** and built it into pytest. I learned about **WCAG standards, axe rules and tags, severity levels, violations vs. incomplete results**, and configurable accessibility checks.

**The lesson:** Accessibility testing doesn't have to be a separate phase—it can become part of the automated development workflow.

### 🔍 Making Failures Useful

**Problem:** A failed test isn't very helpful if all you know is that an assertion failed. I wanted the framework to clearly communicate what interaction failed and provide enough information to troubleshoot it.

**How I solved it / What I learned:** I built reusable element interactions and assertions into the framework and added **HTML/JSON reports, screenshots, structured artifacts, violation details, and improved debugging information**, including integration with `pytest-html-plus`.

I also explored **parallel execution with pytest-xdist**, which introduced new challenges around unique filenames, shared resources, and concurrency-safe reporting.

**The lesson:** A good automation framework doesn't just detect failures—it makes failures understandable and actionable.

### 🧪 Testing the Testing Tool

I learned to separate **unit tests from integration tests** and think carefully about what should be isolated versus tested end-to-end.

Unit tests validate individual components such as configuration, result processing, and reporting, while integration tests validate the interaction between pytest, Selenium, and axe-core.

**The lesson:** Test infrastructure needs to be tested just as seriously as application code.

### 🚀 Turning Tests Into a Quality Gate

I wanted the projects to be continuously validated rather than relying on tests running successfully on my local machine.

I built **CI/CD workflows using GitHub Actions**, including separate unit and integration test stages, automated validation of changes, and preservation of test artifacts for debugging.

I also added **Dependabot** so dependency updates can be proposed automatically and validated through CI.

**The lesson:** CI/CD isn't just about running tests automatically—it creates a feedback loop that protects the quality of the framework itself.

### 🤖 Learning to Work With AI

This project was also an opportunity to learn how to use **ChatGPT and Claude as development partners**.

I used AI throughout the process to explore architecture options, understand unfamiliar APIs, generate implementation ideas, troubleshoot errors, identify edge cases, develop test scenarios, and improve documentation.

But I didn't treat AI-generated code as automatically correct. I had to **evaluate suggestions, run the code, write tests, investigate failures, and revise the implementation**.

**The lesson:** AI can significantly accelerate development, but engineering judgment, testing, and validation remain essential.

---

## The Biggest Lesson

The biggest thing I learned was how to **think beyond individual automated tests and start thinking like a framework developer**.

I started with an idea for making automation approachable for testers, and ended up learning about Python package development, pytest plugin architecture, API design, type safety, accessibility standards, reporting and observability, parallel execution, unit versus integration testing, CI/CD, dependency management, and AI-assisted development.

But the biggest shift for me wasn't any individual technology.

It was learning to think about **the person who will use the framework**:

- How do I make installation easy?
- How do I make the code understandable to someone learning automation?
- How do I provide sensible defaults?
- How do I make failures easy to debug?
- How do I prevent changes from breaking existing functionality?
- How do I make the framework easy to extend?
- How do I make the common use case simple without limiting advanced users?

That mindset changed how I approach automation engineering.

---

## What I Would Do Differently

Building this project taught me that architecture decisions become harder to change as a project grows.

Some functionality started with a simple implementation and was later refactored as I encountered new requirements around **reporting, parallel execution, configuration, and extensibility**.

If I were starting again, I would spend more time upfront defining:

- The public API and plugin interfaces
- The reporting and artifact model
- Configuration boundaries
- What should be extensible versus internal
- The testing strategy for each layer

I would still iterate quickly, but I would spend more time identifying the parts of the system that are likely to become foundational.

**That was an important lesson for me: balance building quickly with designing for the future.**

---

## Looking Back

This project started with a goal of making **automation easier to learn and easier to adopt**. It eventually became an opportunity to learn how to build **reusable testing infrastructure from the ground up**.

More importantly, it helped me expand my thinking from:

> **“How do I automate this test?”**

to:

> **“How do I build a reliable tool that makes automation easier for other testers?”**

That shift—from test automation to **test infrastructure and software engineering**—is the most valuable thing I took away from this project.