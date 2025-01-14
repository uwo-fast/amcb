# Preamble Thoughts and Motivations

## Computational Engineering in Context

Before jumping into coding, let’s take a step back and think about what we mean when we say computational engineering. A core aspect of a computationally engineered system is the usage of **data-driven design** which in simple terms is writing a set of text-based instructions that describe the object you are attempting to model creation of a valid model set. This requires some kind of **description language** to provide the designer with a set of rules to describe their model. Additionally, there needs to be a **toolchain** that translates these instructions and generates the output model representation. This toolchain takes the code you’ve written in the description language and processes it into a usable form. To do this effectively, we should focus on elements that:

1. Set the core constraints or boundary conditions for the system.
2. Are standardized or fixed components that directly shape the rest of the design.

We can talk more about this another time and its benefits and comparison to classical CAD methods.

## AMBB v2

Let's start by revisitng the AMBB. In this case, the electrical components themselves are the key fixed element. Its dimensions and properties are set, we can’t change them. Instead, our job is to design around it, creating a solution that satisfies these contraints. Starting here gives us a solid foundation to build on and helps ensure the design is both functional and as generic as possible in addressing the problem at hand.

The first AMBB was made in FreeCAD then remade in OpenSCAD for the sake of completeness for the publication. For AMBB v2, we will revisit the original design and continue development in OpenSCAD. However, for future iterations, we should plan to adopt a new toolchain that better supports solid modeling, transitioning away from mesh-based approaches.

### Results

I will add the pics and a short discussion here

## AMCB

Okay now lets broaden the scope of our problem here. AMBB was for a singular component, but let's think bigger—think an entire circuit! As we mentioned before, we want to move away from meshes toward solids, and to do this, we’ll use something like CadQuery (CQ). However, I've opted for build123d, which is a sister project essentially built on the same principles as CQ but offers more flexibility. It utilizes stateful context managers and is built on the OpenCASCADE geometric kernel, making it well-suited for more complex modeling tasks. This gives us access to the full Python ecosystem, allowing for greater integration with other libraries and enhanced customization for circuit-level designs.

### Why solids>meshes?

Solids are better than meshes because they represent continuous volumes, making operations like unions and intersections more reliable. Meshes, like STLs, are harder to work with and don’t support the same level of precision. Solids also offer better interoperability with existing CAD programs, making it easier to modify designs and integrate them into workflows with other tools.
