# Data formatting Readme
Jay Martiniuk  
June 11, 2016  
### Microsatellite formatting (post-compilation in MsatAllele and allelematch)



There is a data file and design file (metadata) for each winery's isolates. The data file will be a csv named 'wineryDat', and will contain the plate cell as the identifier (plateId) followed by the microsatellite genotype formatted in `MsatAllele` and `allelematch`. 

- All column names should be written in camelCase (lowercase first word, uppercase second word)
- All single digit numbers must be preceded by a "0" (in Excel, it is necessary to change the cell type to "text" before it will allow a zero to be inserted before a number)

The data file is formatted with each locus having two columns, one per (diploid) allele.The loci alleles are usually listed with the smallest allele first, followed by the second (this may require manual switching for some allelematch applications). The loci alleles are labelled 'locus.1', 'locus.2'

Note that locus names beginning with numbers (e.g. 091 and 009) must be entered into `R` as letters ("O" instead of "0") as `R does not accept numbers as the first character in a variable or object.
Data file columns, in this order:


The design file is a csv titled 'wineryDes' and contains information about the *Saccharomyces* yeast isolate's location, fermentation replicate, fermentation hour isolated, fermentation stage/timepoint, species, etc.
 
 
  Columns (in this order): 


Permitted column entries:

plate: "P" followed by two-digit plate number (e.g. P01, P33)
cell:   Row letter followed by two-digit column number (e.g. A02, G12)
plateId: plate + cell (e.g. P01E12)
species: 
- "Su" = *Saccharomyces uvarum*, 
- "Sc" = *Saccharomyces cerevisiae*, 
- "U" = Unknown species
vintage: four-digit vintage year
winery: 
-"OCP" or 
-"SBV" (with new three-character abbrevs to be added for new wineries)
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
isolate: isolate number from a particular fermentation-timepoint, atwo-digit number (usually between 01-32)




