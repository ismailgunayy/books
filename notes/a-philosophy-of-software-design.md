## A Philosophy Of Software Design by John Ousterhout

---

### Chapter 1 - Introduction

Introductory chapter for the book.

---

### Chapter 2 - The Nature of Complexity

The chapter defines what complexity is, what the main causes and the symptoms are. 

What complexity is:
> Complexity is what a developer experiences at a particular point in time when trying to achieve a particular goal.

A formula for the overall system complexity:  $$C = \sum_{p} C_p t_p$$

Which means:
> The overall complexity of a system (*C*) is determined by the complexity of each part *p*($c_p$) weighted by the fraction of time developers spend working on that part ($t_p$).

This means that if you manage to isolate or even hide the complexity in a system, it's nearly as good as eliminating that complexity.

Causes of complexity:
1. **Dependencies**: If a developer cannot understand or modify a piece of code without considering some other code, and the other code must be considered, or worse, modified if the given code is changed, there is a dependency.
2. **Obscurity**: Obscurity occurs when an important piece of information needed is not obvious (e.g. the name of an entity), or worse, the developer is not aware that they need a piece of information to take an action without causing any issue. 

Symptoms of complexity:
1. **Change Amplification**: The amount of modification you need to do in order to complete a seemingly and supposedly simple task.
2. **Cognitive Load**: The amount of knowledge that the developer needs to have in order to complete a task.
3. **Unknown Unknowns**: The fact that it is not obvious to the developer which part of the system they need to modify or what information they should have in order to complete a task.

**Key Takeaways:** 
- Complexity is the sum of the forces working against the developer when tackling a task.
- Hiding complexity is almost as good as removing it, if not possible to completely remove.
- The complexity does not occur overnight. It gets incrementally bigger as small chunks of dependencies and obscurities add up.

---

### Chapter 3 - Working Code Isn't Enough

The chapter discusses why the strategic approach is better than the tactical approach in the long run.

- **Strategic Programming**: This approach requires the developer to invest some time in system design, think about the bigger picture, introduce a minimal amount of complexity, or ideally reduce it, when changing a piece of code regardless of its size. It usually results in tasks taking 10-20% longer, but pays off very well in the long run. Simply put, "Working code isn't enough".
- **Tactical Programming**: This is considered a short-term solution. It only makes changes that take the least amount of time and usually the easiest to implement. It creates more problems in the long run. *Technical debt* is often caused by this approach.

**Key Takeaway:** We should continually invest in good design, so that small problems don't add up and turn the system into a mess. It's not a one-off; we need a mentality of constantly looking for improvements and executing them when possible.

---

### Chapter 4 - Modules Should Be Deep

The chapter stresses the importance of modular design and how/why to apply it.

**Modular Design**: The approach of separating the software into reasonably sized modules so that developers only need to face a small fraction of the overall complexity when making a change, which helps with cognitive load.

We refer to a piece of code as a **module**, which has an *implementation* and an *interface*. The best modules are the ones whose interfaces are much simpler than their implementations, known as deep modules, which means the module encapsulates most of the complexity inside, and the user does not have to know the details to utilize it. 

This concept is directly related to the term **abstraction**, meaning "a simplified view of an entity, which omits unimportant details". Modules provide an abstraction in the form of their interfaces, which helps us simplify complex problems and have a clearer mental model, when it's not overdone.

**Key Takeaway:** We should avoid creating shallow modules. Instead, we should create deeper modules, encapsulate the complexity and provide a much simpler interface for the sake of better abstraction. This leads us to ease of use, lower cognitive load, fewer unknown unknowns.

---

### Chapter 5 - Information Hiding (and Leakage)

---

### Chapter 6 - General-Purpose Modules are Deeper

---

### Chapter 7 - Different Layer, Different Abstraction

---

### Chapter 8 - Pull Complexity Downwards

---
