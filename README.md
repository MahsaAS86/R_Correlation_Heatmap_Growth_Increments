# R_Correlation_Heatmap_Growth_Increments
R code for making a heat map correlation for visualizing data 
#code for correlation
#heatmap

#Source: http://www.sthda.com/english/wiki/correlation-matrix-a-quick-start-guide-to-analyze-format-and-visualize-a-correlation-matrix-using-r-software

#Modern_samples
# Load necessary libraries
library(corrplot)
library(reshape2)
library(ggplot2)
library("Hmisc")
download.packages("Hmisc")

# Calculate the correlation matrix
res = cor(Correlation_remove_NA, use = "complete.obs")
round(res, 2)

# Perform correlation and get p-values

res2 <- rcorr(as.matrix(Correlation_remove_NA))
res2
res2$r  # Correlation coefficients
res2$P  # P-values

# Function to flatten the correlation matrix

  flattenCorrMatrix <- function(cormat, pmat) {
    ut <- upper.tri(cormat)
    data.frame(
      row = rownames(cormat)[row(cormat)[ut]],
      column = rownames(cormat)[col(cormat)[ut]],
      cor  =(cormat)[ut],
      p = pmat[ut]
    )
  }

# Flatten and display the correlation matrix

res2 <- rcorr(as.matrix(Correlation_remove_NA[,1:5]))

flattenCorrMatrix(res2$r, res2$P)

# Plot the correlation matrix
corrplot(res, type = "upper", order = "hclust", 
         tl.col = "black", tl.srt = 45)

# Plot with significance level
corrplot(res2$r, type="upper", order="hclust", 
           p.mat = res2$P, sig.level = 0.01, insig = "blank")

 # Save the flattened correlation matrix to an Excel file
library(xlsx)
write.xlsx(flattenCorrMatrix(res2$r, res2$P), file = "C:/Users/malidoostsal/OneDrive - The University of Melbourne/Desktop")


------------------------------------

#Archaeological samples
# Load necessary libraries again (if needed)

library(corrplot)
library(reshape2)
library(ggplot2)
library("Hmisc")
download.packages("Hmisc")

# Calculate the correlation matrix for Archaeological data
res = cor(XU10_4_data_R, use = "complete.obs")

res2 <- rcorr(as.matrix(XU10_4_data_R))

res2

res2$r # Correlation coefficients
res2$P  # P-values

# Function to flatten the correlation matrix
  flattenCorrMatrix <- function(cormat, pmat) {
    ut <- upper.tri(cormat)
    data.frame(
      row = rownames(cormat)[row(cormat)[ut]],
      column = rownames(cormat)[col(cormat)[ut]],
      cor  =(cormat)[ut],
      p = pmat[ut]
    )
  }

# Flatten and display the Archaeological correlation matrix

res2 <- rcorr(as.matrix(XU10_4_data_R[,1:4]))

flattenCorrMatrix(res2$r, res2$P)

# Plot the Archaeological correlation matrix

corrplot(res, type = "upper", order = "hclust", 
         tl.col = "black", tl.srt = 45)

# Plot with significance level for fossil data
  
  corrplot(res2$r, type="upper", order="hclust", 
           p.mat = res2$P, sig.level = 0.01, insig = "blank")


# Save the Archaeological correlation results to an Excel file
  
library(xlsx)
write.xlsx(flattenCorrMatrix(res2$r, res2$P), file = "C:/Users/malidoostsal/OneDrive - The University of Melbourne/Desktop")



