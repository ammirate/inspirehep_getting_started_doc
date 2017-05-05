=======
Testing
=======


Not so much to say here, just one thing: Testing is not an activity to ensure that your code works fine. Your code must already work fine. The goal of testing is FIND bugs!
If you don't find any bug during the testing process, it has failed. 
On the other hand, a testing process that pulls up bugs, is a successiful activity.

************
Unit Testing
************


Formally called *functional testing*, this kind of work ensure that your code does exactly what you think it does.
**Scope**: each function in a module or a class has to be tested to verify its logical and functional correctness.

Let's say we want to test a function that sums two integers.

::

    def sum(int_a, int_b):
        return int_a + int_b


To write functional testing, you must think at the code as code written by somebody else. The only thing you know is the function's signature. You should just give some parameters in input and expecting a result. This is what is called Black Box Testing.

::
    
    def test_sum():
        expected = 4
        result = sum(1, 3)
        assert result == expected


Don't worry, I am not going to explain the above test. But I can suggest you to focus also on the structure `expected-result-assertion`, which makes a test very readable and clear.


Test writing process
====================
What I suggest to do when you approach to write a unit test module is:

1. Define dependencies among your functions.
2. Test first functions without dependencies.
3. Then, test the other functions
    a. using the already-tested functions (now you trust them!) **or** 
    b. mocking your functions.

In same cases, you should use both strategies to successfully find bugs in the code. 

Classicist Vs Mock Testing
=====================================
- # TO-DO


Testing open source code
========================
Since you are working on an open source project (even if you are not) you must adopt also a **white-box** testing approach.
Using a White-box approach means that your tests relies on the fact that you know your code, how it is made (how many `if` branches, `for` loop, ecc. it has).
 
So, beside giving some values in input and assert if they correspond to what you expected,
you should write tests able to cover all (or at least almost all) your code branches.

**Best practices**

`if` statement: write code that makes the `if` becoming `True` and `False`, so both blocks of code will be tested.
`for` statements: write code that:

1. don't satisfy the `for` test (e.g. iterating on empty list)
2. cycles just once
3. cycles more than once

**managing files and paths**

Pytest provides an already-made **fixture** returning a temporary path were you can write, read and do all the path operations you want.

Pytest
======

fixtures
--------

how to
^^^^^^

Once per test
^^^^^^^^^^^^^
Once per module
^^^^^^^^^^^^^^^
Sharing fixtures
^^^^^^^^^^^^^^^^
Once you have a fixture returning, let's say, a `FooBar` object instance, you may need it in several tests, testing different modules. In this case, you can put your nice fixture in a separate file and use it without rewriting its code in multiple tests.

A common and high maintainable way to do this is giving a look to the official page: https://docs.pytest.org/en/latest/fixture.html


*******************
Integration Testing
*******************
**TO DO :) **


**************
Practical Tips
**************
Here are some tips for ``py.test`` and in general, ``inspire-next`` newcomers:

- | Running **specific** test methods with py.test

  | For testing a specific function, e.g. ``new_ticket_context``, ``py.test``
  | will detect all related tests which follow the expression ``my_function_name`` and run them.
  
  ::
    
    # When using Docker
    dco run --rm web py.test tests/unit -k new_ticket_context

    # Otherwise
    py.test tests/unit -k new_ticket_context

  
  | More on `selecting tests <https://docs.pytest.org/en/latest/usage.html#specifying-tests-selecting-tests>`_ in ``py.test`` testing framework.

- | *[Dockerl related]* Running specific kind of tests (*i.e. unit/integration/acceptance*) with the option to load a debugger on failure

  | Open a shell (``bash``) into the container whose tests you need to run. 
  | If for example, you need to run ``acceptance`` tests, then:

  ::

    docker-compose -f docker-compose.test.yml run --rm acceptance bash

  From the container shell, you can run:

  ::

    py.test --driver Remote --host selenium --port 4444 --capability browserName firefox --html=selenium-report.html tests/acceptance

  | (To find the ``py.test`` invocation that is being used for each type of tests: ``grep acceptance docker-compose.tests.yml``.)
 
  | To have the option of opening a debugger (e.g. ipdb) on error (or if you've set a trace point), then add ``--ipdb``, as an option in ``py.test`` invocation, like so:

  ::

    py.test --ipdb --driver Remote --host selenium --port 4444 --capability browserName firefox --html=selenium-report.html tests/acceptance


