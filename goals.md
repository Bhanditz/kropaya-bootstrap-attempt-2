##Goals for the language and environment.

Generalised places.

First class labels + polymorphic row types.

Explicit quantification - exists, forall, mu, maybe nu, fresh, maybe lambda?

Linear variables and becoming types.

Polarised types - positive and negative positions.

Algebraic effects + capabilities.

A staged computation story that works without needing separate compilation or files. Some kind of notion of 'chunks' or partial evaluation fragments for the read-eval cycle, so that the reader can be modified even with the execution model that has no notion of source files.

Patterns and sections.

##A fantasy language, unhindered by reality.

Ur-Principle: Like Atomish, but starting from first class labels and row polymorphism instead of starting from message sends to activatable cells.

Does this even make sense? I am not yet sure.

##The Principles

- First class labels and row polymorphic types.
- Reified Readers, Evallers, Printers, Universes, Runloops, and Mirrors.
- Parameterised modules a la Functors, with explicit support for mutual recusion. This allows, amongst other things, really good tree shaking and permgen trimming, as well as elegantly solving the conflicting dependencies problem.
- Generation of statically and dynamically linked binaries.
- Something like a logical extension of functional core/imperative shell.
- Use of staged computation, metaprogramming, generic programming, and tree rewriting for optimisation.
- No C or C++ anywhere (except as needed for platform/library linkage eg for Open GL support).
- Type-directed metaprogramming.
- Locatives, multiple typing.
- Explicit, extensive use of quantification.
- Both parametric (ie 'Theorems for Free') and non-parametric code, with clear edges to prevent breaking invariants.
- Swapping out the reader mid read/the evaller mid eval.
- A continuum of compile-type to run-time, rather than a binary.

Bibliography/Inspirations/Influences

(TODO: Expand this out way more fully)

Current inspirations:

MetaOCaml/BER. Haskell. ISWIM.

Language-Oriented programming inspired by OMeta and the STEPS VPRI project, as well as Kuro/Shiro.

Staged computation inspired by the Shonan Challenge, and especially the papers http://okmij.org/ftp/meta-programming/HPC.html.

Type polarity, and some of the approach to pattern matching were inspired by Levy and Levy#.

Past inspirations:

Inspired by Cola/Pepsi/Idst/Maru, Ioke, Common Lisp and Haskell.

Other influences: Perl 5&6 (Guts on the outside, TMTWTDI, Moose, 6Model), Io (Mirrors), OCaml (module system), Potion.

Minor influences: Atomy, Atomo, Slate, Erlang, Snobol, MetaLua.

A small (in size, scope, and memory footprint), reasonably fast language for writing self contained executables.

Ur-Principle: separating and reifying readers, evallers, printers, runloops, universes, and mirrors.
Goals

Able to compile programs as statically linked executables. Able to compile programs as dynamically linked executables. Able to compile to llvm IL, and then do a final compile and link on a target system.

Able to only pay for what you use, a la the ideal of C++. Several methods to achieve this:

    A sane, parametric module system, so you do not end up with a giant permgen, and you can specialise sanely.
    A metasyntactic evaluator, so you can swap the reader and evaluator functions in and out.
    An MMOP that lets you 'trim' the environment for subexpressions, to make late binding dynamic dispatch faster.
    Use of rewriting macros rather than pragmas for optimisation - ie ua{z+x*y} -> a function that uses raw arithmetic on raw numbers rather than symbolic arithmetic on bignums
    Eventually, the use of twine, ropes and so forth for string manipulation, without needing cumbersome builders.
    Compiled functions with holes for fast templates.

No C or C++ anywhere (except in llvm, the rt_* libraries...)

Good enough FFI by way of bridges, alien cells, and alien evaluators.

This is all supposed to be a replacement for the places I use Ioke, but need something faster with a smaller memory footprint, like as a web app on a small VPS.

Inspired by Cola/Pepsi/Idst/Maru, Ioke, Common Lisp and Haskell.

Other influences: Perl 5&6 (Guts on the outside, TMTWTDI, Moose, 6Model), Io (Mirrors), OCaml (module system), Potion.

Minor influences: Atomy, Atomo, Slate, Erlang, Snobol, MetaLua.
