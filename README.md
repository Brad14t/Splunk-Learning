# Splunk-Learning

Notes while learning Splunk


**Commands Learned:**

`| fields [field]` - add or removes fields from search
* `| fields -[field]` - removes a field from search
`| rename [field] as ["New Name"]`- renames a field

`| eval [Old Name] = [New Name]/10/10` - calculate field values to a new temporary field, /10/10 (divides the field by 10 then 10 again.)

`|erex`, `| rex` - extracts fields from data using Regex syntax

`|erex [Field] fromfield=_raw examples= "examples"` searches data like field extractor 

`| rex field=_raw "expression"` - use regular expressions to extract data

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

Course Topics ▪ Formatting data using transforming commands ▪ Preparing data for use in visualizations ▪ Generating maps using geographic data ▪ Creating and customizing single value visualizations ▪ Visually formatting statistical tables

Course Objectives 

Topic 1 – Formatting Commands 
▪ The fields command 

`| fields`

▪ The table command 

`| table [column] [column2] [column3]`

Outputs columns of your choice in a table.

▪ The dedup command 

`| dedup`

Removes duplicate events.

▪ The addtotals command 
▪ The fieldformat command 

Topic 2 – Visualizing Data 
▪ Explore visualization types 
▪ Use transforming commands to order results into a data table: o top o rare o stats o chart o timechart o trendline 
▪ Understand when to use different transforming commands 

Topic 3 – Generating Maps 
▪ Explore geographic visualization types 
▪ Use commands specific to geographic data o iplocation o geostats o geom 
▪ Prepare data for use in a choropleth map








