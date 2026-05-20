# Contributing to Awesome Architecture Patterns

First off, thank you for considering contributing to Awesome Architecture Patterns! This repository is a community-driven, multi-level taxonomy of software architecture and design patterns, scaling from macro-level cloud topologies down to micro-level object interactions. Your contributions help make this a central index of resources, documentation, and implementation examples for curious people worldwide.

We want to build the most comprehensive catalog of architectural concepts on the web. This is **not an academic resource** meant to gatekeep patterns based on historical prestige. Instead, our goal is to collect as many concepts as possible from across the industry, including classic standards, emerging trends, experimental models, and lesser-known patterns. If it's being used, experimented with, or discussed in the wild, it belongs here!

## Contribution Criteria

To maintain a well-structured index, please make sure your contributions align with the following guidelines:

### 1. Broad Pattern Inclusivity and Categorization
* **All Concepts Welcome**: We welcome classical patterns (e.g., from *POSA*, *Gang of Four*, *DDD*, *Clean Architecture*, *Enterprise Integration Patterns*), but we are equally excited about modern, experimental, custom, or niche patterns found anywhere in the software engineering ecosystem.
* **Clear Categorization**: Your pattern or entry should fit logically into the existing multi-level taxonomy layers:
  * **Layer 1**: System Architecture Patterns
  * **Layer 2**: Enterprise Integration Patterns
  * **Layer 3**: Application Architecture Patterns
  * **Layer 4**: Software Design Patterns
  * **Cross-Cutting Concerns** or **Enterprise Architecture Frameworks**

### 2. High-Quality, Public Reference Implementations
* **Real-World Examples**: Examples must point to public, visible source code repositories (e.g., GitHub, GitLab) that clearly and cleanly demonstrate the pattern in action.
* **Functional Code**: The code repositories must be functional, well-structured, and serve as reference material.
* **What is NOT sought**: Avoid basic "Hello World" scripts, standard tutorial templates (like generic "PokeAPI" or "To-Do" apps), or low-effort repositories unless they have been heavily expanded to show a clear implementation of the specific pattern.

### 3. Formatting
All pattern additions must match our standard `<details>` folding format to keep the README readable and clean. Use the following template:

```markdown
<details>
<summary><strong>Pattern Name:</strong> A single, clear sentence summarizing what the pattern does.</summary>

A comprehensive and detailed description explaining the problem, the core mechanics of the pattern, when to use it, and its benefits or trade-offs (typically 2-4 sentences).

- **Examples:**
  - [owner/repo](https://github.com/owner/repo): A clear and concise description explaining how this repository implements the pattern in a functional or highly illustrative manner.
- **Resources:**
  - "Resource/Article/Book Title" by Author Name: A brief note on what this resource covers and why it is a valuable reference.

</details>
```

* **Alphabetical Order**: Please make sure you insert your pattern or resource in alphabetical order within its respective category or list.

## How to Submit

1. **Fork the Repository**: Create a fork and branch off from `main`.
2. **Make Your Changes**: Update `README.md` with your new pattern, resource, or example, ensuring it complies with the criteria above. If you are fluent in Spanish or Chinese, we encourage you to also update the respective translation files (`README.es.md` and/or `README.zh.md`), but this is entirely optional (see our [Multi-Language Policy](#multi-language-policy) below).
3. **Open a Pull Request**:
   * Provide a clear and concise description of what you are adding.
   * Explain why the pattern, example, or resource is a valuable addition to the taxonomy.
   * Confirm that your additions adhere to the exact formatting standard.

## Multi-Language Policy

This repository is multilingual to make software architecture patterns accessible to as many developers globally as possible. To keep the catalog synchronized without adding friction for contributors, we follow these guidelines:

* **English as the Source of Truth**: The English [README.md](README.md) is our primary index. All new patterns, reference implementations, and resources must be added to it.
* **Optional Translation Submissions**: If you are comfortable translating your addition into Spanish or Chinese, you are warmly invited to update [README.es.md](README.es.md) and/or [README.zh.md](README.zh.md) within the same Pull Request.
* **Maintainer-Led Syncing**: If you only submit your changes in English, your contribution is still 100% welcome! The maintainers will handle translating and syncing your additions to [README.es.md](README.es.md) and [README.zh.md](README.zh.md).

## Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md).

Thank you for helping to build this comprehensive reference index for software architecture!
