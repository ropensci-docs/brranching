# Changelog

## brranching 0.7.1

- adding new maintainer info
  [\#47](https://github.com/ropensci/brranching/issues/47)
- Updating CI Rcmd checks with package `usethis`

## brranching 0.7.0

CRAN release: 2021-05-11

#### MINOR IMPROVEMENTS

- vignettes fix
  ([\#45](https://github.com/ropensci/brranching/issues/45))

## brranching 0.6.0

CRAN release: 2020-06-12

#### MINOR IMPROVEMENTS

- the APG dataset in `taxize` package was updated in taxize `v0.9.97` -
  changes made to comply with the changes in the APG dataset structure
  ([\#41](https://github.com/ropensci/brranching/issues/41))

## brranching 0.5.0

CRAN release: 2019-07-27

#### MINOR IMPROVEMENTS

- now using package `conditionz` in the
  [`phylomatic_names()`](https://docs.ropensci.org/brranching/reference/phylomatic_names.md)
  function for handling messages from the `taxize` package about the
  user not having an API key set
  ([\#36](https://github.com/ropensci/brranching/issues/36))
  ([\#40](https://github.com/ropensci/brranching/issues/40))

#### BUG FIXES

- require newest `phylocomr` version that has fixes for various
  mis-behavior
  ([\#38](https://github.com/ropensci/brranching/issues/38))
  ([\#39](https://github.com/ropensci/brranching/issues/39))

## brranching 0.4.0

CRAN release: 2018-12-05

#### NEW FEATURES

- in the
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md)
  function now using
  [`phylocomr::ph_phylomatic`](https://docs.ropensci.org/phylocomr/reference/ph_phylomatic.html)
  instead of shelling out to Phylocom via `system`. A number of
  parameters are gone due to the change internally
  ([\#30](https://github.com/ropensci/brranching/issues/30))
  ([\#35](https://github.com/ropensci/brranching/issues/35))
- in the
  [`rbladj()`](https://docs.ropensci.org/brranching/reference/rbladj.md)
  function now using
  [`phylocomr::ph_bladj`](https://docs.ropensci.org/phylocomr/reference/ph_bladj.html)
  instead of shelling out to Phylocom via `system`
  ([\#30](https://github.com/ropensci/brranching/issues/30))
  ([\#35](https://github.com/ropensci/brranching/issues/35))
- added a package vignette
  ([\#31](https://github.com/ropensci/brranching/issues/31))
  ([\#34](https://github.com/ropensci/brranching/issues/34)) thanks
  [@fozy81](https://github.com/fozy81)
- added new dataset of four phylogenetic trees that can be used in
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md),
  see
  [`?phylomatic_trees`](https://docs.ropensci.org/brranching/reference/phylomatic_trees.md)

#### MINOR IMPROVEMENTS

- added docs to
  [`phylomatic_names()`](https://docs.ropensci.org/brranching/reference/phylomatic_names.md)
  and the README on using NCBI Entrez API keys

## brranching 0.3.0

CRAN release: 2018-06-19

#### NEW FEATURES

- gains new function `bladj`
  ([\#18](https://github.com/ropensci/brranching/issues/18))
- replaced `httr` with `crul` for http requests
  ([\#25](https://github.com/ropensci/brranching/issues/25))

#### MINOR IMPROVEMENTS

- fix links to readme images
  ([\#29](https://github.com/ropensci/brranching/issues/29))
  ([\#26](https://github.com/ropensci/brranching/issues/26))
- `verbose` param in
  [`phylomatic()`](https://docs.ropensci.org/brranching/reference/phylomatic.md)
  function changed to `mssgs`

## brranching 0.2.0

CRAN release: 2016-04-14

#### NEW FEATURES

- Added function
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md)
  to use Phylomatic locally. Phylomatic is a set of Awk scripts, which
  have to be downloaded by the user. After downloading, this function
  uses the local version of Phylomatic (Same as that that runs as a web
  service). This is advantageous especially when dealing with large
  queries. ([\#13](https://github.com/ropensci/brranching/issues/13))

#### MINOR IMPROVEMENTS

- Fixed `clean` parameter in
  [`phylomatic()`](https://docs.ropensci.org/brranching/reference/phylomatic.md)
  and
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md)
  to expect a logical (`TRUE` or `FALSE`) instead of a “true” or
  “false”. ([\#15](https://github.com/ropensci/brranching/issues/15))
- A related change to that above, changed reading newick strings to use
  [`phytools::read.newick()`](https://rdrr.io/pkg/phytools/man/read.newick.html)
  instead of
  [`ape::read.tree()`](https://rdrr.io/pkg/ape/man/read.tree.html),
  which handles the result of `clean=FALSE` in
  [`phylomatic()`](https://docs.ropensci.org/brranching/reference/phylomatic.md)
  and
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md)
  ([\#16](https://github.com/ropensci/brranching/issues/16))
- Documented that in the `storedtree` parameter of
  [`phylomatic()`](https://docs.ropensci.org/brranching/reference/phylomatic.md)
  and
  [`phylomatic_local()`](https://docs.ropensci.org/brranching/reference/phylomatic_local.md)
  the tree from Zanne et al. is also available by using
  `storedtree="zanne2014"`
  ([\#19](https://github.com/ropensci/brranching/issues/19))

## brranching 0.1.0

CRAN release: 2015-11-12

#### NEW FEATURES

- Released to CRAN.
