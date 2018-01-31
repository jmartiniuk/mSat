# Microsatellite formatting Readme
Jay Martiniuk  
June 11, 2016  

## Microsatellite data formatting and analysis

### Naming conventions

**S. cerevisiae winery and vineyard isolates have two names:** 
- `plateId`: a short, unique name used in sample submission to NAPS and in processing in GeneMapper.
- `isolateId`: a much longer unique, descriptive name for use in R analysis

***Other experiments can follow this convention optionally.

- `plateId` contains the plate catalog number and cell (e.g. P01A01). Format: PxxYzz, where xx is the two digit plate number, Y is the uppercase plate row, and zz is the two digit column number.
- `isolateId` contains at minimum: vintage(4 digits),vineyard,fermRep_isolateNo(two digits). **eg: 2016TII05_33**

The `isolateId` and `plateId` can be made in Excel.

In general, any time a single digit (e.g. 1-9) is included in a sample name, it must be preceded by a 0 to ensure the samples order correctly.

Other conventions:
**Don't use any special characters in sample names.
**Avoid hyphens.
**design file column names, if more than one word, should be  written in camelCase (lowercase first word, uppercase second word), e.g. mlgId, isolateNo



### Two file types: data and design

Every project should have two types of files: 
- a data file with `plateId`s and multi-locus genotypes
- a 'design' or metadata file containing the `plateId`, `isolateId` and important information about each sample (e.g. winery, timepoint, replicate, etc.)
- The data file is generated in GeneMapper and modified in Excel depending on what R package it will be used for)
- The design file can be made in Excel. 

####The data file

- The data file should contain, at minimum, the `plateId` and the alleles at each of 11 loci. Each locus will have two columns. Locus order is arbitrary and dictated by GeneMapper. Do not change the locus order for any downstream applications.

- The data file must be 'cleaned up' in Excel or OpenOffice after export from GeneMapper.

Example files
- pre-cleaning: [gm-precleaned.txt](gm_precleaned.txt)

The data file is formatted with each locus having two columns, one per (diploid) allele.The loci alleles are usually listed with the smallest allele first, followed by the second. The loci alleles are labelled 'locus.1', 'locus.2'

Note that locus names beginning with numbers (e.g. 091 and 009) must be entered into `R` as letters ("O" instead of "0") as `R does not accept numbers as the first character in a variable or object.



The design file is a csv titled 'wineryDes' and contains information about the *Saccharomyces* yeast isolate's location, fermentation replicate, fermentation hour isolated, fermentation stage/timepoint, species, etc. This can be made in Excel.
 
 
Columns (in this order): 

plate: "P" followed by two-digit plate number (e.g. P01, P33)
cell:   Row letter followed by two-digit column number (e.g. A02, G12)
plateId: plate + cell (e.g. P01E12)
species: 
- "Su" = *Saccharomyces uvarum*, 
- "Sc" = *Saccharomyces cerevisiae*, 
- "U" = Unknown species
vintage: four-digit vintage year
winery: uppercase two or three-letter code (e.g. LF, SB, TII) 

vineyard: 
- "B" = SBV winery fermentations (2013, 2014, 2015; 700L bins)
- "G" = green block (OCP 2013, reps 16,17,18)
- "HE" = home east block (SBV 2013, 2014, 2015, reps 04, 05, 06 in 2013)
- "HW" = home west block (SBV 2013, 2014, 2015, reps 01, 02, 03 in 2013)
- "OG" = orchard grove block (SBV 2013, 2014, 2015, reps labelled 07, 08, 09 in 2013, 01-05 are without skins in 2015, 06-08 are with skins in 2015)
- "W" = white block (OCP 2013)
- "WIN1,2,3" = OCP Winery fermentations 2014, 2015, inoculated with starter culture (150L) *Note: these are labelled "OCP" in the plate legends*
- "WIN4,5,6" = OCP Winery fermentations 2014, 2015, spontaneous fermentations (150L) *Note: these are labelled "OCP" in the plate legends*
- "Y" = yellow block (OCP 2013, 2014, 2015 - now called "Blue" at OCP)

fermRep: two-digit number
hour: three-digit number (e.g. 010, 334) or brix level
timepoint: "0", "E", "M" or "L", to be determined based on sugar/weight loss
isolate: isolate number from a particular fermentation-timepoint, a two-digit number (usually between 01-48)


##Exporting genotype tables from GeneMapper

*** Make sure no question marks are left in the alleles column under the genotypes tab!
- Make a folder for your project on the Desktop (e.g. for the Okanagan Pinot Noir survey, make a directory called 'okpn')

In GeneMapper,
- Change the table setting from 'S. cerevisiae' to 'MS export.'
- Make sure the 'Samples' tab is selected, then go to 'File -> **Export combined table...**'

- In the opened window, name the document using a descriptive title (plate catalog number, mlgId, etc.) + Dat. The first letter of the name should be lowercase. **examples: p68Dat, dv10Dat**
- Select *'Export File As Tab-delimited text (.txt)'* and *'Merge One line per sample.'* 





