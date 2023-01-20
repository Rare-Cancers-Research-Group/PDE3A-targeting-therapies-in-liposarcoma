## PDE3A targeting therapies in liposarcoma

This is code repository supplement for manuscript Toivanen et. al titled "Therapeutic opportunity of phosphodiesterase 3A modulators in myxoid liposarcoma"

## Project code outline
1. Fetching IST genedata from sqlite version of IST database.<br/>
 A. Fetch consists of expression of all genes across all healthy and malignant tissue samples except ones primarily consisting adipocytes or liposarcomas. Also at least 6 datapoints are required per tissue type to be included.<br/>
 B. Calculation is then made to find top 500 expressed genes per tissue.<br/>
 C. Exclusion list is formed by finding unique gene ids among all per tissue top 500 expressed genes.<br/>

2. Processing Bluebee sequenced bulk-RNAseq liposarcoma samples.<br/>
 A. Basis for analysis here is Quantseq pipeline processed gene level counts per sample.<br/>
 B. Clinical metadata and sample id:s are matched so that we have clinical data for each sample with sequencing data, other samples are excluded.<br/>
 C. Gene annotation is fetched from Ensembl.<br/>
 D. Both gene counts and selected clinical variables are imported into DGElist objects.<br/>
 E. Gene count data is filtered with default EdgeR parameters.<br/>
 F. Additional sample level QC is performed by excluding samples of which median have more than +-10% deviation from median of all sample medians.<br/>
 G. Liposarcoma samples are divided into three groups and DEG test is performed with logic one vs. other two for all three groups by using exactTest from EdgeR.<br/>
 H. DEG results are filtered based on LogFC and PValue, as well as genes in IST defined exclusion list are removed from the results.<br/>
  
 ## Data origins
 A. IST data licensed for Rare Cancers Research Group, University of Helsinki, original database version published "Kilpinen et al. Genome Biology, 2008".<br/>
 B. bulk-RNAseq data results are submitted to [TODO: where and what ID?]<br/>
