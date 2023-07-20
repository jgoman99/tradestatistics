
<!-- README.md is generated from README.Rmd. Please edit that file -->
<p>
<a href="https://www.digitalocean.com/">
<img src="https://opensource.nyc3.cdn.digitaloceanspaces.com/attribution/assets/PoweredByDO/DO_Powered_by_Badge_blue.svg" width="201px">
</a>
</p>


# Note (From John) 
This is my attempt to fix some bugs in the original package as well as add some QoL improvements. I have not forked packages before, so please pardon any lack of etiquette/let me know how to improve.

### Bugs

It looks like under group name match (gnm), commodity should be section.
```
Error in tradestatistics::ots_commodity_code(group = commodities_wm[x]) : 
  unused argument (group = commodities_wm[x])
```

This led to another error in ots_strings_processing where it looks as though lookup for sections has not been implemented. I added a simple implementation in line with the commodities Code

This led to a final NA error, which I opted to remove before data construction. Fix below
```
commodities = commodities[!is.na(commodities)]
```


# Open Trade Statistics package <img src="svg/hexicon.svg" width=150 align="right" alt="sticker"/>

[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![Lifecycle:
stable](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://www.tidyverse.org/lifecycle/#stable)
[![R build
status](https://github.com/ropensci/tradestatistics/workflows/R-CMD-check/badge.svg)](https://github.com/ropensci/tradestatistics/actions?workflow=R-CMD-check)
[![CRAN
status](https://www.r-pkg.org/badges/version/tradestatistics)](https://cran.r-project.org/package=tradestatistics)
[![Coverage
status](https://codecov.io/gh/ropensci/tradestatistics/branch/master/graph/badge.svg)](https://codecov.io/github/ropensci/tradestatistics?branch=master)
[![](https://badges.ropensci.org/274_status.svg)](https://github.com/ropensci/onboarding/issues/274)

[Open Trade Statistics](https://tradestatistics.io) is an effort to open
international trade data. `tradestatistics` provides an easy way to
obtain data from OTS by accessing its API.

This is what the package does:

![Data diagram](svg/data-diagram.svg)

Using `tradestatistics` package is all about efficiency, without this
package you could obtain the same data from the API at the expense of
using additional time and effort for the same results. As an API wrapper
and utility program this package makes data obtaining faster and easier
for you.

## Installation

``` r
# Install stable version from CRAN
install.packages("tradestatistics")

# Install stable version from GitHub
devtools::install_github("ropensci/tradestatistics")
```

## Code of conduct

Please note that this project is released with a [Contributor Code of
Conduct](https://docs.ropensci.org/tradestatistics/CODE_OF_CONDUCT.html).
By participating in this project you agree to abide by its terms.

[![ropensci\_footer](https://ropensci.org/public_images/ropensci_footer.png)](https://ropensci.org)

