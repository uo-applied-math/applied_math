---
layout: page
title: syllabus // computation and combinatorics
description: Syllabus for Computation and Combinatorics
---

See [the schedule](fall_schedule.html) for topics by week
and links to the homework.




## Topics 

First part of the class: combinatorial enumeration, iteration; standard combinatorial objects, combinatorics of 2D stat mech models.

- partitions, posets, trees, graphs, etc
- dimer model, spanning tree, nonintersecting lattice path, ising model.
- standard algorithms for working with these objects.
- generating functions and combinatorial statistics

Second part of the class: discrete probability, random sampling and random generation from these models.
- markov chains, markov growth rules.

Throughout the class: computation and computer algebra.
- basics of writing python covered by "language immersion"
- effective computation; code optimization, profiling.
- Refactoring code, object-oriented programming, test driven development

# Course Goals

By end of class, students should be able to:
- write code to generate large random combinatorial objects of the above types
- prove theoretical results about these objects
- fluently write scientific code
- develop conjectures and proofs with the help of computational experiment

## Prerequisites:

Experience with programming similar to an undergraduate course (preferably in python). Familiarity with probability, random variables, and linear algebra at an undergraduate level.


## Course structure

Three hours of lecture (including computer demonstration and chalkboard exposition).


## Homework and assessment

I will assign roughly 8 weekly homeworks - to be due all weeks except Week 1 (the first week of term) and Week 6 (midterm week).  Assignments are due in Canvas on Tuesdays, at 11:59pm.  There's a late penalty of 10 percent per day, so please submit on time.  I'll drop the lowest assignment grade. 
 
These assignments will consist of a mix of theoretical problems and computational exercises.  Homework will be turned in as jupyter notebooks, allowing integration of programming, simulation results, and LaTeX into a single document.

## Grading 

Mathematics graduate classes now have 2 separate "heavy load" and "light load" grading schemes.  This is to allow Ph.D. students (who have significant other responsibilities) to continue to take classes throughout their program. 

- Heavy load grading scheme
	- 25% midterm, 50% final exam, 25% homework
	- Tests are pen-and-paper, no computer (I'll ask about math and pseudocode)
- Light load grading scheme
	- 100% homework, scaled so that a grade of B+ corresponds to getting passing grade on about half the assignments.
	- If you have an alternative suggestion for how you would like to be evaluated (e.g. a relevant research project) let me know

Whether you are taking the "light load" or "heavy load" version of this class largely depends on your status in the program.

- Math undergrads and pre-Ph.D. students: **heavy load** grading scheme.
- Math Ph.D. students: **light load** grading scheme.
- Students from other departments: **heavy load** grading scheme.

If you feel that an exception to the above should be made, please discuss with me and with your advisor.  

## Software

We will use python for this class.

To install python, together with everything you need for this class, I suggest installing [miniconda](https://www.anaconda.com/download). Miniconda is a python distribution that is commonly used in data science and scientific computing.  We will need the following packages:

- jupyter 
- numpy
- sympy
- matplotlib

In my own work, I also use [Sage](https://sagemath.org), a computer algebra system based on python.  Sage can also be installed through miniconda, and indeed this is probably the easiest way to install sage at the moment.  However, for continuity with future classes in the applied math sequence, I'm going to try not to use Sage.


## Books

We will not follow a single text, but students who would like additional reading might find these useful:
    
* Bollobas, *Modern Graph Theory* nicely covers the graph theory topics we will cover (and more).
* Richard Stanley, *Enumerative Combinatorics* is the standard reference.
* Donald E. Knuth, *The Art of Computer Programming Vol. 4a* is a great text on combinatorial algorithms.

## Inclusion and accessibility

We take seriously our responsibility to create inclusive learning environments.
Please notify us if there are aspects of the instruction or design of this
course that result in barriers to your participation! You are also encouraged
to contact the Accessible Education Center in 164 Oregon Hall at 541-346-1155
or uoaec@uoregon.edu.



