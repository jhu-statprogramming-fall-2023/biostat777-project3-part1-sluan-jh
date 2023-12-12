# reshape2

<!-- badges: start -->
[![R build status](https://github.com/hadley/reshape/workflows/R-CMD-check/badge.svg)](https://github.com/hadley/reshape/actions)
[![Codecov test coverage](https://codecov.io/gh/hadley/reshape/branch/master/graph/badge.svg)](https://codecov.io/gh/hadley/reshape?branch=master)
<!-- badges: end -->

## Assignment Info

Link to original github repo of the `reshape2` package: https://github.com/hadley/reshape/

Link to deployed website: https://jhu-statprogramming-fall-2023.github.io/biostat777-project3-part1-sluan-jh/

Website customizations:

1. Changed website theme to flatly

2. Changed code chunk theme to breeze-light

3. Changed code background to color `#404040`

4. Changed base font to 'Inter'

5. Added footnote to the end

6. Rearranged navigation bar order

## Status

[![Lifecycle: superseded](https://img.shields.io/badge/lifecycle-superseded-blue.svg)](https://lifecycle.r-lib.org/articles/stages.html#superseded)

reshape2 is superseded: only changes necessary to keep it on CRAN will be made. We recommend using [tidyr](http://tidyr.tidyverse.org/) instead.

## Introduction

Reshape2 is a reboot of the reshape package. It's been over five years since the first release of reshape, and in that time I've learned a tremendous amount about R programming, and how to work with data in R. Reshape2 uses that knowledge to make a new package for reshaping data that is much more focused and much much faster.

This version improves speed at the cost of functionality, so I have renamed it to `reshape2` to avoid causing problems for existing users.  Based on user feedback I may reintroduce some of these features.

What's new in `reshape2`:

 * considerably faster and more memory efficient thanks to a much better
   underlying algorithm that uses the power and speed of subsetting to the
   fullest extent, in most cases only making a single copy of the data.

 * cast is replaced by two functions depending on the output type: `dcast`
   produces data frames, and `acast` produces matrices/arrays.

 * multidimensional margins are now possible: `grand_row` and `grand_col` have
   been dropped: now the name of the margin refers to the variable that has
   its value set to (all).

 * some features have been removed such as the `|` cast operator, and the
   ability to return multiple values from an aggregation function. I'm
   reasonably sure both these operations are better performed by plyr.

 * a new cast syntax which allows you to reshape based on functions
   of variables (based on the same underlying syntax as plyr):

 * better development practices like namespaces and tests.

 * the function `melt` now names the columns of its returned data frame `Var1`, `Var2`, ..., `VarN`  instead of `X1`, `X2`, ..., `XN`.

 * the argument `variable.name` of `melt` replaces the old argument `variable_name`.

Initial benchmarking has shown `melt` to be up to 10x faster, pure reshaping `cast` up to 100x faster, and aggregating `cast()` up to 10x faster.

This work has been generously supported by BD (Becton Dickinson).
