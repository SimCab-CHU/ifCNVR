# ifCNVR
 ifCNV R package
 
 # Installation
 
 To install ifCNVR type:
 
 `
devtools::install_github("https://github.com/SimCab-CHU/ifCNVR",subdir = "ifCNVR")
`

# Example

See the example.R file reproduced below:

```R
library(ifCNVR)

pathToBam <- "/path/to/bam/files/"
pathToBed <- "/path/to/bed/file.bed"
pathToBedtools <- "/path/to/bedtools/"
outputPath <- "/path/to/html/report.html"

# After installing bedtools (https://bedtools.readthedocs.io/en/latest/content/installation.html), 
# type which bedtools in your console to get the pathToBedtools

# Create reads matrix
readsMatrix <- CreateReadsMatrix(pathToBam, pathToBed, pathToBedtools)

# Detect CNV positive samples 
CNVpos <- abSamples(readsMatrix)

# Detect CNV positive targets
CNVtar <- abTargets(readsMatrix, CNVpos)

# Create the results table
resTable <- calculateScore(readsMatrix, CNVpos, CNVtar, thrScore = 7)

# Generate the html report
generateReport(outputFile = outputPath, readsMatrix, resTable, CNVpos)

```




