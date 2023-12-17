---
title: "Python"
subtitle: ""
date: 2023-12-01T15:29:29+08:00
lastmod: 2023-12-01T15:29:29+08:00
draft: true

tags: []
categories: []
---
一些python代码的总结

/home/yh/dzx/work/inter_motif_filter/motif_filter.py 


    tomtom_motif = ref_data["Query_consensus"].copy().unique()

    #以Query_consensus列为键，对应的Target_V4_gene列为值，构建字典

    tomtom_dict = defaultdict(set)  # 默认值为 set

    forkey, valueinzip(ref_data["Query_consensus"], ref_data["Target_V4_gene"]):

    tomtom_dict[key].add(value)
