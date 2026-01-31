<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# snanmeanpn

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute the [arithmetic mean][arithmetic-mean] of a one-dimensional single-precision floating-point ndarray, ignoring `NaN` values and using a two-pass error correction algorithm.

<section class="intro">

The [arithmetic mean][arithmetic-mean] is defined as

<!-- <equation class="equation" label="eq:arithmetic_mean" align="center" raw="\mu = \frac{1}{n} \sum_{i=0}^{n-1} x_i" alt="Equation for the arithmetic mean."> -->

```math
\mu = \frac{1}{n} \sum_{i=0}^{n-1} x_i
```

<!-- <div class="equation" align="center" data-raw-text="\mu = \frac{1}{n} \sum_{i=0}^{n-1} x_i" data-equation="eq:arithmetic_mean">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@42d8f64d805113ab899c79c7c39d6c6bac7fe25c/lib/node_modules/@stdlib/stats/base/ndarray/snanmeanpn/docs/img/equation_arithmetic_mean.svg" alt="Equation for the arithmetic mean.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import snanmeanpn from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-base-ndarray-snanmeanpn@esm/index.mjs';
```

#### snanmeanpn( arrays )

Computes the [arithmetic mean][arithmetic-mean] of a one-dimensional single-precision floating-point ndarray, ignoring `NaN` values and using a two-pass error correction algorithm.

```javascript
import Float32Array from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-float32@esm/index.mjs';
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ctor@esm/index.mjs';

var xbuf = new Float32Array( [ 1.0, 3.0, NaN, 2.0 ] );
var x = new ndarray( 'float32', xbuf, [ 4 ], [ 1 ], 0, 'row-major' );

var v = snanmeanpn( [ x ] );
// returns 2.0
```

The function has the following parameters:

-   **arrays**: array-like object containing a one-dimensional input ndarray.

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   If provided an empty one-dimensional ndarray, the function returns `NaN`.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import uniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-uniform@esm/index.mjs';
import filledarrayBy from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-filled-by@esm/index.mjs';
import bernoulli from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-bernoulli@esm/index.mjs';
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-base-ctor@esm/index.mjs';
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import snanmeanpn from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-base-ndarray-snanmeanpn@esm/index.mjs';

function rand() {
    if ( bernoulli( 0.8 ) < 1 ) {
        return NaN;
    }
    return uniform( -50.0, 50.0 );
}

var xbuf = filledarrayBy( 10, 'float32', rand );
var x = new ndarray( 'float32', xbuf, [ xbuf.length ], [ 1 ], 0, 'row-major' );
console.log( ndarray2array( x ) );

var v = snanmeanpn( [ x ] );
console.log( v );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

* * *

<section class="references">

## References

-   Neely, Peter M. 1966. "Comparison of Several Algorithms for Computation of Means, Standard Deviations and Correlation Coefficients." _Communications of the ACM_ 9 (7). Association for Computing Machinery: 496–99. doi:[10.1145/365719.365958][@neely:1966a].
-   Schubert, Erich, and Michael Gertz. 2018. "Numerically Stable Parallel Computation of (Co-)Variance." In _Proceedings of the 30th International Conference on Scientific and Statistical Database Management_. New York, NY, USA: Association for Computing Machinery. doi:[10.1145/3221269.3223036][@schubert:2018a].

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-base-ndarray-snanmeanpn.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-base-ndarray-snanmeanpn

[test-image]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/actions/workflows/test.yml/badge.svg?branch=v0.1.0
[test-url]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/actions/workflows/test.yml?query=branch:v0.1.0

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-base-ndarray-snanmeanpn/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-base-ndarray-snanmeanpn?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-base-ndarray-snanmeanpn.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-base-ndarray-snanmeanpn/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-base-ndarray-snanmeanpn/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-base-ndarray-snanmeanpn/main/LICENSE

[arithmetic-mean]: https://en.wikipedia.org/wiki/Arithmetic_mean

[@neely:1966a]: https://doi.org/10.1145/365719.365958

[@schubert:2018a]: https://doi.org/10.1145/3221269.3223036

</section>

<!-- /.links -->
