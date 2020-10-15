# Numpy

## Introduction

The following is a list of short problems you can use to practice your numpy programming.  Some of them we made up, and some of them come from the following large list (\*):

[100 Numpy Exercises](http://www.labri.fr/perso/nrougier/teaching/numpy.100/)

You should solve these without using loops, you should be using the functions or methods in numpy itself. If done
correctly, most of these functions will be a single line and most will be very short.
You may have to look up some numpy methods we didn't cover in class to solve some of the exercises.  If you ever find yourself thinking

> I wonder if there's just a function in `numpy` that does <thing>

there is a pretty good chance the answer is "yes".  Don't hesitate to explore the numpy documentation and stack-overflow; this is a very important part a building your knowledge base as a python user.

## Basic
### Part 1

1. Write a function that creates a **column vector** (an array of shape (n, 1)) containing the sequence of numbers 0, 1, 2, ..., n-1:

    ```
    column_vector(3)
        => [[0], [1], [2]]
    ```

1. Write a function that creates an array of random floating point numbers between zero and one of a given shape. Do not assume that the shape will 
be a 2D array; your function should work for any shape. Your function should return something like:

    ```
    random_array((4, 3))
        => array([
            [ 0.30159734,  0.46366088,  0.78706666],
            [ 0.26946135,  0.80638833,  0.25265662],
            [ 0.82426648,  0.46202413,  0.20735323],
            [ 0.19923862,  0.4677537 ,  0.60799465]])
    ```

    ```
    random_array((2,2,2,2)) 
        => array([
            [[[0.6840515 , 0.9126597 ],
            [0.41925388, 0.88833245]],

            [[0.42349186, 0.65294607],
            [0.31532532, 0.64656652]]],

            [[[0.50583897, 0.56033669],
            [0.50719292, 0.30445478]],

            [[0.94537857, 0.31618756],
            [0.21473817, 0.7942768 ]]]])
    ```


1.  Given an integer numpy array of 0's and 1's, write a function that creates a new array where 0's are replaced with the word `"red"` and 1's are replaced with the word `"blue"`.

    ```
    x = np.array([0, 0, 1, 0, 1]) 
    color_replace(x)
        => np.array(["red", "red", "blue", "red", "blue"])
    ```


1. Given two equal length arrays, `x` with some general numeric data, and `b` an array of booleans, write a function that computes the sum of the data in `x` at the same positions where `b` is True, and the sum of the values in `x` at the positions where `b` is false.

    ```
    x = np.array([0,    1,    2,     3,    4,     5])
    b = np.array([True, True, False, True, False, False])
    compute_true_false_sums(x, b)
        => {True: 4, False: 11}
    ```

1. Write a function that selects from one of two arrays based on the value in another boolean array.

    ```
    x = np.array([1,    2,    3,     4,    5,     6])
    y = np.array([10,   20,   30,    40,   50,    60])
    b = np.array([True, True, False, True, False, True])
    select_from_two_arrays(x, y, b):
        => np.array([1, 2, 30, 4, 50, 6])
    ```

1. Write a function that compute the sum of squared differences between two arrays:
    
    ```
    x = np.array([0, 1, 0, 1, 0, 1])
    y = np.array([0, 1, 2, 3, 4, 5])
    sum_of_squared_differences(x, y)
        => 40
    ```

## Advanced
### Part 2

1. Write a function that consumes a two-dimensional numpy array (so, a matrix), and a label which is either "row" or "column".  The function should return a one-dimensional numpy array (vector) with either the row or column averages.

    ```
    X = np.array([[0, 1], [2, 1]])
    row_or_column_means(X, label="row")
        => np.array([0.5, 1.5])
    row_or_column_means(X, label="column")
        => np.array([1.0, 1.0])
    ```


1. Write a function that creates a square two-dimensional array of zeros, but with ones on the diagonals immediately below and above the main diagonal.  For example, when `n=5`, you should create the following two-dimensional array

    ```
    ones_above_and_below_diagonal(5)
        => np.array([
      [0, 1, 0, 0, 0],
      [1, 0, 1, 0, 0],
      [0, 1, 0, 1, 0],
      [0, 0, 1, 0, 1],
      [0, 0, 0, 1, 0]
    ])
    ```


1.  Write a function that creates a square two-dimensional array with a checkerboard pattern of 0's and 1's of any given size.

    ```
    checkerboard(5)
        => np.array([
      [1, 0, 1, 0, 1],
      [0, 1, 0, 1, 0],
      [1, 0, 1, 0, 1],
      [0, 1, 0, 1, 0],
      [1, 0, 1, 0, 1],
    ])
    ```

1. Write a function that creates a square two-dimensional array with ones around the border, and zeros in the interior.


    ```
    ones_border(5)
        => array([
      [1, 1, 1, 1, 1],
      [1, 0, 0, 0, 1],
      [1, 0, 0, 0, 1],
      [1, 0, 0, 0, 1],
      [1, 1, 1, 1, 1]
    ])
    ```

1.  Given a two-dimensional array `M`, create a new two-dimensional array containing only the *columns* of `M` where at least one of the entries is negative.

    ```python
    M = np.array([[ 0.5,  0.2, -0.3,  0. ],
                  [ 0.4,  0.3,  0.3,  0.4],
                  [-0.2, -0.4,  0.1,  0.4]])
    select_negative_columns(M)
    >>> array([[ 0.5,  0.2, -0.3],
               [ 0.4,  0.3,  0.3],
               [-0.2, -0.4,  0.1]])
    ```

1. Given an array and a number, find the index of the number in the array that is closest to the number.

    ```
    x = np.random.randint(100, size=10)
    x
        => array([89, 55, 76,  4, 12, 86, 18, 18, 30, 88])
    get_closest_idx(x, 11)
        => 4
    ```

1. Subtract the row mean from each row of a two-dimensional array (element by element).

    ```
    x = np.array([
        [0, 1, 0, 1],
        [1, 1, 1, 1],
        [1, 2, 3, 4]])
    subtract_row_means(x)
        => np.array([
      [-0.5,  0.5, -0.5,  0.5],
      [ 0. ,  0. ,  0. ,  0. ],
      [-1.5, -0.5,  0.5,  1.5]])
   ```

## Extra Credit
### Part 3

1.  Write a function that converts an  array of shape `(n, 2)` representing Cartesian coordinates of `n` points into a new `(n, 2)` array containing the polar coordinates of those points.

    ```
    x = np.array([[0, 1], [1, 0], [1, 1]])
    cartesian_to_polar(x)
        => np.array([1, np.pi / 2], [1, 0], [np.sqrt(2), np.pi / 4])
    ```

1.  Given an array `x`, and a two-dimensional array `M` with the same number of columns as the length of `x`, find the row in `M` that makes the smallest angle with `x`.

    ```python
    x = np.array([-0.2,  0.4,  0.4,  0.7])
    M = np.array([[ 0.8, -0.8,  0.1,  0.1],
               [ 0.1, -0. , -0.2, -0.8],
               [-0.3, -0.8, -0.1,  0.2],
               [ 0.5, -0.5,  0.4,  0.3],
               [ 0.5, -0. ,  0.5, -0.4]])
    smallest_angle(x, M)
    >>> array([ 0.5, -0.5,  0.4,  0.3])
    ```

Do additional problems from [100 Numpy Exercises](http://www.labri.fr/perso/nrougier/teaching/numpy.100/)

(\*) There is also a work in progress version of this for Pandas, if you are interested in that:

[100 Pandas Exercises](https://github.com/ajcr/100-pandas-puzzles)
