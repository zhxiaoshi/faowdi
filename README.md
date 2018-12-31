### Introduction

This program merges FAOSTAT and WDI data for user-selected items and countries in Stata.  It then (optionally) runs regressions on user-selected variables and compiles all results into a single dataset.

### Instructions

1. Install required Stata packages
2. Populate the /FAO_data and /FAO_data/codes folders with files downloaded from FAOSTAT (see README files in those folders)
3. Set parameters in params.do
4. Run runprog.do
5. Run regs.do (optional)

### Required Stata packages

- touch
- wbopendata
- parmest (only required for regs.do)

### Output

**files/allregs.dta** contains regression results for all countries.  
**files/COUNTRYGROUPCODE/allregs.dta** contains regression results for all countries in COUNTRYGROUP.

**files/reg_COUNTRYCODE.dta** contains regression results for COUNTRYCODE.  
**files/all_COUNTRYCODE.dta** contains merged FAOSTAT and WDI data for COUNTRYCODE.

**files/COUNTRYGROUPCODE/\*.dta** *(same structure as above)*.

Intermediate files:  
**files/fao_COUNTRYCODE.dta** contains user-selected FAOSTAT data for COUNTRYCODE.  
**files/wdi_COUNTRYCODE.dta** contains user-selected WDI data for COUNTRYCODE.

### Folders

The /files folder contains all the data files generated by this program.

The /files/COUNTRYGROUPCODE folders contain the data files generted by this program organized into country groups following FAOSTAT country group definitions from http://www.fao.org/faostat/en/#definitions.

The /FAO_data folder contains data files downloaded from FAOSTAT (see folder README).

The /FAO_data/codes folder contains FAOSTAT definitions (see folder README).

### Notes on country definitions

FAOSTAT country codes have a one-to-one relationship with ISO2 codes, except for the case of Sudan.  In this case, two different FAOSTAT country codes share one ISO2 code (SD): 206 for "Sudan (former)" ending in 2011, and 276 for "Sudan" starting in 2012.

WDI data does not distinguish between former and current Sudan, and has a one-to-one relationship between World Bank country codes and ISO2 codes.  World Bank does, however, seem to define their own ISO2 codes for country groups.  Examples include 8S for South Asia, which is not in the ISO2 list at all, and ZF for Sub-Saharan Africa, which exists in the ISO2 list, but is currently unassigned.
https://www.iso.org/obp/ui/#iso:pub:PUB500001:en

Care must be taken regarding data for China.  FAOSTAT includes data for China, Taiwan, Hong Kong, and Macao, while WDI data does not include Taiwan.  See the following note:
https://datahelpdesk.worldbank.org/knowledgebase/articles/114933-where-are-your-data-on-taiwan

### Related projects

A similar project for R is located here:
https://github.com/mkao006/FAOSTATpackage

### Links

FAOSTAT: http://www.fao.org/faostat

World Development Indicators (WDI): http://datatopics.worldbank.org/world-development-indicators/
