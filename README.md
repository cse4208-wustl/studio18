# Studio 18

## Generic Algorithms

In this studio, you will see how different kinds of iterators (including plain-old pointers) can be used with different algorithms from the C++ standard library, and how callable types can be used to extend the behaviors of some of those algorithms further. Those features in turn depend significantly on details of C++ templates, traits, and other advanced generic programming topics that we have considered in recent lectures and studios.

## Collaboration

You are encouraged to work in groups of 2 or 3 people (groups may change from studio to studio), though you may also complete this studio individually.

## Exercises

Record your answers in `ANSWERS.md` as you work. Include the names of everyone who worked on the studio in your first answer, and number your responses so they are easy to match to the exercises.

1. List the names of the people who worked together on this studio.

2. SSH into `shell.cec.wustl.edu` using your WUSTL Key credentials, then use `qlogin` to connect to one of the Linux Lab machines and confirm that the version of `g++` there is correct, as you did in [Studio 0](https://github.com/cse4208-wustl/studio0).

   Clone your `studio18` repo using SSH:

   ```bash
   git clone git@github.com:cse4208-wustl/studio18.git
   cd studio18
   ```

   The repo already includes a `Makefile` that builds an executable named `studio18` from `studio18.cpp`. As you work on this studio, update the `Makefile` so it lists all of the source and header files you develop.

   Add a new source file, `studio18.cpp`, and in it define a `main` function that declares a (plain-old C-style) array of integers, initialized with an odd number of unsorted values in which at least a few of the values appear more than once, for example:

   ```cpp
   int arr[] = {-2, 19, 80, -47, 80, 80, -2, 19, 19};
   ```

   Declare pointer variables that are initialized to point to the first element in the array and just past the end of the array, respectively. Then use the `copy` algorithm to print out the contents of the array by passing it those pointers and a variable of type `ostream_iterator<int>` that is initialized with `cout` and a string like `" "` to print between each of the integer values in the array.

   Compile and run your program. In your answers, show the code you wrote and the output your program produced.

3. In your `main` function, declare a container variable of type `vector<int>` and an iterator variable of type `back_insert_iterator<vector<int>>`. Pass the pointers from the previous exercise and that iterator into a call to the `copy` algorithm so that it copies the contents of the array into the vector. Then use other appropriate iterators to print out the contents of the vector to the standard output stream (again with spaces between the elements, as in the previous exercise).

   Compile and run your program. In your answers, show the code you wrote for this exercise and the output produced by that code.

4. Use the `sort` algorithm to sort the integers in your array into non-decreasing order (smallest to largest), and then again use the `copy` algorithm to print out the contents of the sorted array.

   Compile and run your program. In your answers, show the code you wrote for this exercise and the output produced by the code you added.

5. Use the `adjacent_find` algorithm to locate and print out each range of repeated elements in the sorted array from the previous exercise on a separate line. For the example array above, the output would be:

   ```text
   -2 -2
   19 19 19
   80 80 80
   ```

   Compile and run your program. In your answers, show the code you wrote for this exercise and the output produced by the code you added.

6. Sort the contents of the vector into non-increasing order (largest to smallest) by passing an object of type `greater<int>` as a third argument to the `sort` algorithm, and then again use the `copy` algorithm to print out the contents of the sorted vector.

   Compile and run your program. In your answers, show the code you wrote for this exercise and the output produced by the code you added.

7. Use the `count` and `accumulate` algorithms to compute the median (middle value), mean (average), and mode (most frequent value) of the integers in the sorted vector from the previous exercise.

   **Hints:**

   - With an odd number of elements, the median is easy to calculate using iterator arithmetic.
   - To avoid round-off errors when calculating the mean, use a `float` initialized with the result of the `accumulate` algorithm.
   - One way to calculate the mode is to iterate through one of the sorted containers, and each time a new value is found, call the `count` algorithm on the remaining sorted range to see how many of that value there are, and then skip over that many repeated elements (using iterator arithmetic).

   Compile and run your program. In your answers, show the code you wrote for this exercise and the output produced by the code you added.

## Deliverables

Commit and push all modified and added files, including `ANSWERS.md`, to the repo.
