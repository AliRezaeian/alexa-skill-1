## Introduction:

The goal is to talk to Alexa and have your database table (DynamoDB) update the field with what you told Alexa.

[Image of the architecture]

1. Build the Alexa Interaction Model (the front-end) on developer.amazon.com.
2. Build the back-end functionality using a Node.js lambda function on aws.amazon.com. Point the front-end to the back-end.
3. Set up a database that will store information about what user asked for.
4. Connect the back-end lambda function to the database so that the command you speak to Alexa is stored in the database.

## Before you Begin
You will need an Amazon Echo, an account with [developer.amazon.com](http://developer.amazon.com/) and an account with [aws.amazon.com](http://aws.amazon.com/).

Go to [developer.amazon.com](http://developer.amazon.com/) and [aws.amazon.com](http://aws.amazon.com/) and sign up with the same email address that you’ve registered your Amazon Echo with.

When signing up for AWS, choose the free Basic plan. Building, deploying and testing your solution is all covered by the free plan.

[Image]

## Building the Alexa Interaction Model

The requests the skill can handle (for example, plan a trip, get a fact, turn on a light, find and play video content).
The words the user can say to invoke those requests:
"Alexa, tell plan my trip I want to go to Seattle"
"Alexa, ask cat facts for a fact"
"Alexa, turn on the living room lights"
"Alexa, play Manchester by the Sea"

For the custom model, you define the requests (intents) and the words (sample utterances) yourself. Your code then determines how your skill handles each intent.

## Create a New Skill

1. Go to [developer.amazon.com/alexa](https://developer.amazon.com/alexa).
2. Click **Your Alexa Consoles** and then click **Skills**. This opens the developer console and displays any skills you have already created.
3. Click **Create Skill**.
4. Enter the **Skill name** "MyAlexaSkill".
   * **Skill name**: This is the name customers will see when you publish the skill. You can edit this name later on the Distribution page.
   * **Default language**: You can add additional languages to the skill later.
5. Click the **Custom** model.
6. Click **Create skill**.

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill1.png?raw=true)

7. Select **Start from scratch** to create a new blank skill, then click **Choose**.


![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill2.png?raw=true)

You should now have a green checkmark next to the **Invocation Name**, which means you’ve successfully completed the first small step.

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill3.png?raw=true)

## Add Intents, Slots, and Utterances
An intent represents an action that fulfills a user's spoken request. 
Intents can optionally have arguments called Slots.
The utterances specify the words and phrases users can say to invoke your intents. 

1. From the checklist, click the second bullet **Intents, Samples, and Slots**
2. Enter the name of the new intent **PlanMyTrip** and click **Create custom intent**. This adds a new intent and opens its detail page, displaying the intent's sample utterances and slots.
3. Click **Create custom intent**

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill4.png?raw=true)

4. In the Intents Slots section, create below slots.

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill5.png?raw=true)

5. Enter some sample utterances like:
 
* _i am going on a trip on friday_
* _i want to visit portland_
* _i want to travel from seattle to portland next friday_

Once you have written a few utterances, note the words or phrases that represent variable information. These will become the intent's slots. For example, in the utterances identified above, the variables are highlighted friday, seattle, and portland.

6. In an utterance, highlight the word or phrase representing the slot value.
7. In the drop-down that appears, select the slot. This will replace the original value in the utterance with the slot name in curly brackets ({ }).

8. Click **Save Model**

9. Click **Build Model**.

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill6.png?raw=true)

For example, if user say: "_Alexa, ask Plan My Trip i want to travel from seattle to portland next friday._"

The Alexa service sends the Plan My Trip service a PlanMyTrip intent with the value "Seattle" in the fromCity slot, "Portland" in the toCity slot and the date for the next upcoming Friday travelDate slot. The service can then save this information and send back text to convert to speech.

Slots are defined with different types. The travelDate slot in the above example uses Amazon's built-in AMAZON.DATE type to convert words that indicate dates (such as "today" and "next friday") into a date format, while both fromCity and toCity use the built-in AMAZON.US_CITY slot.

10. Click **Build** menu, You should now have a green checkmark next to the steps 1, 2, and 3.

![](https://github.com/AliRezaeian/alexa-skill-1/blob/master/images/createskill7.png?raw=true)


