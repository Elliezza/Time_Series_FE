# Time Series Feature Extraction for Federated Learning
This repo details the dataset used in the demonstration for time series features in federated learning. We consider a vertical federated learning system, where the initiator holds the data label, and the collaborator holds additional features.

## Data Set

The data set used in this demonstrarion is a real-world data set collected with in a e-commerce platform, with the purpose to predict the purchasing itention of high potential users. The details of the dataset are described here [[1]](#1) and [here](DATASET.md).

## Feature Extraction

We adopt our in-house feature engineering tools [[2]](#2)[[3]](#3) on the production AutoML platform HyperCycleML [[4]](#4) to perform feature extraction. The configuration of the original dataset is described in [config.json](dataset/config.json). The detailed operations on the featues are summarized in [feql.script](dataset/feql.script). The operations are described in Feature Enginnering QL (FEQL), an in-house feature descitptive language.

## Feature Division across Federated Parties

The extracted features byt the aforementioned feature engineering tools are logically divided into three sets:

- Static features: original features and non-time-related extracted features.
- Time series set A: time series features generated with time windows constructed from user action logs.
- Time series set B: time series features with time windows constructed from user product interaction logs.

This division is for the purpose of evaluating the model accuracy with or without time series features. Note because the original dataset is not for federated learning, this division is done by different ways to construct time windows to simulate such scenarios. The detail features of each feature set is shown in the table.

| Group               | Feature Names                                                |
| ------------------- | ------------------------------------------------------------ |
| Static features     | f_flattenRequest_bo_product_a1_direct_7, f_flattenRequest_bo_product_a2_direct_8, f_flattenRequest_bo_product_a3_direct_9, f_flattenRequest_bo_product_br_direct_10, f_flattenRequest_bo_product_cate_direct_11, f_flattenRequest_bo_user_age_direct_13, f_flattenRequest_bo_user_sex_direct_15, f_flattenRequest_bo_user_user_lv_cd_direct_16, f_original_pair_id_2, f_original_sku_id_3, f_combine_34_27, f_combine_35_29, f_combine_36_31, f_combine_37_34 |
| Time series group A | f_flattenRequest_bo_action_br_top3frequency_18, f_flattenRequest_bo_action_cate_top3frequency_19, f_flattenRequest_bo_action_model_id_top3frequency_20, f_flattenRequest_bo_action_type_top3frequency_21, f_flattenRequest_bo_action_model_id_distinct_count_24, f_flattenRequest_bo_action_model_id_distinct_count_25, f_flattenRequest_bo_action_type_distinct_count_26 |
| Time series group B | f_flattenRequest_window_unique_count_pair_id_30, f_flattenRequest_window_top1_ratio_pair_id_31, f_flattenRequest_window_top1_ratio_pair_id_32, f_flattenRequest_window_unique_count_pair_id_33, f_flattenRequest_window_count_pair_id_43, f_flattenRequest_window_count_pair_id_44 |
| Time series group C | f_flattenRequest_bo_comment_bad_comment_rate_avg_5,f_flattenRequest_bo_comment_bad_comment_rate_avg_6,f_flattenRequest_bo_comment_bad_comment_rate_min_17,f_flattenRequest_bo_comment_comment_num_distinct_count_27,f_flattenRequest_bo_comment_comment_num_distinct_count_28,f_flattenRequest_bo_comment_has_bad_comment_distinct_count_29 |
## Federated Training Settings

There are three training settings in this demonstration.

- Baseline: only static features are used
-  Setting A: time series feature group A is included on the initiator, representing a scenario for non-federated time series features at a single party
-  Setting B: time series feature group B is further included on the collaborator, representing a scenario for federated time series extraction on both participating parties. 

The actual data used in the training experiements can be found at [dataset](dataset/). The training data is saved in compressed form.

## References

<a id="1">[1]</a> JD Data Set.  https://jdata.jd.com/html/detail.html?id=1.

<a id="2">[2]</a> OpenMLDB.  2021. An  Open  Source  Database  for  Ma-chine  Learning  Systems.https://github.com/4paradigm/OpenMLDB.

<a id="3">[3]</a> Chen, C.; Yang, J.; Lu, M.; Wang, T.; Zheng, Z.; Chen, Y.;Dai, W.; He, B.; Wong, W.-F.; Wu, G.; Zhao, Y.; and Rudoff,A. 2021.  Optimizing In-Memory Database Engine for AI-Powered on-Line Decision Augmentation Using PersistentMemory.Proc. VLDB Endow., 14(5): 799–812.

<a id="4">[4]</a>  HyperCycleML.  2021.   An  Automated  Machine  LearningPlatform. https://en.4paradigm.com/product/hypercycleml.html
