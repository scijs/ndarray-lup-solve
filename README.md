# ndarray-lup-solve

[![Build Status](https://travis-ci.org/scijs/ndarray-lup-solve.svg?branch=master)](https://travis-ci.org/scijs/ndarray-lup-solve) [![npm version](https://badge.fury.io/js/ndarray-lup-solve.svg)](http://badge.fury.io/js/ndarray-lup-solve)  [![Dependency Status](https://david-dm.org/scijs/ndarray-lup-solve.svg)](https://david-dm.org/scijs/ndarray-lup-solve)

Solve ndarray Ax=b via LU factorization with pivoting

## Introduction

Given an LUP factorization, this module solves for x in Ax = b. More precisely, it solves for x in LUx = Pb.

## Example

```javascript
var lup = require('ndarray-lup-factorization'),
    solve = require('ndarray-lup-solve'),
    ndarray = require('ndarray'),
    pool = require('ndarray-pool')

var A = ndarray([2,1,1,0, 4,3,3,1, 8,7,9,5, 6,7,9,8], [4,4])
var b = ndarray([13,38,102,107])

// In-place LUP factorization:
lup(A, A, P)
lupSolve( A, A, P, b)

// b now contains the answer x: [2,5,4,3]
```

## Usage

#### `require('ndarray-lup-solve')( L, U, P, b [, work] )

- `L`: The n x n ndarray lower-triangular portion of the LUP factorization. The diagonal entries are implicitly assumed to be 1.
- `U`: The n x n ndarray upper-triangular portion of the LUP factorization.
- `P`: An `Array` of length n containg the permutation
- `b`: An ndarray of length n containing the righthand side of Ax = b
- `work`: (optional) A vector used to permute the entries. If not provided, it is allocated and released into an `ndarray-scratch` typed vector pool.

Returns `true` on successful completion; `false` otherwise.




## Credits
(c) 2015 Ricky Reusser. MIT License

