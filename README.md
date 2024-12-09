# Splunk-Learning

Notes while learning Splunk for **Splunk Core Certified User**

# Using Fields 

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


# Scheduling Reports & Alerts

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

# Visualizations

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

# Working with Time

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

* Use the bin command with the _time field 

**Topic 2 – Formatting Time**

* Use various date and time eval functions to format time 

**Topic 3 – Using Time Commands**

* Use the timechart command 
* Use the timewrap command 

**Topic 4 – Working with Time Zones**

* Understand how time and timezones are represented in your data
* Determine the time zone of your server 
* Use strftime to correct timezones in results








