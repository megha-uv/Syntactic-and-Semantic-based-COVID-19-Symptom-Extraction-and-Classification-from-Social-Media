# Syntactic-and-Semantic-based-COVID-19-Symptom-Extraction-and-Classification-from-Social-Media

During COVID-19 Pandemic the social media was a medium of communication to share the experiences,symptoms,remedies for COVID-19.This work aims to extract COVID-19 related posts from Reddit Platform and perform severity classification of COVID-19 for the social media user based on the severity of the symptoms extracted from the posts.

To extract the COVID-19 Symptom words a deep language model was developed using 2 unqiue architectures namely BERT and MLP.The concept of Named Entity Recognition is used to identify the symptom words using the BIOE tags.

B-> Beginning of Symptom <br />
I-> Intermediate words of Symptom <br />
O-> Non-Symptom Words <br />
E-> End of Symptom Words <br />

The deep language model is trained using clinical text.The clinical text is a text recorded by doctors to report about the personal details of the patient, the symptoms experienced by them,the medications provided to them and other lab results.Both BERT and MLP genrates BIOE tags for each word of the input symptom mentioned text and their outputs are combined using an integration algorithm.In a similar procedure the Social Media posts are passed into the model.

Based on the tags the symptom words are extracted and a new dataset is created by labelling the sociial media data with the severity based on the severity of the symptom specified in the CDC(Centre for Disease and Control:https://www.cdc.gov/coronavirus/2019-ncov/symptoms-testing/symptoms.html).
<br />
Example: *Symptom extracted:Shortness of Breath  Severity:Severe <br />
          Symptom extracted:Fever                Severity:Non-Severe <br />

With this severity labelled dataset the machine learning classifiers namely:Decision Tree Classifier,Ada Boost Classifier,SVM,Gradient Boost Classifier.Accurate severity classification was obtained.


Dataset Description:

Clinical text dataset : https://github.com/AmirYasseen/Clinical-Textual-Datasets-Of-Coronavirus/blob/main/DS1-IRAQ-Clinical%20Text%20COVID-19.xlsx <br />

Reddit Posts dataset : 




         

