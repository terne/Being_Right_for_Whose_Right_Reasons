# Being Right for Whose Right Reasons


## Abstract
Explainability methods are used to benchmark the extent to which model predictions align with human rationales
i.e., are 'right for the right reasons'. Previous work has failed to 
acknowledge, however, that what counts as a rationale is sometimes subjective. This paper presents what we think is a first of its kind, a collection of human rationale annotations augmented with the annotators demographic information. 
We cover three datasets 
spanning sentiment analysis and common-sense reasoning, and 
six demographic groups 
(balanced across age and ethnicity). 
Such data enables us to ask both what demographics our predictions align with and
whose reasoning patterns our models' rationales align with. We find systematic inter-group annotator disagreement 
and show how 16 Transformer-based models 
align better with rationales provided by certain demographic groups: 
We find that models are biased towards aligning best with older and/or white annotators. We zoom in on the effects of model size and model distillation, finding – contrary to our expectations – 
negative correlations between model size and rationale agreement as well as no evidence that either model size or model distillation improves fairness.



## Data and code

You can find the data description and codebook in [data](https://github.com/terne/Being_Right_for_Whose_Right_Reasons/tree/main/data), and the code for reproducing our experiments in [code](https://github.com/terne/Being_Right_for_Whose_Right_Reasons/tree/main/code).

The content in [code](https://github.com/terne/Being_Right_for_Whose_Right_Reasons/tree/main/code) is a `git submodule`. Details on how to integrate our code and data are given in the its [README](https://github.com/lautel/fair-rationales/blob/main/README.md) file.
  

## Citation
If using the code and data in this repository, please cite our
[paper](https://arxiv.org/abs/2306.00639) (to appear in ACL 2023): 
```
@article{Jakobsen2023BeingRF,
  title={Being Right for Whose Right Reasons?},
  author={Terne Sasha Thorn Jakobsen and Laura Cabello and Anders S{\o}gaard},
  journal={ArXiv},
  year={2023},
  volume={abs/2306.00639}
}
```


