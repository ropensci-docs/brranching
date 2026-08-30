# Phylomatic names

Get family names to make Phylomatic input object, and output input
string to Phylomatic for use in the function phylomatic

## Usage

``` r
phylomatic_names(taxa, format = "isubmit", db = "ncbi", ...)
```

## Arguments

- taxa:

  quoted tsn number (taxonomic serial number)

- format:

  output format, isubmit (you can paste in to the Phylomatic website),
  or 'rsubmit' to use in fxn phylomatic_tree

- db:

  One of "ncbi", "itis", or "apg". if you use "apg", no HTTP requests
  are made (no internet connection needed), whereas if you use "ncbi" or
  "itis" you do need an internet connection. IMPORTANT: see
  **Authentication** below if using "ncbi".

- ...:

  curl options passed on to
  [`taxize::tax_name()`](https://docs.ropensci.org/taxize/reference/tax_name.html)

## Value

string (e.g., "pinaceae/pinus/pinus_contorta"), in Phylomatic submission
format

## Authentication

NCBI Entrez doesn't require that you use an API key, but you get higher
rate limit with a key, from 3 to 10 requests per second, so do get one.
Run
[`taxize::use_entrez()`](https://docs.ropensci.org/taxize/reference/key_helpers.html)
or see
https://ncbiinsights.ncbi.nlm.nih.gov/2017/11/02/new-api-keys-for-the-e-utilities/
for instructions.

NCBI API key handling logic is done inside of the `taxize` package, used
inside this function.

Save your API key with the name `ENTREZ_KEY` as an R option in your
`.Rprofile` file, or as environment variables in either your `.Renviron`
file or `.bash_profile` file, or `.zshrc` file (if you use oh-my-zsh) or
similar. See [Startup](https://rdrr.io/r/base/Startup.html) for help on
R options and environment variables. You cannot pass in your API key in
this function.

Remember to restart your R session (and to start a new shell window/tab
if you're using the shell) to take advantage of the new R options or
environment variables.

We strongly recommend using environment variables over R options.

Note that if you don't have an ENTREZ_KEY set, you'll get a message
about it, but only once during each function call. That is, there can be
of these messages per R session, across function calls.

## Examples

``` r
if (FALSE) { # \dontrun{
mynames <- c("Poa annua", "Salix goodingii", "Helianthus annuus")
phylomatic_names(taxa = mynames, format='rsubmit')
phylomatic_names(mynames, format='rsubmit', db="apg")
phylomatic_names(mynames, format='isubmit', db="ncbi")
phylomatic_names(mynames, format='isubmit', db="apg")
} # }
```
