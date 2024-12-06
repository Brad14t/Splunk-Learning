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

Course Topics 
* Creating and managing Scheduled Reports 
* Creating and managing Alerts 
* Using Alert Actions

Course Objectives 
Topic 1 – Creating a Scheduled Report 
* Create a report 
* Schedule a report 
* Define a report's time range 
* Define schedule priority 
* Define schedule window 
* Add a trigger condition 

Topic 2 – Managing Reports 
* View report settings 
* Edit report permissions 
* Enable report embedding 

Topic 3 – Creating Alerts 
* Save a search as an alert 
* Define alert permissions 
* Understand scheduled and real-time alert types 
* Define alert trigger conditions 

Topic 4 – Using Alert Actions 
* Define actions that respond to trigger conditions 
* Write results to a log event 
* Output results to a lookup 
* Output results to a telemetry endpoint 
* Send an email containing search results 
* Set up a webhook alert action 

Topic 5 – Managing Alerts 
* View alert settings 
* Edit alert permissions













