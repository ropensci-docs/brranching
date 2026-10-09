# Query Phylomatic for a phylogenetic tree.

Query Phylomatic for a phylogenetic tree.

## Usage

``` r
phylomatic(
  taxa,
  taxnames = TRUE,
  get = "GET",
  informat = "newick",
  method = "phylomatic",
  storedtree = "R20120829",
  treeuri = NULL,
  taxaformat = "slashpath",
  outformat = "newick",
  clean = TRUE,
  db = "apg",
  mssgs = TRUE,
  ...
)
```

## Arguments

- taxa:

  Phylomatic format input of taxa names.

- taxnames:

  If `TRUE` (default), we get the family names for you to attach to your
  species names to send to Phylomatic API. If `FALSE`, you have to
  provide the strings in the right format.

- get:

  'GET' (default) or 'POST' format for submission to the website.

- informat:

  One of newick (default), nexml, or cdaordf. If using a stored tree,
  informat should always be newick.

- method:

  One of phylomatic (default) or convert

- storedtree:

  One of R20120829 (Phylomatic tree R20120829 for plants), smith2011
  (Smith 2011, plants), binindaemonds2007 (Bininda-Emonds 2007,
  mammals), or zanne2014 (Zanne et al. 2014, plants). Default: R20120829

- treeuri:

  URL for a phylogenetic tree in newick format.

- taxaformat:

  Only option is slashpath for now. Leave as is.

- outformat:

  One of newick, nexml, or fyt.

- clean:

  Return a clean tree or not. Default: `TRUE`

- db:

  One of "ncbi", "itis", or "apg". Default: apg

- mssgs:

  Print messages. Default: `TRUE`

- ...:

  curl options passed on to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

Newick formatted tree as `phylo` object or nexml character string

## Details

Use the web interface at <http://phylodiversity.net/phylomatic/>

If you set `taxnames = FALSE`, you need to pass in a character vector,
with each element like this example:
`"asteraceae/taraxacum/taraxacum_officinale"`, of the form
`"family/genus/genus_specfic epithet"`

## Examples

``` r
if (FALSE) { # \dontrun{
# Input taxonomic names
taxa <- c("Poa annua", "Phlox diffusa", "Helianthus annuus")
tree <- phylomatic(taxa=taxa, get = 'POST')
plot(tree, no.margin=TRUE)

# Genus names
taxa <- c("Poa", "Phlox", "Helianthus")
tree <- phylomatic(taxa=taxa, storedtree='R20120829', get='POST')
plot(tree, no.margin=TRUE)

# Lots of names
taxa <- c("Poa annua", "Collomia grandiflora", "Lilium lankongense", "Phlox diffusa",
"Iteadaphne caudata", "Gagea sarmentosa", "Helianthus annuus")
tree <- phylomatic(taxa=taxa, get = 'POST')
plot(tree, no.margin=TRUE)

# Don't clean - clean=TRUE is default
(tree <- phylomatic(taxa=taxa, clean = FALSE))
## with clean=FALSE, you can get non-splitting nodes, which you
## need to collpase before plotting
library('ape')
plot(collapse.singles(tree), no.margin=TRUE)

# Output NeXML format
taxa <- c("Gonocarpus leptothecus", "Gonocarpus leptothecus", "Lilium lankongense")
out <- phylomatic(taxa=taxa, get = 'POST', outformat = "nexml")
cat(out)

# Lots of names, note that when you have enough names (number depends on length of individual
# names, so there's no per se rule), you will get an error when using `get='GET'`,
# when that happens use `get='POST'`
library("taxize")
spp <- names_list("species", 500)
# phylomatic(taxa = spp, get = "GET")
(out <- phylomatic(taxa = spp, get = "POST", db = "itis"))
plot(out)
} # }
```
