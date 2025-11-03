---
layout: post
title: Using Mermaid for Diagram-Based Documentation
category: thoughts
tags:
  - documentation
  - architecture
  - mermaid
  - c4-model
  - diagrams-as-code
  - software-architecture
---

As I mentioned in my [previous post]({% post_url 2025-10-31-How-create-good-readme %}), documentation should originate from a single source of truth and branch out to provide detailed information as needed. The repository's README file is the most common starting point.

Documentation often benefits from visual support through diagrams. Mermaid offers a simple, elegant solution for creating and embedding diagrams directly in README files or any linked markdown document. By using a text-based syntax, diagrams become version-controlled, reviewable, and maintainable alongside your code. Check out this [example of how Mermaid works](https://github.com/alexcuesta/mermaid-test) in my repository.

Mermaid supports the [C4 model by Simon Brown](https://c4model.com/), a hierarchical approach to documenting software architecture across four levels of abstraction:

* **Level 1 - [System Context](https://c4model.com/abstractions/software-system)**: Shows how your system fits within the broader ecosystem of users and external systems
* **Level 2 - [Containers](https://c4model.com/abstractions/container)**: Depicts the high-level technical building blocks like frontend/backend services, applications, and databases
* **Level 3 - [Components](https://c4model.com/abstractions/component)**: Details the internal structure including libraries, modules, and major components
* **Level 4 - [Code](https://c4model.com/abstractions/code)**: Provides fine-grained views of code elements such as interfaces, classes, and functions

When documenting your repository, choose the appropriate level based on scope. For individual repositories, levels 3 or 4 work well to illustrate components and code structure. For broader features spanning multiple services, consider placing a README in a monorepo or parent repository with level 1 or 2 diagrams to provide the big picture view.

