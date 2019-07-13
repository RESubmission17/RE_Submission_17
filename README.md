# Labelled_Forum_Sentences (Artifact RE-2019)
## Contact details

RE Submission ID: 17

## Overview
This repository contains "Artifacts" from our research on software product forums. The research is described in our paper "Can A Conversation Paint A Picture? Mining Requirements In Software Forums", submitted to the Requirements Engineering conference 2019.

The Artifact is the manually labelled, software product forum feedback, created in our research and used as the truth set for RQ2 and RQ3. The feedback is labelled per sentence, with 1 of 18 forum feedback classifications, detailed in our paper. 

## Database file

The labelled sentences are contained in "VLC_labelled_sentences_4RE.sqlite". The database contains three tables: (1) labelled_sentences; (2) verbs; (3) POS.

The "labelled_sentences" table contains the feedback sentences and the manual labels.
Each DB table's contents are described below.

### labelled_sentences

| Column Names  | Description           | 
| ------------- |:-------------:| 
| id     | Links the three DB tables | 
| topic_forum   | The forum/subforum the feedback is from     | 
| post_position | Forum field the feedback is from: title, initial post, reply, etc      | 
| user_level     | User level of the feedback author | 
| sentence   | Feedback sentence      | 
|label | Manually given sentence label      | 

### Verb tags

This table contains the present verb counts for each feedback sentence. The tables are linked via the id column.

A detailed description of the verb tags can be found at https://www.clips.uantwerpen.be/pages/mbsp-tags

| Column Names  | Description           |
| ------------- |:-------------:| 
| id     | Links the three DB tables | 
| MD |  verb, modal auxillary  | 
| VB |  verb, base form   | 
| VBZ |  verb, 3rd person singular present   | 
| VBP |  verb, non-3rd person singular present  | 
| VBD |  verb, past tense   | 
| VBN |  verb, past participle  | 
| VBG |  verb, gerund or present participle  | 
| tagged_sentence |  Feedback sentence with verb tags   | 


### Part of Speech tags (POS)

This table contains the present POS counts for each feedback sentence. The tables are linked via the id column.

A detailed description of the POS tags can be found at https://www.clips.uantwerpen.be/pages/mbsp-tags

| Column Names  | Description           | 
| ------------- |:-------------:| 
| id     | Links the three DB tables | 
| CD | cardinal number  | 
| DT | determiner   | 
| EX | existential there | 
| IN_ | conjunction, subordinating or preposition | 
| JJ | adjective | 
| JJS | adjective, superlative | 
| NN | noun, singular or mass    | 
| NNS | noun, plural | 
| NNP | noun, proper singular    | 
| PRP | pronoun, personal   | 
| PRPS | pronoun, possessive   | 
| RB | adverb   | 
| TO_ | infinitival to   | 
| tagged_sentence |  Feedback sentence with POS tags   | 

## Database Access
The database can be accessed with a python script. e.g.

import sqlite3
db = sqlite3.connect("C:\\db_location")

for row in db.execute("SELECT * from labelled_sentences"):
    print(row)

for row in db.execute("SELECT * from POS"):
    print(row)
    
for row in db.execute("SELECT * from verbs"):
    print(row)

