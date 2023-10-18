---
title: "E-Utilities获取文献"
subtitle: ""
date: 2023-10-16T00:01:14+08:00
lastmod: 2023-10-16T00:01:14+08:00
draft: true

tags: []
categories: ["生物文本挖掘"]
---
## E-utilities

[Entrez Direct :: Anaconda.org](https://anaconda.org/bioconda/entrez-direct)

```shell
conda install entrez-direct
conda activate ***
```

从[网页](https://www.ncbi.nlm.nih.gov/research/coronavirus/docsum?filters=e_condition.LongCovid)上下载相关文献的结果tsv文件格式（search.results.litcovid.tsv） 包含15066篇文献的pmid,tilte,journal信息

忽略上述文件以 # 开头的行，然后输出 pmid 列的数据

```shell
awk -F '\t' '!/^#/ {print $1}' search.results.litcovid.tsv >pmid.txt
```

## efetch

```shell
# efetch_abstract.sh#! /bin/bash
id_list='/home/yh/dzx/work/BioNLP/DataPreprocess/pmid.txt'

# Set the initial counter to 1
counter=1

#读取id时跳过pmid.txt第一行列名
while read line
do
    if [ $line != 'pmid' ]
    then
        echo $line >> /home/yh/dzx/work/BioNLP/DataPreprocess/get_abstract_id.txt
        #暂存单个摘要
        efetch -db pubmed -id $line -format abstract > /home/yh/dzx/work/BioNLP/DataPreprocess/tmp_abstract.txt
        #更改编号
        sed -i "1s/^1\./$counter\./" /home/yh/dzx/work/BioNLP/DataPreprocess/tmp_abstract.txt
        #将摘要追加到abstract.txt
        cat /home/yh/dzx/work/BioNLP/DataPreprocess/tmp_abstract.txt >> /home/yh/dzx/work/BioNLP/DataPreprocess/abstract.txt
        echo >> /home/yh/dzx/work/BioNLP/DataPreprocess/abstract.txt
        counter=$((counter+1))
    fi
    sleep 2
done < $id_list
echo '摘要获取完毕！'
```
