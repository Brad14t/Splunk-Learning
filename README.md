# Splunk-Learning

Notes while learning Splunk for **Splunk Core Certified User**

# Description

I am currently studying to take the Splunk Core Certified User exam, but in general I am studying this to improve my skills in Network analytics and potentially get me a job in a SOC enviorment. If anyone is in the same boat, below I am listing all the important things I am looking at daily to study. I will try to provide all the information I am injesting, to hopefully pass the exam and pass this knowlege to the next.

# Material Used

* Splunk Free Learning Course's

https://www.splunk.com/en_us/training/free-courses/overview.html

* Splunk Test Blueprint

https://www.splunk.com/en_us/pdfs/training/splunk-test-blueprint-user.pdf

* (Udemy) The Complete Splunk Core Certified User Course - SPLK-1001

![1](https://github.com/user-attachments/assets/c185c2bf-ca58-4caf-9ede-5b49e9795dd7)

* Brainscape (Self made flash cards)

* Quizlet (Practice test and flashcards)

https://quizlet.com/350611828/splunk-core-certified-user-flash-cards/?funnelUUID=4e320c6b-f888-40a4-b0e9-e7d16a5f53bb

https://quizlet.com/833938908/splunk-core-certified-user-practice-test-2-flash-cards/

# Keyboard Shortcuts:

`Shift` + `Enter` = A new line 

`Ctrl` + `\` = Auto format search

`Ctrl` + `z` = Go back steps in search

`Ctrl` + `Shift` + `z` = Expanded search (good for macros)

# Splunk Free Learning Course'

**Courses:**

* Intro to Splunk
* Using Fields
* Scheduling Reports and Alerts
* Visualizations
* Working with Time
* Statistical Processing
* Leveraging Lookups and Subsearches
* Search Optimization

**Using Fields**

**Course Topics** 
* What are Fields?

Fields are values extracted during indexing

* What is Field Discovery? 
* Use Fields in Searches 
* Compare Temporary versus Persistent Fields 
* Enrich Data

**Course Objectives** 

**Topic 1 – What are Fields?** 
* Define fields and field auto-extraction

Fields are values of intrest from the data, auto extraction is the index automatically pulling fields from data

* Add fields to the Selected Fields list

Selecting a value from a field window

**Topic 2 – What is Field Discovery?**
* Understand Field Discovery 
* Explore search modes and their effect on search results

**Topic 3 – Use Fields in Searches** 

* Use fields with operators

Operators are: =, != for #'s and strings. >,>=,<,<= for #'s

**Topic 4 – Compare Temporary versus Persistent Fields** 
* Differentiate between temporary and persistent fields

Persistent fields will be extracted everytime the search is run.

Temporary fields are made for specific searches using commands like `|eval`

* Extract temporary fields with the erex and rex commands

`| erex`, `| rex`

RegEx video for learning: https://www.youtube.com/watch?v=QvxLJ9f6AK0 

erex is easier, you dont need to know RegEx, requires samples, and generates a RegEx expression
rex is harder and more intense of a search, you need to know RegEx, doesnt require samples and can use a RegEx as a starting point for searches

**Topic 5 – Enrich Data** 

* Understand how fields from lookups, calculated fields, field aliases, and field extractions enrich data

Calculated fields can only refrence fields that already exist
Calculated field Ex: Bytes/1024/1024

Field Aliases allow alternate names for fields, ex: I search User, the computer searches for all other words I associated with User.

Lookups allow you to add fields or values to events that arent a part of the data.

Search times operation order when working with knowlege objects: Field Extractions, Field Aliases, Calculated Fields, Lookups, Event Types, and Tags


**Scheduling Reports & Alerts**

**Course Topics** 
* Creating and managing Scheduled Reports 
* Creating and managing Alerts 
* Using Alert Actions

**Course Objectives** 
**Topic 1 – Creating a Scheduled Report**
* Create a report 
* Schedule a report 
* Define a report's time range

Time range is when you want the report to report on.

* Define schedule priority

This allows for less strain due to reports completing before moving to the next

* Define schedule window

This is the time in which the action could be performed

* Add a trigger condition 

Trigger condition is what is required for the trigger to activate

**Topic 2 – Managing Reports** 

* Enable report embedding

This makes the report viewable to anyone who has access to web page

**Topic 3 – Creating Alerts** 

* Save a search as an alert

You can save a search and it will alert when the trigger is alerted.

* Define alert permissions

When set to `Private` only I would have access. With `Shared in App` all users in app. 

* Understand scheduled and real-time alert types

Real time will run continuously.

* Define alert trigger conditions

You specify what needs to be going on to send the alert.

**Topic 4 – Using Alert Actions** 

* Define actions that respond to trigger conditions

The action is what the response is to the alert.

* Write results to a log event

Sends log events to Splunk

* Output results to a lookup

Creates or edits a CSV table
  
* Set up a webhook alert action 

Webhook alert is setting it up so an app over the web can receive this alert like a help desk or support app

**Visualizations**

**Course Topics** 
* Formatting data using transforming commands 
* Preparing data for use in visualizations 
* Generating maps using geographic data 
* Creating and customizing single value visualizations 
* Visually formatting statistical tables

**Course Objectives** 

**Topic 1 – Formatting Commands **

* The fields command 

`| fields`

* The table command 

`| table [column] [column2] [column3]`

Outputs columns of your choice in a table.

* The dedup command 

`| dedup [field]`

Removes duplicate events.

* The addtotals command 

`| addtotals col=true label="Toal Sales" labelfield="product_name" fieldname+"Total by Product"`

adds the total of x and creates a column in `| chart`, Label is name of row, field is the field you are looking in and name is the column name

* The fieldformat command 

`| field format` - changes the look of a data field without changing the underlying data

**Topic 2 – Visualizing Data** 

* Explore visualization types 

These are many different types of graphs. Usually requires tables to have 2 colomuns.

* Use transforming commands to order results into a data table: 

`| top` - Finds most common fields (Top 10),  `| top [field] limit=20` changes the shown results #.

`| rare` - Same as top but opposite

`| stats` - anything to do with counting and showing the results 

`| chart` - charting data with visualization

`| timechart` - stat aggrigation using time

`| trendline` - can show data that has been tredning as of lately 

* Command Clauses with transforming commands.

`limit` = int

`countfield` = string

`percentfield` = string

`showcount` = True/False

`showperc` = True/False

`showother` = True/False

`otherstr`= string

**Topic 3 – Generating Maps**

* Explore geographic visualization types

These are different graphs and maps

* Use commands specific to geographic data
`| iplocation` - will create fields of City, Country etc

`| geostats latfield=[field] longfield=[field] count` - aggreigate data for use in a map. ( allows you to split data using a `by` argument.

* Prepare data for use in a choropleth map

You'll need a `.kmz` file (KeyHole Markeup Language)

`| geom` - adds field that match polygons on the map.

EX: 

`| stats count as [New Name Column] by [field_1]`

`| geom [.kmz file] featureIdField=[field_1]`

**Working with Time**

**Course Topics** 

* Searching with Time 
* Formatting Time 
* Comparing Index Time versus Search Time 
* Using Time Commands 
* Working with Time Zones

**Course Objectives**

**Topic 1 – Searching with Time**

* Understand the _time field and timestamps

When data is injested, the timestamp is listed under the field `_time`

Timestamps are in `Unix` or `epoc` time, then translated into readable info.

The timestamp is in your local timezone.

* View and interact with the Event Timeline

Choose your selected time range and select `Zoom to selection`

* Use the earliest and latest time modifiers

`earliest=[+ or -][timeint][timeunit]@[timeunit]`

`latest=[+ or -][timeint][timeunit]@[timeunit]`

+ or - is forward or backwards in time

timeint = the #

timeunit = m = minute, h =hour, d = day, w = week, m = month

EX:

`-30m@h` = looks back `30 minutes` and snap back to the beginning of the `hour`

earliest=-h@h = Rounds down to the hour.

* Use the bin command with the _time field

`| bin` essentially categorizes data

`| bin span=1h _time` = each result will be an hour long span, then you add the data you choose,

`| stats sum(field) as "Name of Coulmn" by _time` = this adds the fields and outputs the hourly amount.

Next to make it readable use the `| eval` command

`| eval [Name column] = strftime(_time, "%b %d, %I %p") 

For the date and time documentation visit: https://docs.splunk.com/Documentation/Splunk/9.3.2/SearchReference/Commontimeformatvariables

**Topic 2 – Formatting Time**

* Use various date and time eval functions to format time

`| eval field1 = now()` = returns the time a search was started 

`| eval field1 = time()` = returns the time an event was processed by eval command

`| eval field1 = relative_time(X,Y)`

**Topic 3 – Using Time Commands**

* Use the timechart command

`| timechart` = aggrigates data into a timed chart

* Use the timewrap command

`| timewrap 1w` = follows a timechart command adn compares, this coompares 1 week ago 

**Statistical Processing**

**Course Topics**

* What is a Data Series

* Transforming Data

* Statistical Aggregation with the stats Command
  
* Manipulating Data with eval
  
* Formatting Data

**Course Objectives** 

**Topic 1 – What is a Data Series**

* Introduce data series

A sequence of related data point inside a visulization.

* Explore the difference between single-series, multi-series, and time series data series

Single-Series: Related data points that review a single data category 

Multi-Series: Related data points that review multiple data categories

Time-Series: Single or multi series that compaires values over time.

**Topic 2 – Transforming Data** 

* Use the chart, timechart, top, and rare commands to transform events into data tables

![1](https://github.com/user-attachments/assets/62cbfa6c-c924-4c11-828b-9eb30cd8e955)

![1](https://github.com/user-attachments/assets/659713d8-ea92-4ab9-b3a7-bfa09012f1e8)

![1](https://github.com/user-attachments/assets/a5a7a7fb-0fd9-449a-a3a0-953412ab2d48)

**Topic 3 – Statistical Aggregation with the stats Command** 

* Define aggregation 

Summarize event values to create a single value

* Explore the stats command and eight of its functions 

![1](https://github.com/user-attachments/assets/15b13481-4736-477f-9f42-0a0e162abb9b)

`| stats dc(field)` = (distinct count) returns a count of the unique values of given field 

`| stats sum(field1)` `|rename sum(field1) as Newfield1` `| sort -Newfield1` = adds the sum of fields and splits it by hosts, rename column, sorts by the most visited (desending order)

`min()` = lowest value in field

`max()` = highest value

`avg()` = average value

`values() as "x"` = gives the values of a field

`list() as "x"` = lists all values even duplicates

**IN GENERAL**

Use `| stats` command for a table.

Use `| chart` and `| timechart` commands for visulizations.

**Topic 4 – Manipulating Data with eval Command** 

* Explore the eval command

![1](https://github.com/user-attachments/assets/e17a8b39-2c49-42dc-9d35-567f1a5a06ca)


* Explore and perform calculations using mathematical and statistical eval functions

![1](https://github.com/user-attachments/assets/15d8bf82-938a-4141-82e2-ea08962d72cb)

* Use the eval command as a function with the stats command 

`pow(x,y)` = Returns xto the power of y, (10, 2) = 100

`round(x,y)` = Rounds x to y (10.34567,2) = 10.34

`max(x, ...)` = Takes an arbritrary number of arguments and returns the maximum

`min(x, ...)` = Takes an arbritrary number of arguments and returns the minimum

`random()` = Takes no arguments and returns a random integer

**Topic 5 – Formatting Data**

* Use the rename command

![1](https://github.com/user-attachments/assets/2ce618ea-f372-4d6d-8616-1f77ba1d5eea)

* Use the sort command

![1](https://github.com/user-attachments/assets/f388e4cb-5074-41d2-bc49-ea29972fc8fe)

**Comparing Values**

**Course Topics** 

* Using eval to Compare 
* Filtering with where & Managing Missing Data

**Course Objectives** 

**Topic 1 – Using eval to Compare**

* Explore the eval command
  
* Explain evaluation functions

![1](https://github.com/user-attachments/assets/76636c6a-2150-47e5-aabd-b1dcf357e9c9)

![1](https://github.com/user-attachments/assets/17eb8ce6-12ba-458c-95a7-c34cb4ae7c75)

![1](https://github.com/user-attachments/assets/0a190509-03c4-45ec-bf03-6eb2cc74f150)


The `validate ()` function is similar to the `case ()` function, but instead of figuring out if a statment is true, instead when a statment it false it returns an argument 

![1](https://github.com/user-attachments/assets/c3578a7c-4253-451a-a755-50732d8b98d7)

![1](https://github.com/user-attachments/assets/0a32fe6e-debb-4978-83d2-91b6f6e0cae3)

![1](https://github.com/user-attachments/assets/d5876031-73ea-4535-bcae-f841e0630fa5)

* Identify and use comparison, conditional, and text functions

![1](https://github.com/user-attachments/assets/6fbf4b25-2e13-4185-9900-bd39fcc5a1e2)

![1](https://github.com/user-attachments/assets/eda602f3-68d7-4998-af21-d73cc2c4ecc6)

![1](https://github.com/user-attachments/assets/26d9a55b-1bba-4a88-ae65-cebc8e661ea6)

![1](https://github.com/user-attachments/assets/2996ec18-34db-4ec4-bdae-5fb4410f46e3)


**Result Modification**

Course Topics 

* Manipulating Output 
* Modifying Result Sets 
* Modifying Field Values 
* Normalizing with eval 

Course Objectives 

Topic 1 – Manipulating Output 

* Convert a 2-D table into a flat table with the untable command 
* Convert a flat table into a 2-D table with the xyseries command 

Topic 2 – Modifying Result Sets 

* Append data to search results with the appendpipe command

![1](https://github.com/user-attachments/assets/2c21349c-d094-4f47-a1a2-cb570bab4bdb)

![1](https://github.com/user-attachments/assets/4abd548e-1e28-4cb9-ac8a-0bffa8764709)

* Calculate event statistics with the eventstats command

![1](https://github.com/user-attachments/assets/799513c6-30dd-4b50-a5b9-7dff80eb4cd3)

* Calculate "streaming" statistics with the streamstats command
  
![1](https://github.com/user-attachments/assets/fd5898f8-49b0-4870-b7dd-668ae23ca2a6)

![1](https://github.com/user-attachments/assets/72750c40-ead8-4fdc-ae22-7b870d486514)

`| xyseries <name Y column>, <X Row>, <field>`

Topic 3 – Modifying Field Values 

* Understand the eval command

`| foreach <field1, field2, field3>` [template]

![1](https://github.com/user-attachments/assets/741a7e41-13a8-44e9-b12d-a4b10bc28526)

* Use conversion and text eval functions to modify field values

`upper()`, `lower()` = upper or lowercase a field

`substring()` = returns a selection of a string

`coalesce()` = take a listr of arguments and returns the first value thats not null.

![1](https://github.com/user-attachments/assets/23b8de7f-ef64-4089-80a7-1368c869b670)


**Leveraging Lookups and Subsearches**

Course Topics 

* Using Lookup Commands 
* Adding aSubsearch 
* Using the return Command

Course Objectives 

Topic 1– Using Lookup Commands 

* Understand lookups 

Lookups allow for adding fields and values not included in the indexer

By default there are 4 types of lookups.

`File` - fields pulled from files like a .csv file

`External` - appends the data using scripts (Python) or executables

`KV Store` - Look up pairs from a KV storage

`Geospacial` - add geographic locationb using a `.kmz` or `.kml` file

* Searchtime sequence: Field Extractions -> Filed Aliases -> Calculated Fields -> Lookups -> Event Types -> Tags

* Usetheinputlookup command to search lookup files 

`| lookup <field> <input> as <new name> OUTPUT <new field1, new field2>`

![1](https://github.com/user-attachments/assets/d00249b1-92ee-40cb-b5ba-de495520be46)

Topic 2– Adding a Subsearch 

* Define subsearch 
* Usesubsearch to filter results 
* Identify when to use subsearch 
* Understand subsearch limitations and alternatives 

Topic 3– Using the return Command 

* Usethereturn command to pass values from a subsearch 
* Comparethereturn and fields commands

**Intro to Knowledge Objects**

Course Topics 

* Using knowledge objects to discover and analyze data 
* Developing naming conventions for knowledge objects 
* Defining permissions for knowledge objects 
* Managing knowledge objects

Topic 1 – What are Knowledge Objects? 

* Understand the different types of knowledge objects: 

* Fields

The resulting extracted data from a search

* Field extractions

Most fields are automaticly extracted on search, but you can find more manually.

* Field aliases

Normalize data by adding alternate names to multiple fields.

* Calculated fields

Fields completing a calculation from a eval command

* Lookups

Data fields not found in current data.

* Event types

A way to save popular or oftenly used searches.

* Tags

Labels for the data.

* Workflow actions

Uses HTTP GET and POST methods to past info to external sources, or return info to Splunk.

* Reports

Another way to save your search.

* Alerts

A way to be notified, or perform an action due to a specific incident, set by you.

* Macros

Search strings or (commands) that can be used in multiple places.

* Data models

Hierarchal structured data sets you can adjust in Pivot (users explore the data)

Topic 2 – Knowledge Object Settings 

* Define naming conventions

Recommended to use 6 keys: group, type, platform, category, time, and description.

* Define role-based permissions for knowledge objects

There are 3 main types: Private (default)(User created), Specific App (Power and Admin user), and All Apps (Admin User)


# Splunk: Zero to Power User


**Module 2:**

Components of Splunk:

* `Forwarder` - Sender of data, lives on the machine, feeds raw data to indexer 

* `Indexer` - Processes data, stores events

* `Search Head` - Executes the searches, interfface for searching indexers, craft SPL

Types of installations of Splunk:

* `Standalone` - single instance, or all in one. (Downloading splunk on your computer)

* `Basic` - use forwarders on remote machine

* `Multi-Instance` - seperation of the search head, forwarders and indexers

* `Clustering` - or having a 1 for 1 replica search heads and a minimum of 3 search heads (use `Deployer` to manage cluster). Same with indexers, replicates mean if 1 goes down the others have the data.


**Module 4A:**

Data Pipeline:

* Input - Forwarders Data=streams

* Parsing - Processing of data Data=events

* License Usage - license meter check

* Indexing - Data is written to disk Data=compressed

**Module 4C:**

An App:

* An App is something with a gui, something you have to launch. (Adds a new front point)

Examples:

* AWS
* Azure
* Corelight

An Add-On:

* Something that runs in the background, workstation view doesnt change.

Examples:

* CrowdStrike
* Juniper
* Unix and Linux
* Palo Alto


**Module 6: Knowledge Objects**

What are knowledge objects?

* Tools and useful things to take advantage when investigating.
* All Knowlege Objects are sharable 

Examples:

* Build an alert when you hit 50 sales.
* Create a tag to turn green when a user is logged in.


Who manages the knowlegde objects?

* Knowlege Manager (person who provides centeralized managment of all KO's)

Best practice for naming conventions:

* <Group name>_<type>_<descriptionz>

Permissions are important for KO's

Types:

* `Private` - Only the creator can use or edit
* `This app only` - Object presist on the context of an app
* `All Apps` - Object presists globally

**Module 7: Fields**

* `Field names` are case sensitive
* `Field values` are NOT case sensitive

* `a` - next to the field means its alphanumeric
* `#` - shows its numeric


**Module 8A:**

Splunk Colors and Syntax:

* `Orange` - Command modifiers (Boolens, as, by)
* `Blue` - The commands (stats, table, rename)
* `Green` - The Arguments (limit, span)
* `Purple` - The Functions (Tostring, sum, values, min, max)

* `Splunk SPL`: Search Processing Language

* `table` - Makes a table from searches 
* `rename` - rename fields
* `fields` - call on fields you want to include or exclude
* `dedub` - removes duplicates
* `sort` - sorts results


**Search process**


I start with a search with my given `index=web` and pick out my fields I want in the table.

I then search `index=web | table clientip, action, categoryId, status`

![Screenshot 2024-12-23 134009](https://github.com/user-attachments/assets/14379ec6-a2b8-4d26-afc3-cf72b2764e0d)

But there are `null` values in the action and field, to remove these from the search I include the `where isnotnull(action)` command to remove the values with null fields.

![Screenshot 2024-12-23 134745](https://github.com/user-attachments/assets/2580e9ac-a36b-4aff-afe1-b3b6fc6f4528)

Then to rename some fields to make it look better I use the `rename` command.

`| rename action as "Action", clientip as "Shoppers IP"`

![Screenshot 2024-12-23 135419](https://github.com/user-attachments/assets/fa9bf3fe-167d-4351-a14a-a8020e19a04e)

Next is using the `fields` command to remove the status.

![Screenshot 2024-12-23 135553](https://github.com/user-attachments/assets/05a16967-4074-414d-a270-01565c9b1204)








