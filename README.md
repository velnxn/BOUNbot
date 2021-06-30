CONTENTS OF THIS FILE
---------------------

 * Overview
 * Requirements
 * Installation
 * Contributors


OVERVIEW
------------

The BOUN.bot is a chatbot created to solve the problem of finding your way around the campus without getting lost, a problem that many newcomers to Boğaziçi University may encounter. While giving information about the locations of the buildings in all campuses of Boğaziçi University, it also carries out the task of providing the users with some general information regarding the university itself. The potential questions we used for this project were extracted via the personal experiences of the developers, and a Google Forms survey, which can be reached here: #href. While we did not integrate all of them, we determined major and frequent issues.

There are several technical problems one encounters when actualizing such a project, with several subproblems. To start with, natural language understanding was a big one. To handle most of this, we used Dialogflow. We created multiple intents for asking for a way to get to a location, asking for information, asking about student clubs, and asking for a label for questions such as "ÖTK ne / What is ÖTK?". For these intents we created entities which were categorized under academic and functional buildings, and a cultural category for information intent entities (such as buddy, ötk, öfb). For each entity (="buddy") there were synonyms accounting for morphological properties, typos, and different typing styles ("Buddy", "buddyde", "badi", and so on). Then, we trained our Dialogflow bot for intent classificiation by manually entering potential question forms such as "NH nerede, NH nerde, NHye nasıl gitcem?". After we entered all of our entities and trained our intents, Dialogflow was able to successfully classify the intent of a given input.

Once we completed intent classification, we moved onto Python. First, we integrated the Dialogflow API to pull the intent and to direct our program to the correct answer function. For further natural language understanding, we used Regular Expressions to isolate the entity from the user input. Then for location, clubs, and information answers, we used dictionaries to match the input with its appropriate response. Then, in another function, we called for these dictionaries to print the matching answer. We have this system set up for location, student clubs, and information. For label questions, we wanted to use CFGs to integrate something else from our course. In order to do this, we attempted to pull the entity values from Dialoglow, then, we sent this entity value to another dictionary function with a matching explanation. So far, this is similar to what the have done with RegEx. The difference is that we extract the value from Dialogflow instead (unfortunately this did not work as we could not get the isolated string value), and then we use three functions to give an answer instead of two. For the first function, we use a dictionary as explained above, however, we do not call for this dictionary, but instead use it directly inside a function which returns the value match of the key(the entity) as a string. Then, we have a simple CFG generator function, it generates a few potential sentences that serve as transitions to the actual answer, which is retracted from the dictionary. Then, we have an answer function to adjoin these strings. In the main conversation loop, we call this adjoining function to print both sentences.

To evaluate we intended to use an intrinsic evaluation model. If we had more time we were going to create test data for intent classification consisting of a hundred potential questions. Then we were going to create them matching intents manually and check if Dialogflow is classifying them correctly.


REQUIREMENTS
------------

For the purposes of Python integration for our course, this project requires the private_key.json file for the Dialogflow API to work which is included in our submission. Additionally, it requires installing dialogflow and google-api-core.


INSTALLATION
------------

Install the dialogflow and google-api-core modules by using !pip install.


CONTRIBUTORS 
------------

 * Ateş İsmail Çalışır
 * Duygu Bayram
 * Metehan Eryılmaz
 * Gökçe Güneyi
 * Muhammet Raşit Şenol


