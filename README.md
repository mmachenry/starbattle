Star Battle Solver by Mike MacHenry
----

This is a solver for the Star Battle puzzle that I originally wrote for
MIT Mystery Hunt 2017.

I noticed that a traditional backtracking solver took far too long (more than a
day) to solve a 10x10 Star Battle. I decided to rewrite it using constraint
logic programming on finite domains, or CLP(FD). It now solves the 10x10 in
about a minute and thirty seconds.

TODO
----

* Improve performance of rows constraint by somehow not building up a large
  tree of possible outcomes. A potential algorithm to solve this is mentioned
  in the comments.
  
* Consider parallelizing solution generation. A good strategy for this might
  be to provide an argument to generate that constrians the most significant
  digit in the puzzle generation to be a particular number. It could then be
  run in parallel with each possible argument.

* Check for input validity of the board

* Allow for parameterization of how many stars must be in each region. Some
  variations require 1 per region and have more regions.

* Accept as many rule adjustments as possible on the commandline

Notes
----

To get performance information, you can build with profiling enabled.

    stack build --executable-profiling --library-profiling --ghc-options="-fprof-auto -rtsopts"
    stack exec -- star-battle examples/changing_rooms.csv +RTS -p -RTS
