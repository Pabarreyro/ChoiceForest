# Product Overview
## Summary
This site deploys a discrete choice experiment (choice experiment). The point of a choice experiment is to uncover how individuals value certain attributes of a program, product or service by asking them to choose between different hypothetical arrangements of those attributes (_a.k.a._, bundles). In many instances, choice experiments are used to understand how much individuals are willing to pay for something that does not have a market value. The experiment presented in this site is one such instance, focusing on attributes associated with a major urban forested park in Portland, OR. The intended user interacts with this site primarily as a subject of the experiment and therefore only visits it once.

### Working Product Names
* ChoiceForest
* Forest of Choice 
* ChoiceTree 
* SorTri 
* SorTree 
* Atreebute

# Specific Functionality
### Splash Page 
The splash page for the site contains the name of the site, potentially a sub-title for the experiment, and the logos/names of experimental collaborators.

**Key Components:**
* Title, subtitle, logos
* Start button 

**User Actions:**
* Click: start button

**2nd Gen:**
* Animation on the logos 

### Progress Bar
At the top or bottom of every page following the splash is a color-coded progress bar to visualize the user’s progress. Each section of the site is represented by a different color, and page progress appears within or bookends the bar.

**Key Components:**
* Bar with color coding and page progress 

### Introduction 
The first page of the site is an introduction to the study, Forest Park, the experimental attributes with each level, and experimental payment vehicle.

**Key Components:**
* Panels with blocks of text and related media 
* Photo viewer with thumbnail navigation on specific panels 
* Responsive slider or tabs to navigate through panels 
* Progress bar

**Key Actions/Effects:**
* Click/slide: panel tabs or responsive slider

**2nd Gen:**
* Pop-up boxes for more detailed explanations of key words or technical information 
* Animation while sliding back/forth through panels 
* Embedded Google Map for Forest Park panel 

### Choice Experiment
The key component of this site is the choice experiment itself. The entire experiment occurs on one page consisting of approximately 9-11 panels. Each panel is randomly populated with a pair of attribute bundles from a group of 10-15 preselected bundles. These are called choice sets, and the bundles within them are named either Option A or Option B. A third choice, Option C, is available in each choice set if the user prefers neither Option A nor Option B. (_see_ docs folder for choice experiment templates and attributes list)

In each choice set, the user chooses the option that (s)he/they prefer(s). The user may only submit a decision once for each choice set; there is no going back. _Special note_: The first choice set presented to each user is treated as a practice round and kept out of the sample population.

**Key Components:**
* Static collapsible banner with instructions 
* Panels with choice sets that are randomly populated 
* Choice buttons with hover and click highlight effects 
* Submit/Next Set button that is hidden until a choice is made 
* Progress bar

**Key Actions/Effects:**
* Hover: choice button
* Click: choice button, submit/next button

**2nd Gen:**
* Pop-up descriptions of attributes and/or levels 
* Sliding animation for choice sets 

### Questionnaire
The final section of this site contains a questionnaire of roughly 30 questions. These questions are also organized into separate panels that the user either slides, clicks or tabs through. The panels headers are: Allocation, Visits, Activities, Access, Parks, Environmental Attitudes, Personal/Profile. (_see_ docs folder for questionnaire questions)

**Key Components:**
* Panels with form fields for input, radio and checkboxes 
* Responsive slider or tabs to navigate through panels  
* Progress bar

**Key Actions/Effects:**
* Click/slide: panel tabs or responsive slider
* Alert: for unanswered mandatory questions

# Data Model
### Bundle Database
* __bundle_id__: primary key for each tested bundle
* __forest__: level for forest restoration attribute within each bundle
* __education__: level for educational programs attribute within each bundle
* __access__: level for park access attribute within each bundle
* __trails__: level for trail improvement attribute within each bundle
* __signage__: level for signage improvement attribute within  each bundle
* __price_range__: subset assignment for testable price range, delineated in $10 increments from $10-60 
* __sets__: number of sets in which each bundle has appeared
* __set_idX_idY__: number of times bundleX has appeared with bundleY in a choice set

### Experimental Database
* __user_id__: identifier for respondent
* __start_time__: time recorded at experiment start
* __choice_set__: instance of choice set presented to respondent
* __option_A__: randomly assigned attribute bundle in a certain choice set (bundle_id)
* __option_B__: randomly assigned attribute bundle in a certain choice set (bundle_id)
* __choice__: respondent’s stated preferred choice in
* __end_time__: time recorded at end of experiment
* __[fund_option]__: placeholder for each column assigned to allocation question
* __[questionnaire_field]__: placeholder for each column assigned to each questionnaire field

# Technical Components
### Essential Logic
* Method for checking frequency of bundle appearance, either in terms of generic sets or distinct pairs
* Method for assigning bundles to choice sets based on relative past appearance, initially by weighted random sampling with replacement

### Other Specifications
* Program to render pages, gather user input, and pass data back to server
* Bootstrap questionnaire if necessary

# Schedule
### Key Steps
- [ ] Build databases for storing bundle data and experimental data (20 hrs, moderate)
- [ ] Build, train and test essential logic (80 hrs, hard)
- [ ] Build site scaffolding (10 hrs, easy)
- [ ] Build site interactivity (20 hrs, moderate)
- [ ] Maintain documentation and ReadMe (4 hrs, easy)

### Further Work
In the event that all 2nd gen features are completed ahead of schedule, the next phase is to begin building a researcher interface with dashboard-style data outputs for descriptive statistics, marginal willingness to pay and price elasticity of demand for each tested attribute.

