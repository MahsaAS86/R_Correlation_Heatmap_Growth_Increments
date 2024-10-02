# R_Correlation_Heatmap_Growth_Increments
R code for making a heat map correlation for visualizing data 
#code for correlation
#heatmap

#Source: http://www.sthda.com/english/wiki/correlation-matrix-a-quick-start-guide-to-analyze-format-and-visualize-a-correlation-matrix-using-r-software

#Modern_samples

library(corrplot)
library(reshape2)
library(ggplot2)
library("Hmisc")
download.packages("Hmisc")


res = cor(Correlation_remove_NA, use = "complete.obs")
round(res, 2)

res2 <- rcorr(as.matrix(Correlation_remove_NA))

res2
res2$r
res2$P

-------------------------------
  flattenCorrMatrix <- function(cormat, pmat) {
    ut <- upper.tri(cormat)
    data.frame(
      row = rownames(cormat)[row(cormat)[ut]],
      column = rownames(cormat)[col(cormat)[ut]],
      cor  =(cormat)[ut],
      p = pmat[ut]
    )
  }


res2 <- rcorr(as.matrix(Correlation_remove_NA[,1:5]))

flattenCorrMatrix(res2$r, res2$P)
-----------------------------------

library(corrplot)

corrplot(res, type = "upper", order = "hclust", 
         tl.col = "black", tl.srt = 45)

---------------------------------

corrplot(res2$r, type="upper", order="hclust", 
           p.mat = res2$P, sig.level = 0.01, insig = "blank")


corrplot(res2$r, type="upper", order="hclust", 
         p.mat = res2$P, sig.level = 0.01, insig = "blank")  
  
---------------------------------

library(xlsx)
write.xlsx(flattenCorrMatrix(res2$r, res2$P), file = "C:/Users/malidoostsal/OneDrive - The University of Melbourne/Desktop")


------------------------------------

#Archaeologicla samples


library(corrplot)http://127.0.0.1:24093/graphics/plot_zoom_png?width=1280&height=658

library(reshape2)
library(ggplot2)
library("Hmisc")
download.packages("Hmisc")


res = cor(XU10_4_data_R, use = "complete.obs")


res2 <- rcorr(as.matrix(XU10_4_data_R))

res2

res2$r
res2$P

-------------------------------
  flattenCorrMatrix <- function(cormat, pmat) {
    ut <- upper.tri(cormat)
    data.frame(
      row = rownames(cormat)[row(cormat)[ut]],
      column = rownames(cormat)[col(cormat)[ut]],
      cor  =(cormat)[ut],
      p = pmat[ut]
    )
  }


res2 <- rcorr(as.matrix(XU10_4_data_R[,1:4]))

flattenCorrMatrix(res2$r, res2$P)
-----------------------------------
  
  library(corrplot)

corrplot(res, type = "upper", order = "hclust", 
         tl.col = "black", tl.srt = 45)

---------------------------------
  
  corrplot(res2$r, type="upper", order="hclust", 
           p.mat = res2$P, sig.level = 0.01, insig = "blank")


corrplot(res2$r, type="upper", order="hclust", 
         p.mat = res2$P, sig.level = 0.01, insig = "blank")  

---------------------------------
  
library(xlsx)
write.xlsx(flattenCorrMatrix(res2$r, res2$P), file = "C:/Users/malidoostsal/OneDrive - The University of Melbourne/Desktop")



