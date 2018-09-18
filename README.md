# Python Ranges

Inspired by DLang's ranges. The inspiration is that I'm dissapointed by python's
current approach to iteration and functional programming.

# Installation

    git clone https://github.com/AODQ/python-drange.git
    cd python-drange
    sudo pip install .

# Features

    Static Typing with 'Any' and Variant option
    Memory pool with proper slices [Slices do not copy unless modified]
    Many different range types:
        Input, Forward, Bidirectional, Random Access
        Output, Assignable, Infinite
    Introspection functions (Is_input, Is_infinite, etc)
    "UFCS"-optional chaining functions [upper-case = supported]:
        Map, Filter, Reduce, Chain, Enumerate, Drop, Dropback, Cycle, Iota, Chunks,
        Choose, Zip, Stride, Tee, Take, Array, and Retro
    To change size, just write to a range's length
    + to concatenate, == for equality

# Examples

    assert(Iota(1, 11).Reduce(lambda x, y: x-y) == -53)
    assert(Iota(1, 11).Array().Retro().Reduce(lambda x, y: x-y) == -44)
  
    class FibonacciRange:
      Empty = InfiniteEmpty()
      def __init__(s, l=1, r=0): (s.l, s.r) = (l, r)
      def Front(s):
        (s.l, s.r) = (s.l+s.r, s.l)
         return s.r
      Save = lambda s: FibonacciRange(s.l, s.r)
  
    fib = FibonacciRange();
    assert(Take(fib, 10).Reduce(lambda x, y: x+y) == 143);


Check out drange_test.py for more, which includes unit tests

Restrictions;

    Python lists, maps, dicts, etc are not allowed in a range
