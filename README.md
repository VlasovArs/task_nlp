# task_nlp
test_task_in_the_Contour_nlp

# Introduction
In the Circuit, we work a lot with documents: arbitration claims, public procurement, enforcement proceedings. In this task, we suggest that you make a model that will help the public procurement department extract
the necessary piece of text from the document in order to form an application form. Exactly which text fragment needs to be extracted depends on the questionnaire item corresponding to the document.
In total, in each document with which you will work, there is 1 of 2 points of the questionnaire for which it is necessary to extract pieces from the text:
- contract enforcement
- provision of warranty obligations

Accordingly, your model, taking as input `the text of the document` and `the name of one of the two items`, should return `the corresponding piece of text from the text of the document`.

# Data

### train.json 
The training data in json format has the following fields:
- `id': int - id of the document
- `text`: str - the text of the document, which may contain a fragment of text corresponding to the questionnaire item from the `label` field
- `label': str - the name of the questionnaire item. It can take one of two meanings: `securing the performance of the contract` or `securing warranty obligations`
- "extracted_part": dict of the following format:

   {
"text": [text fragment from the "text" field corresponding to the questionnaire item],
"answer_start": [index of the beginning symbol of the text fragment in the document text],
"answer_end": [index of the end character of a text fragment in the document text]
   } 
  
  
### test.json

To demonstrate the operation of the model, use the data from the 'test' file.json`. It has all the same fields as in the 'train' file.json`, except for the `extracted_part` field - that's what you will need to add,
so that we can evaluate the quality of your model.

# Test task

To complete the test task, it is required to develop a model that will be able to extract the desired text fragment from the document text using a pair of `document text` and `questionnaire item`. 
After training the model, add `test' to the file.json`field `extracted_part` in the same format as in the 'train' file.json`. Name the new file `predictions.json`

**Hint**: After examining the data, you may notice that part of the observations does not have a text fragment to extract (an empty line inside the `extracted_part` field with `answer_start` and
`answer_end` equal to zero). This means that the text of the document does not contain the necessary text fragment corresponding to the questionnaire item. Take this into account when training your model and when forming
a file with answers.

# Evaluation criteria
1. To evaluate the final solution, the `Accuracy` metric will be used: the proportion of observations in which the text fragment extracted by the model fully corresponds to the actual
   the required fragment.
2. The purity of the code, design and clarity of the study.

# Solution Requirements
As a solution, we expect a zip archive with all *.py and *.ipynb files in the solution folder and the 'predictions' file.json` in the root. Format of the zip archive name: LastName_FirstName.zip (example Ivanov_Ivan.zip ).
The file `predictions.json` should include columns `id`, `text`, `label` containing the same data as the original 'test' file.json`, as well as the `extracted_part` column in the same
format as in the 'train' file.json`
Marking up a test dataset and including it in training/validation is prohibited.

The solution folder should contain the study and all the code needed to reproduce the study.

Good luck!
