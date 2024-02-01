# Researchers Approach New Speed Limit for Seminal Problem

[Reference from tldr](https://www.quantamagazine.org/researchers-approach-new-speed-limit-for-seminal-problem-20240129/?utm_source=tldrnewsletter)

- “Basically, ILP is the bread and butter of operations research both in theory and practice,” said Santosh Vempala
- Often turn to a variant of linear programming called integer linear programming (ILP).
  - It's popular in applications that involve discrete decisions.
  - Including production planning, airline crew scheduling and vehicle routing.
- Researchers have discovered various algorithms that can solve ILP problems.
  - But they all been relatively slow.
- The best version they could come up with "a kind of speed limit" comes from the trivial case where the problem's variables.
- Unfortunately, once the variables take a value beyond just zero and 1, the algorithm’s runtime grows much longer.
- “This new algorithm is extremely exciting”
  - ILP works by transforming a given problem into a set of linear equations that must satisfy some inequalities.
- ILP geometrically
  - Turn the inequalities at the heart of ILP to a convex shape, such as any regular polygon.
    - This shape represents the constraints of the individual problem you're solving, whether it’s couch production or airline scheduling, so the shape’s interior corresponds to all possible values that could solve the inequalities, and thus the problem.
    - The problem’s dimension influences the dimension of this shape: With two variables it takes the form of a flat polygon; in three dimensions it is a Platonic solid, and so on.
  - Next, imagine all the integers as an infinite set of grid points, known in mathematics as a lattice.
    - A two-dimensional version looks like a sea of dots, and in three dimensions it looks like the points where steel beams in a building connect.
    - The dimension of the lattice also depends on the dimension of a given problem.
