# Use Phylomatic locally - ideal for large queries

Use Phylomatic locally - ideal for large queries

## Usage

``` r
phylomatic_local(
  taxa,
  taxnames = TRUE,
  storedtree = "R20120829",
  db = "apg",
  lowercase = FALSE,
  nodes = FALSE,
  verbose = TRUE
)
```

## Arguments

- taxa:

  (character) Phylomatic format input of taxa names. required

- taxnames:

  If `TRUE` (default), we get the family names for you to attach to your
  species names to send to Phylomatic API. If `FALSE`, you have to
  provide the strings in the right format. See Details.

- storedtree:

  One of R20120829 (Phylomatic tree R20120829 for plants), smith2011
  (Smith 2011, plants), binindaemonds2007 (Bininda-Emonds 2007,
  mammals), or zanne2014 (Zanne et al. 2014, plants). Default: R20120829

- db:

  (character) One of "ncbi", "itis", or "apg". Default: apg

- lowercase:

  (logical) Convert all chars in taxa file to lowercase. Default:
  `FALSE`

- nodes:

  (logical) label all nodes with default names. Default: `FALSE`

- verbose:

  (logical) Print messages. Default: `TRUE`

## Value

Newick formatted tree as `phylo` object

## Details

uses
[`phylocomr::ph_phylomatic()`](https://docs.ropensci.org/phylocomr/reference/ph_phylomatic.html)
under the hood

This function uses Phylomatic via Phylocom using the phylocomr package.
The interface is slightly different from
[`phylomatic()`](https://docs.ropensci.org/brranching/reference/phylomatic.md):
there's no tree by URL available, and some of the parameters are not
included here.

If you set `taxnames = FALSE`, you need to pass in a character vector,
with each element like this example:
`"asteraceae/taraxacum/taraxacum_officinale"`, of the form
`"family/genus/genus_specfic epithet"`

## Examples

``` r
if (FALSE) { # \dontrun{
library('ape')

# Input taxonomic names
taxa <- c("Poa annua", "Phlox diffusa", "Helianthus annuus")
(tree <- phylomatic_local(taxa))
plot(collapse.singles(tree), no.margin=TRUE)

taxa <- c("Poa annua", "Collomia grandiflora", "Lilium lankongense",
"Phlox diffusa", "Iteadaphne caudata", "Gagea sarmentosa",
"Helianthus annuus")
(tree <- phylomatic_local(taxa))
plot(collapse.singles(tree), no.margin=TRUE)

library("taxize")
spp <- names_list("species", 500)
length(spp)
(tree <- phylomatic_local(spp))
} # }
```
