# AlexaBot for Asana -- Create Asana Tasks with Amazon Echo

## Overview
AlexaBot is an Alexa Skill that lets you create tasks in Asana with voice
commands through the Amazon Echo. It's optimized for quick task creation, letting
you create reminders for yourself and for others in your workspace.

## User Experience
Unlike other Alexa Skills, this script optimizes for efficiency of adding tasks.
Alexa Skills usually require you to invoke the app and then give it a command.
This causes the command to be overly verbose and cumbersome ("Alexa, tell Asana
to create a task for Peter to buy milk today").

AlexaBot uses the person's name as the invocation name, which makes it much faster to
create tasks. You can say things like:

 - Alexa, ask Peter to buy milk today.
 - Alexa, tell Charlie to pick up the dry cleaning tomorrow.
 - Alexa, tell David to fix the sink by next week.
 - Alexa, ask Elizabeth to get more dog food before end of this month.

AlexaBot creates a task and assigns it to the right person.

It also parses out the relative date from the utterance, translating it into
the Due Date field in Asana. In the last example above, Elizabeth will get
assigned the task "Get more dog food" with a due date of "January 31, 2017"
(assuming today is a day in January 2017).

For a list of supported date utterances, check out ./alexa_config/TARGET_DATES.txt.

## Setting Up Your Asana Workspace
1. Create a new user in your workspace called "AlexaBot". The script will
connect to Asana as this user.
2. Create a project in your workspace called "Alexa Tasks". This will make it
easy to see all tasks created from Alexa in one view.

## Setting Up The Script
Instructions for setting up the script are in the AlexaAsanaClient.py file.
After configuring the variables, run create_deployment.py to package up a .zip
file to upload to Amazon AWS Lambda.

Be sure to create an environment variable ASANA_ACCESS_TOKEN in the Lambda function
console with the Personal Access Token obtained in the Asana Account Settings.
**Be sure to log into Asana as Alexa Bot to get the right token.**

## Setting Up The Alexa Skills
You will need to set up a separate skill for every person in your team in
the Alexa Developer Console. This makes it super easy to invoke task creation
as mentioned above.

If you're setting up a skill for Peter:

 - In "Skill Information": set Name to "Asana - Peter"
 - In "Skill Information": set Invocation Name to "peter"
 - In "Interaction Model": follow directions in ./alexa_config/README.md
 - In "Configuration": choose "AWS Lambda ARN (Amazon Resource Name)" click "North America" and paste the ARN name found in your Amazon Lambda function.

That's it. AlexaBot should be up and running at this point.

## Feedback
This is not an official Asana project. Open to all feedback, but I won't have time
to maintain this project. Hope you find this useful!
