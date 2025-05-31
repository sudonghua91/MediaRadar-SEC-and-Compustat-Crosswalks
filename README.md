# MediaRadar-SEC-and-Compustat-Crosswalks
This crosswalk was derived by setting JW distance ⩽ 1% to keep my sample free from any erroneous matches. This is also a caveat as errors depend on what sample you are using. You will also need to balance the number of matches and the degree of inconsistency. The punch line is that we need to keep firm names matched right.

We follow a few steps working on the proprietary advertising data:

Download advertising data from MediaRadar from 2015-2023. Summarize the total media expense (sum of network television, spot television, cable television networks, syndicated television, Spanish-language network television, local radio, national spot radio, network radio, magazine, Sunday magazine, local magazine, Spanish-language magazine, business publication, newspaper, national newspaper, Spanish-language newspaper, outdoor, and internet display) of top 1000 firms ranked by media dollar from Ad$pender (Kantar Media) for 2009-2014. Download SEC-CIK-GVKEY link from WRDS.

Fuzzy match between MediaRadar's firm names and SEC's firm names using the R codes.
We do this for each year. Generate "match1_year.dta" - "match14_year.dta" due to the limitation of R's memory size and then append for each year in Stata. (See
Stata codes)

In R, we need to merge original data with clean names for each year for both MediaRadar (with ad info) and SEC (with GVKEY).

Drop name duplicates for each year. Duplicates are sometimes due to subsidiaries of a parent. We sum ad expenses for each GVKEY considering only parent firms.

Merge original MediaRadar and SEC filings to the matched names.

Go to fill these values into the missing values in Compustat. Drop those observations not included in Compustat.

Reference:

Seo, T. (2025). Two Persistent Trees: Advertising and the Cross Section of Equity Returns.
Liang C. Advertising rivalry and discretionary disclosure[J]. Journal of Accounting and Economics, 2024, 77(1): 101611.
