# demo
## 2021-09-27 homework-1
### 解释1.gtf文件中第4、5列代表什么，exon长度应该是$5-$4+1还是$5-$4?
- 第4、5列代表基因或转录本在参考序列上的起始和终止的位置， exon的长度应该是$5-$4+1.

### 列出1.gtf文件中 XI 号染色体上的后 10 个 CDS （按照每个CDS终止位置的基因组坐标进行sort）。
- cat 1.gtf | awk '$1 == "XI"{ print $1, $3, $4, $5 }' | grep 'CDS'|tail
- cat 1.gtf |grep 'CDS'| awk '$1 == "XI"{ print() }' | tail

### 统计 IV 号染色体上各类 feature （1.gtf文件的第3列，有些注释文件中还应同时考虑第2列） 的数目，并按升序排列。
- grep -v '^#' 1.gtf | awk '$1 == "IV" && $2 =="ensembl" { print $3}'|sort |uniq -c|sort -k 1
