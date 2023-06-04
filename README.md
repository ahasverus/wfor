
<!-- README.md is generated from README.Rmd. Please edit that file -->

# wfor - The World Flora Online Plant List R Package

<!-- badges: start -->
<!-- badges: end -->

## Purpose

This R package facilitates the reconciliation of multiple data sets
containing plant names to each other via standardised World Flora Online
name IDs. This enables the merging of data based on a global, consensus
taxonomy in a reproducible way. It will also report on provenience of
the name matching process and current taxonomy of the names used in the
analysis for subsequent publication.

## Status

One round of development has created this minimum viable product. It
still needs more work but you are welcome to have a play. We plan to
submit an improved version to CRAN by the end of 2023 In sh’Allah!

## Installation

You can install the development version of wfor from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("rogerhyam/wfor")
```

## Example

This is a basic example which shows you how to solve a common problem:

    library(wfor)

    # auto match the Belgian Magnoliopsida test data
    `mags_example <- wfo_match_df_names(Belgian_Magnoliopsida_sp_ssp_var_2011, name_col="scientific_name", authors_col="authorship", interactive=FALSE)`
    # check how many  have been matched using the [wfo_stat_matches()] function.
    `wfo_stat_matches(mags_example)`
    # do a second pass interactively to resolve unmatched names (or until you get tired)
    `mags_example <- wfo_match_df_names(mags_example, name_col="scientific_name", authors_col="authorship", interactive=TRUE)`
    # do a third pass matching names to the nearest genus
    `mags_example <- wfo_match_df_names(mags_example, name_col="scientific_name", authors_col= "authorship", fallback_to_genus=TRUE)`
