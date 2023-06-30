# Data

We collected new annotations and rationales for subsets of the datasets CoS-E [[1]](#1), DynaSent [[2]](#2), and SST/Zuco [[3]](#3)[[4]](#4). (See our paper for descriptions of these subsets: https://arxiv.org/abs/2306.00639 .) Annotators were recruited via Prolific and consented to the use of their responses and demographic information for research purposes. The annotation tasks were conducted through Qualtrics surveys. Exports and word documents of the exact surveys can be found in [qualtrics_survey_exports](https://github.com/terne/Being_Right_for_Whose_Right_Reasons/tree/main/data/qualtrics_survey_exports).

The folders *cose*, *dynasent* and *SST* contain the annotations seperated by socio-demographic groups following recruitment criteria. The files herein ending with *_processed.csv* contain the data after exclusions, as described in the paper, and are those used in our testing and analysis and are neccesary for running scripts to reproduce our results. In the *SST* folder, you'll find files ending with *_indexes.csv*: these contain SST-2 indeces for each annotated instance and are used to remove the instances from the train and val set before training models on the SST-2 data.

The folder *all* contains the same data, but here the annotations of all groups are collected in one file for each dataset (before and after exclusions). **If you just want the data, this might be what you want**. These files, unlike the others, contain proxy annotator/participant IDs (i.e. not Prolific IDs, but an integer given instead to be able to distinguish participants).

Every row in the files corresponds to one participant's response to one given text/sentence, herein both the labeling and the rationale marking. Below we describe the data variables in detail.


## Codebook

| Variable | Description |
| --- | --- |
| QID | The ID of the Question (i.e. the annotation element/sentence) in the Qualtrics survey. Every second question asked for the classification and every other asked for the rationale, of the classification, to be marked. These two questions and answers for the same sentence is merged to one row and therefore the QID looks as if every second is skipped. |
| text_id | A numerical ID given to each unique text/sentence for easy sorting before comparing annotations across groups. |
| sentence | The text/sentence that is annotated, in it's original formatting. |
| original_label | The label from the original dataset (Cose/Dynasent/SST). |
| label | The (new) label given by the respective annotator/participant from Prolific. |
| label_index | The numerical format of the (new) label. |
| rationale | The tokens marked as rationales by our annotators. |
| rationale_index | The indeces of the tokens marked as rationales. In the processed files the index start at 0. However in the unprocessed files ("_all.csv", "_before_exclussions.csv") the index starts at 1.|
| age | The reported age of the annotator/participant (i.e. their survey response). This may be different from the age-interval the participant was recruited by (see recruitment_age). |
| ethnicity | The reported ethnicity of the annotator/participant. This may be different from the ethnicity the participant was recruited by (see recruitment_ethnicity). |
| gender | The reported gender of the annotator/participant. |
| english_proficiency | The reported English-speaking ability (proxy for English proficiency) of the annotator/participant. Options were "Not well", "Well" or "Very well". |
| attentioncheck | All participants were given a simple attention check question at the very end of the Qualtrics survey (i.e. after annotation) which was either PASSED or FAILED. Participants who failed the check were still paid for their work, but their response should be excluded from the analysis. |
| originaldata_id | The id given to the text/sentence in the original dataset. In the case of SST data, this refers to ids within the Zuco dataset – a subset of SST which was used in our study.|
| sst2_id | The processed SST annotations contain an extra column with the index of the text in the SST-2 dataset. -1 means that we were unable to match the text to an instance in SST-2 |
| group_id | An id describing the socio-demographic subgroup a participant belongs to and was recruited by. |
| recruitment_ethnicity | The ethnicity specified for the Prolific job to recruit the participant by. Sometimes there is a mismatch between the information Prolific has on participants (which we use for recruitment) and what the participants report when asked again in the survey/task. This seems especially prevalent with some ethnicities, likely because participants may in reality identify with more than one ethnic group. |
| recruitment_age | The age interval specified for the Prolific job to recruit the participant by. A mismatch between this and the participant's reported age, when asked in our survey, may mean a number of things, such as: Prolific's information is wrong or outdated; the participant made a mistake when answering the question; the participant was inattentive. |
| originaldata_split | The set (train, val, test) of which the text/sentence appears in, in the original dataset. Included to make it easier to match the instances to the original datasets. |
| sst2_split | In the case of SST annoations, there is an extra column refering to the set which the instance appears in within SST-2. Some instances a part of the train set and should therefore be removed before training a model on SST-2 and testing on our annotations. |
| rationale_binary | A binary version of the rationales where a token marked as part of the rationale = 1 and tokens not marked = 0. |


## References
<a id="1">[1]</a> 
Nazneen Fatema Rajani, Bryan McCann, Caiming Xiong, and Richard Socher. 2019. Explain Yourself! Leveraging Language Models for Commonsense Reasoning. In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, pages 4932–4942, Florence, Italy. Association for Computational Linguistics.

<a id="2">[2]</a>
Christopher Potts, Zhengxuan Wu, Atticus Geiger, and Douwe Kiela. 2021. DynaSent: A Dynamic Benchmark for Sentiment Analysis. In Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics and the 11th International Joint Conference on Natural Language Processing (Volume 1: Long Papers), pages 2388–2404, Online. Association for Computational Linguistics.

<a id="3">[3]</a>
Richard Socher, Alex Perelygin, Jean Wu, Jason Chuang, Christopher D. Manning, Andrew Ng, and Christopher Potts. 2013. Recursive Deep Models for Semantic Compositionality Over a Sentiment Treebank. In Proceedings of the 2013 Conference on Empirical Methods in Natural Language Processing, pages 1631–1642, Seattle, Washington, USA. Association for Computational Linguistics.

<a id="4">[4]</a>
Nora Hollenstein, Jonathan Rotsztejn, Marius Troendle, Andreas Pedroni, Ce Zhang, and Nicolas Langer. 2018. Zuco, a simultaneous eeg and eye-tracking resource for natural sentence reading. Scientific Data.

