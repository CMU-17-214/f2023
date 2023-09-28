# Lab 6: Refactoring and Anti-Patterns

## Introduction 
A lot of the design principles and heuristics we have been encouraging in this class are there to encourage good design *up-front*. But you do not always have control over how a system you are using gets created. 


**Anti-patterns** are common examples of bad design. They tend to come about due to a program’s natural evolution, coupled with poor choices early on, which leads to code that is increasingly *tangled*, badly coupled, low on cohesion, etc. These are often signaled by **code smells** -- heuristic, but not guaranteed indicators of anti-patterns, like overly long methods, or a class that calls a lot of another class’ code (feature envy, signals high coupling).

In this lab, you will become a code-smelling agent who detects  and attempt at refactoring them. 
## Deliverables

- [ ] Identify the anti-pattern associated with Frogger crossing the road and fix it. Use the Appendix for anti-pattern vocabulary!
- [ ] Identify the anti-pattern associated with Frogger records and fix it.
- [ ] Identify at least two issues (no need to name the anti-pattern) associated with the Drawing System, and explain how you would refactor it. No coding required.

## Instructions

### Setup
<u>Fork</u> and clone the repo from [https://github.com/CMU-17-214/f23-lab06](https://github.com/CMU-17-214/f23-lab06.git).

The first two tasks are explicitly referring to Java code (the typescript codebase is also provided, but as longer legacy version from previous semesters). The last task is provided both in Java and Typescript, so feel free to explore the one you are most comfortable with. If you would like additional exercise, feel free to look into the "accounts" folder.

### Task 1
Frogger is trying to cross the road, which she holds as a "Road" object in her fields. The latter holds a boolean array indicating which steps are “occupied”; Frogger is on a specific square (“position”) and provides a move method (either forward or backward).

In the frogger folder, navigate to the Frogger.java and Road.java classes and take a look at the code. What is it doing and what anti-pattern is present? Then try to fix the design by modifying the two classes.

> Hint: 
> + What information should the Frogger hold? Does it do things that appear weird for a Frogger?


### Task 2

Frogger crossed the road and remembered: she was here to *record* her identity status at the Frogger Office. That's why there is a "Records" object in her field. Frogger tries to fill in the fields according to the Record object. But there is simply too many things to fill in--Frogger is annoyed.

Take a look at Records.java and then Frogger.java (again). What anti-pattern is present? Then try to fix the design by modifying the two classes... or, take a look at FroggerID.java. How might you use it for convenience?

### Task 3

Next, let's study the “drawing” system. Open the drawing folder. The system has multiple substantial flaws, some in the same components. Rather than working top-down, trying to retrieve violations of design principles in the code, let’s work bottom up, identifying code smells and anti-patterns, and then strategizing about how to remedy those.

1) Read through every file, making note of anything that stands out. This can be more specific than code smells; think: duplicated code, problematic ‘instanceof’ checking, poor extensibility. While you are reading, try to identify the “control-flow” of this code; who calls whom (e.g.: Shape calls Line), and where would the first user-based call come from? What does the system do?

2) Try to map your concerns to anti-patterns. Is everything that stood out really problematic? Is it all urgently in need of a solution? If not, what would you tackle first? Reason through the design implications of each change. Some will be very minor, some major.

Prepare at least two refactorings.
Is it as seamless as you thought it would be?
Do you prefer the code afterwards?

## Appendix

Below are a few of the many anti-patterns/code smells that people have identified, with a brief explanation and refactoring actions. This is not meant to be a comprehensive list; it includes several common examples. And you don’t need to memorize all of it; instead, try to learn to recognize them through examples like the ones below, and occasionally discover new ones using the resources we pointed to.

1. **Feature envy**: when one class uses a lot of another’s functionality. This strongly indicates that some of the work being done in the former belongs in the latter (information expert).
  - Refactoring: move methods/fields, possibly part or some of them, to the information expert. This might work for inappropriate intimacy (below), but if both classes really need the same fields, create a delegate, used by both instead.
  - Related: **inappropriate intimacy**, where one class relies too much on the implementation details (fields, protected methods) of another

2. **Large (“god”) class**: one class that has many responsibilities (poor cohesion).
  - Refactoring: extract classes to delegate too, sub-class if you need inheritance. Also helps to extract an interface, to identify the important components.
  - Related: **middle man**, where one class only exists to delegate work elsewhere. But note that this smell applies to classes that don’t do any actual work, and can also show up in small classes.

3. **Message chains**: one method makes a series of calls on the return values of another. Think of the CardDeck → FlashCard.getStatus() → CardStatus.getSuccesses example from the midterm.
  - Refactoring: create a delegate method in the intermediate class (e.g. ‘getSuccesses’ on ‘FlashCard’.

4. **Shotgun Surgery**: making any change requires changing a lot of code (bad responsibility assignment).

5. **Long method**: a method does too many things at once.
  - Refactoring: extract any cohesive parts to separate methods.

6. **Long parameter list**: a long list of parameters provided to a method.
  - Refactoring: identify an object that already holds all/most of these parameters, or create a “parameter Object” if not; pass that instead. If this does not apply, identify if any parameters require a method call to compute on the caller’s side; move that method call into the method.

7. **Refused bequest**: two classes are connected through inheritance despite rather limited similarities (excessive coupling).
  - Refactoring: either restructure the hierarchy to a much simpler superclass object (if inheritance is really appropriate to the remainder), or (more commonly) extract a delegate for the shared functionality

