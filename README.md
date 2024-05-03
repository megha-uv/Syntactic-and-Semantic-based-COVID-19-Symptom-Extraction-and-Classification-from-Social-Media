# Syntactic and Semantic-based COVID-19 Symptom Extraction and Classification from Social Media

During the COVID-19 pandemic, social media became a vital medium for sharing experiences, symptoms, and remedies related to COVID-19. This project aims to extract COVID-19 related posts from the Reddit platform and classify the severity of COVID-19 for social media users based on the severity of symptoms extracted from the posts.

## Methodology

A deep language model was developed using two unique architectures, BERT and MLP. Named Entity Recognition (NER) is employed to identify symptom words using the BIOE tags:

- B: Beginning of Symptom
- I: Intermediate words of Symptom
- O: Non-Symptom Words
- E: End of Symptom Words

2 architectures are utilized because BERT has an advantage of extracting long range symptom words wheras MLP could'nt.The limitations of each model could be overcome by integerating them.

The deep language model is trained using clinical text, which includes personal details of patients, symptoms experienced, medications provided, and other lab results. Both BERT and MLP generate BIOE tags for each word of the input symptom-mentioned text, and their outputs are combined using an integration algorithm. The same procedure is applied to social media posts.

The integeration algorithm is designed such that if both the output tags generated by the model are same its considered as the final tag for the corresponding word.If there's discrepancy in output a priority based comparision of tags is implemented and the high priority tag is assigned as the final tag to the word. The priority for the tags are assigned based on their occurence and importance such that B tag is assigned higher priority because most of COVID-19 symptoms are of single word symptoms,the priority of I and E are set slightly less because only for the long range symptom words the tags are used which is rare, the O tag is set to least priority since it is insignificant.

Based on the final output tags, the symptom words are extracted, and a new dataset is created by labelling the social media data with severity based on the severity of the symptom extracted as specified by the CDC ([Center for Disease Control](https://www.cdc.gov/coronavirus/2019-ncov/symptoms-testing/symptoms.html)).

Example:

- Symptom extracted: Shortness of Breath, Severity: Severe
- Symptom extracted: Fever, Severity: Non-Severe

Machine learning classifiers, including Decision Tree Classifier, Ada Boost Classifier, SVM, and Gradient Boost Classifier, were employed for accurate severity classification.

## Dataset Description

- Clinical text dataset: [Clinical Textual Datasets of Coronavirus](https://github.com/AmirYasseen/Clinical-Textual-Datasets-Of-Coronavirus/blob/main/DS1-IRAQ-Clinical%20Text%20COVID-19.xlsx)
- Reddit Posts dataset: `Dataset/socialmedia.xlsx`
  - This dataset consists of symptom-mentioned social media posts related to COVID-19 collected from Feb 23, 2024, to March 29, 2024.
- Annotated Clinical Text dataset:
  - The clinical text is annotated with B, I, O, E tags for training the models and is split into a ratio of 80:20 into two files.It is passed into BERT and MLP and final output tags are got for each word in symptom mentioned text:
    - Training dataset: `Dataset/final_train.tsv`
    - Testing dataset: `Dataset/final_test.tsv`
- Sample Output files:
  - The `Output files/final_tags.txt` shows the integrated tags output genrated by BERT and MLP for the input clinical text.

## References
- Luo, X., Gandhi, P., Storey, S., & Huang, K. (2022). A Deep Language Model for Symptom  Extraction From Clinical Text and its Application to Extract COVID-19 Symptoms From Social Media. IEEE Journal of Biomedical and Health Informatics, 26(4), 1737–1748

- Amir Yasseen Mahdi And Siti Sophiayati Yuhaniz, “Automatic Diagnosis of COVID-19 Patients from Unstructured Data Based on a Novel Weighting Scheme,” C. Mater. Contin., vol. 74, no. 1, pp. 1375–1392, 2023, doi: 10.32604/cmc.2023.032671.
  






         

