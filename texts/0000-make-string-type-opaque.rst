- Feature Name: Make the String Type Opaque
- Start Date: 2018-07-23
- RFC PR: Leave this empty, filled on proposal accept
- Haskell Report Issue: Leave this empty, filled on proposal accept



#######
Summary
#######

The Haskell Language Report defines ``String`` as type synonym of ``[Char]``.
The goal of this proposal is to remove this guarantee and change it to an 
opaque type to leave it implementation-dependent.
Implementations can also choose to use the synonym approach to minimize the 
impact.


##########
Motivation
##########

The ``[Char]`` type has massive overhead, 
which resulted in unnecessary performance loss.
But implementations cannot choose other implementations for ``String`` because
it is mandated the language standard.


###############
Detailed design
###############

1. The language report does not mention that the ``String`` is a synonym again.
2. Add a new predefined module ``Data.String``, 
   which contains nearly all functions in ``Data.List`` but for ``String`` and 
   functions converting from or to ``[Char]``.


#########
Drawbacks
#########

It might break nearly all packages if some implementation decided to use an 
opaque type.


############
Alternatives
############

1. Change the ``String`` to ``Array Int Char``.


####################
Unresolved questions
####################

None yet.
