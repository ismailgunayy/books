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

The chapter discusses the information hiding technique for creating deep modules.

**What is information hiding?**

Information hiding can be described as encapsulating any piece of knowledge in a module. It's one of the best ways of reducing complexity, in 2 ways:
- It simplifies the interface of a module, by hiding the exposed design decisions or implementation details that don't bring any value to the user. Hence, lower _cognitive load_ for the user of the module.
- Hiding a piece of information means there are no _dependencies_ on that information, which makes our module easier to maintain. If we want to make a change in the implementation, which we'll most likely do, the user doesn't have to know about this change. Hence, less _change amplification_.

**Anti-Patterns**
- Information Leakage: The opposite of information hiding. It occurs when design decisions are exposed through the interface of a module, or they are reflected in multiple modules, transitively. It creates a _dependency_ between modules which results in bigger _change amplification_ and higher _cognitive load_.
- Temporal Decomposition: Structure of the system reflecting the order in which operations occur instead of focusing on what common knowledge the modules have. Also results in information leakage. If you have multiple modules sharing the same piece of knowledge in the different parts of the execution order, they might be better merged to create a deeper module.

When should we expose the knowledge?
- If a piece of knowledge is really required for the user of the module, for the system to function properly, then we must not hide the information.

**Key Takeaway:** We should hide as much information as possible to create deeper modules to prevent/reduce complexity.

---

### Chapter 6 - General-Purpose Modules are Deeper

The chapter discusses the benefits of generality such as the code being simpler, cleaner and easier to understand and problems of specialization.

- Generality helps with addressing a broad range of problems, not only today's needs but also possible future needs. It matches the _Strategic Programming_ mindset, which recommends that we continually invest in good design. However, when it's too general, it can even fail to solve the particular problem you have today.
- Specialization helps with addressing your current problem, and the code can always be refactored when additional uses are discovered. It's consistent with the common incremental approach in software development. On the other hand, when it's too specialized, it may require too much effort to make changes when it needs to be updated for additional needs.

**Make modules somewhat general-purpose**

The sweet spot is to implement modules somewhat general-purpose, which can be decided by looking at the simplicity of the interface and the functionality of the module. The module's functionality must be special enough to address your needs, but its interface should not reflect those needs while being simple enough to use for today's needs.

**Questions to ask yourself**
- What is the simplest interface that will cover all my current needs?
  - If you manage to reduce the number of methods in the interface without trimming the functionality, and without introducing many more arguments which in fact are not helping with the simplicity, then you're probably creating more general-purpose methods.
- In how many situations will this method be used?
  - If a method exists for one particular case, that is a red flag. Either it should be merged into another general-purpose method, if possible, or several special-purpose methods should be replaced with fewer general-purpose methods.
- Is this API easy to use for my current needs?
  - If you end up writing a lot of additional code to utilize a class for your current needs, then you've probably made the module too general-purpose.
 
**Key Takeaway:** It's never possible to fully eliminate special cases and make everything general-purpose as much as possible. The goal should be having a *somewhat* general-purpose module that's still covering the current needs without any additional complexity.

---

### Chapter 7 - Different Layer, Different Abstraction

---

### Chapter 8 - Pull Complexity Downwards

---
