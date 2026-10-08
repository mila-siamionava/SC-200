Kusto Query Language (KQL) is the query language used to perform analysis on data to create analytics, workbooks, and perform hunting in Microsoft Sentinel. Learn how basic KQL statement structure provides the foundation to build more complex statements.

## Learning objectives

Upon completion of this module, the learner is able to:

- Construct KQL statements
- Search log files for security events using KQL
- Filter searches based on event time, severity, domain, and other relevant data using KQL
# Introduction
Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel and Microsoft Defender XDR. Understanding basic KQL statement structure provides the foundation to build more complex statements.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting. To query log data, you use the Kusto Query Language (KQL).

To learn to write KQL, you start with the basic structure of a KQL statement. The basics include what table to query, how to apply a filter, and how to return specific columns.

# Understand the Kusto Query Language statement structure
A KQL query is a read-only request to process data and return results. The request is stated in plain text, using a data-flow model designed to make the syntax easy to read, write, and automate. The query uses schema entities organized in a hierarchy similar to SQL: databases, tables, and columns.

The query consists of a sequence of query statements. At least one statement is a tabular expression statement that produces data arranged in a table-like mesh of columns and rows. The query's tabular expression statements produce the results of the query.

The tabular expression statement's syntax has tabular data flow from one tabular query operator to another. Starting with the data source, then flowing through a set of data transformation operators bound together by using the pipe (|) delimiter.

For example, the following query has a single statement, which is a tabular expression statement. The statement starts with a table called SecurityEvent. The EventID column's value filters the data (rows) and then the results are summarized by creating a new column for the count() by Account. Next, in the Prepare phase, the results are then limited to 10 rows.

![Diagram of K Q L Statement showing data, condition, and evidence.](https://learn.microsoft.com/en-us/training/wwl-sci/construct-kusto-query-language-statements/media/kql-pipe.png)

 Important

It's essential to understand how the results flow through the pipe "|". Everything on the left of the pipe is processed then passed to the right of the pipe.

## Access the Log Analytics demo environment

Microsoft provides access to an environment to practice writing KQL statements. The only requirement is to have an account to log into Azure. There are no charges to your Azure account to access this environment. You can execute the KQL statements in this module in the demo environment.

You can access the demo environment at the [Logs Demo site](https://aka.ms/lademo). If you receive the message _No results found_, try increasing the time range (or timeOffset) to > 30 days.

 Important

The log analytics demo database is a dynamic environment. The events recorded in the tables in that environment are continuously updating with different security events. This is similar to what a person would experience in a real-world security operations setting. As a result, finite queries in this training may show no results depending on the state of the demo database at the time the query is run. For example, a query on the _SecurityEvent_ table for "discardEventID = 4688" within the last day may show no results if that particular event last took place three days ago. Therefore, you may need to adjust variables in the scripts listed in this training depending on what data is in the demo database at the time you run the script in order for the query to show results. These script adjustments are similar to what you would perform in the real world and should help you learn how the specific parts of the script function.

![Screenshot of the Log Analytics Demo Environment.](https://learn.microsoft.com/en-us/training/wwl-sci/construct-kusto-query-language-statements/media/log-analytics-demo-2.png)

The Query window has three primary sections:

- The left area is a reference list of the tables in the environment.
    
- The middle top area is the Query editor.
    
- The bottom area is the Query Results.
    

Before running a query, adjust the time range to scope the data. To change the result columns displayed, select the Columns box, and choose the required columns.

# Use the where operator
The where operator filters a table to the subset of rows that satisfy a predicate.

Try each of these queries separately to see the results.

Kusto

```
SecurityEvent
| where TimeGenerated > ago(1d)

SecurityEvent
| where TimeGenerated > ago(1h) and EventID == "4624"

SecurityEvent
| where TimeGenerated > ago(1h)
| where EventID == 4624
| where AccountType =~ "user"

SecurityEvent | where EventID in (4624, 4625)
```

# Use the let statement
Let statements bind names to expressions. For the rest of the scope, where the let statement appear, the name refers to its bound value. Let statements improve modularity and reuse since they allow you to break a potentially complex expression into multiple parts. Each part is bound to a name through the let statement, and together they compose the whole. Let statements allow for the creation of user-defined functions and views. The views are expressions whose results look like a new table.

## Declare and reuse variables

Let statements allow for the creation of variables to be used in later statements. In this example, timeOffSet and discardEventId are created and used as part of the SecurityEvent "where" clause.

 Note

You may need to increase the timeOffset and time ranges to see results in the [Logs Demo site](https://aka.ms/lademo) environment. We suggest using > 30 days if you don't see results.

Kusto

```
let timeOffset = 7d;
let discardEventId = 4688;
SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId

```

 Tip

"ago()" is a function that takes the current Date and Time and subtract the value provided.

## Declare dynamic tables or lists

Let statements allow for the creation of dynamic tables or lists.

Kusto

```
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

Kusto

```
let LowActivityAccounts =
    SecurityEvent 
    | summarize cnt = count() by Account 
    | where cnt < 1000;
LowActivityAccounts | where Account contains "SQL"
```

# Use the extend operator
The extend operator will create calculated columns and append the new columns to the result set.

The KQL example below uses the extend operator to create a new column, StartDir containing the directory a process was started in. The StartDir column is a calculated column containing the results of a substring function.

Kusto

```

SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
```

# Use the order by operator


Sort the rows of the input table by one or more columns.

The order by operator can utilize any column or multiple columns by using a comma separator. Each column can be ascending or descending. The default order for a column is descending.

Kusto

```
SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
| order by StartDir desc, Process asc
```

![[Pasted image 20260929151248.png]]

# Summary and resources
You should have learned how basic KQL statement structure provides the foundation to build more complex statements.

You should now be able to:

- Construct KQL statements
- Search log files for security events using KQL
- Filter searches based on event time, severity, domain, and other relevant data using KQL

## Learn more

You can learn more by reviewing the following.

[KQL quick reference | Microsoft Learn](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Become a Microsoft Sentinel Ninja](https://techcommunity.microsoft.com/t5/azure-sentinel/become-an-azure-sentinel-ninja-the-complete-level-400-training/ba-p/1246310)


# Analyze query results using KQL

# Introduction
Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel and Microsoft Defender XDR. Understanding how to summarize and visualize data with a KQL statement provides the foundation to build efficient threat detections.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting. To query log data, you use the Kusto Query Language (KQL). You write KQL statements that aggregate and correlate data that allows for pattern detection. One such aggregation might be the number of failed logons. This information, combined with a predetermined threshold, can be used to generate an alert for "Account with over 10 failed logons in the past hour" as an example.

The KQL summarize operator performs the calculations, and produces a table that aggregates the contents of the input table. To quickly see a pattern, an analyst can visualize the results in a graph. The KQL render operator performs the visualization. Combining the summarize and render operators provides the foundation for advanced visualizations, including time bucketing and time slicing.

 Tip

You can test the following KQL query examples in the [LA Demo site](https://ms.portal.azure.com/#view/Microsoft_OperationsManagementSuite_Workspace/LogsDemo.ReactView/). If you receive the message "No results found," try changing the time range.

# Use the summarize operator
You use the summarize operator with other operators like the count operator. The count operator with its variations creates a new column with the calculated result for the specified fields.

The first statement below returns one column that is a unique list of Activity column values.

The second statement returns a count of SecurityEvent rows where EventID equals 4688, and the count is grouped by Process and Computer. Because of the by clause, the result set contains three columns: Process, Computer, Count.

Run each Query separately to see the results.

Kusto

```
SecurityEvent | summarize by Activity

SecurityEvent
| where EventID == "4688"
| summarize count() by Process, Computer

```

The example below is a partial list of the most common simple aggregate functions used with the summarize operator.

|Function(s)|Description|
|---|---|
|count(), countif()|Returns a count of the records per summarization group|
|dcount(), dcountif()|Returns an estimate for the number of distinct values taken by a scalar expression in the summary group.|
|avg(), avgif()|Calculates the average of Expr across the group.|
|max(), maxif()|Returns the maximum value across the group.|
|min(), minif()|Returns the minimum value across the group.|
|percentile()|Returns an estimate for the specified nearest-rank percentile of the population defined by _Expr_. The accuracy depends on the density of population in the region of the percentile.|
|stdev(), stdevif()|Calculates the standard deviation of Expr across the group, considering the group as a sample.|
|sum(), sumif()|Calculates the sum of Expr across the group.|
|variance(), varianceif()|Calculates the variance of Expr across the group, considering the group as a sample.|

## count function example

An aggregate function column can be explicitly named by including the "fieldname=" before the aggregate function.

The KQL statement returns three columns: "cnt," "AccountType," and "Computer." The "cnt" field name replaces the default "count_" name.

Kusto

```
SecurityEvent
| where TimeGenerated > ago(1h)
| where EventID == 4624
| summarize cnt=count() by AccountType, Computer

```

## <dcount> function example

The following example returns a count of unique IP Addresses.

Kusto

```
SecurityEvent
| summarize dcount(IpAddress)

```

## Let's take a look at a real-world example

The following statement is a rule to detect Invalid Password failures across multiple applications for the same account.

The where operator for ResultDescription filters the result set for results including "Invalid password." Next, the statement "summarize" produces a distinct count of application names and group by User and IP Address. Finally, there's a check against a variable created (threshold) to see if the number exceeds the allowed amount.

Kusto

```
let timeframe = 30d;
let threshold = 1;
SigninLogs
| where TimeGenerated >= ago(timeframe)
| where ResultDescription has "Invalid password"
| summarize applicationCount = dcount(AppDisplayName) by UserPrincipalName, IPAddress
| where applicationCount >= threshold
```

# ==Use the summarize operator to filter results==
The arg_max() and arg_min() functions filter out top and bottom rows respectively.

## arg_max function

The following statement returns the most current row from the SecurityEvent table for the computer SQL10.NA.contosohotels.com. The * in the arg_max function requests all columns for the row.

Kusto

```
SecurityEvent 
| where Computer == "SQL10.na.contosohotels.com"
| summarize arg_max(TimeGenerated,*) by Computer

```

## arg_min function

In this statement, the oldest SecurityEvent for the computer SQL10.NA.contosohotels.com is returned as the result set.

Kusto

```
SecurityEvent 
| where Computer == "SQL10.na.contosohotels.com"
| summarize arg_min(TimeGenerated,*) by Computer

```

## Revisiting the result pipe

The order results pass through the pipe character matters. Review the following two KQL statements. What is the difference between the result sets?

Run each Query separately to see the results.

Kusto

```
// Statement 1

SecurityEvent
| summarize arg_max(TimeGenerated, *) by Account
| where EventID == "4624"

// Statement 2

SecurityEvent
| where EventID == "4624"
| summarize arg_max(TimeGenerated, *) by Account

```

Statement 1 has Accounts for which the last activity was a Logon.

The SecurityEvent table is summarized and returns the most current row for each Account. Then only rows with EventID equal to 4624 (Login) are returned.

Statement 2 has the most recent Logon for Accounts that have logged in.

The SecurityEvent table is filtered to only include EventID = 4624. Then these results are summarized for the most current Logon row by Account.

# Use the summarize operator to prepare data

Completed100 XP

- 5 minutes

The make_ functions return a dynamic (JSON) array based on the specific function's purpose.

## make_list() function

The function returns a dynamic (JSON) array of all the values of Expression in the group.

This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of Accounts. The resulting JSON array will include duplicate accounts.

Kusto

```
SecurityEvent
| where EventID == "4624"
| summarize make_list(Account) by Computer

```

![Screenshot of a make_list function results.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-results-kusto-query-language/media/make-list-results.png)

## make_set() function

Returns a dynamic (JSON) array containing distinct values that Expression takes in the group.

This KQL query will first filter the EventID with the where operator. Next, for each Computer, the results are a JSON array of unique Accounts.

Kusto

```
SecurityEvent
| where EventID == "4624"
| summarize make_set(Account) by Computer

```

![Screenshot of a Make_set function results.](https://learn.microsoft.com/en-us/training/wwl-sci/analyze-results-kusto-query-language/media/make-set-results.png)

# Use the render operator to create visualizations


The render operator generates a visualization of the query results.

The supported visualizations are:

- `areachart`
- `barchart`
- `columnchart`
- `piechart`
- `scatterchart`
- `timechart`

Kusto

```
SecurityEvent 
| summarize count() by Account
| render barchart

```

## Use the summarize operator to create time series

The bin() function rounds values down to an integer multiple of the given bin size. Used frequently in combination with summarize by .... If you have a scattered set of values, the values are grouped into a smaller set of specific values. Combining the generated time series and pipe to a render operator with a type of timechart provides a time-series visualization.

Kusto

```
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart
```

![[Pasted image 20260929164208.png]]

- **`areachart`** — use for **trends over time when volume matters**.  
    Example: _How did alert volume change over time?_
    
- **`barchart`** — use to **compare categories or show Top N results**.  
    Example: _Which users generated the most alerts?_
    
- **`columnchart`** — use to **compare categories or time buckets with vertical columns**.  
    Example: _How many incidents occurred each day?_
    
- **`piechart`** — use to show **parts of a whole / percentages**.  
    Example: _What percentage of alerts came from each severity?_
    
- **`scatterchart`** — use to show the **relationship between two numeric values**.  
    Example: _Is file size related to execution count?_
    
- **`timechart`** — use for **time-series data and changes over time**.  
    Example: _How did failed logins change over the last 24 hours?_

![[Pasted image 20260929165302.png]]


    

**Easy memory rule:**  
`timechart` = time, `barchart` = ranking, `piechart` = percentage, `scatterchart` = number vs number.

![[Pasted image 20260929165341.png]]
![[Pasted image 20260929165400.png]]
![[Pasted image 20260929165848.png]]
![[Pasted image 20260929165909.png]]
![[Pasted image 20260929165924.png]]
# Summary and resources
You should have learned how Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel.

You should now be able to:

- Summarize data using KQL statements
- Render visualizations using KQL statements


# Build multi-table statements using KQL
# Introduction
Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to correlate data from different tables with a KQL statement provides the foundation to build detections in Microsoft Sentinel.

You're a Security Operations Analyst working at a company that's implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting.

To query log data, you use the Kusto Query Language (KQL). Often a result set from a KQL statement needs to be combined or joined with another result set. You can use the union operator to combine two result sets. The join operator joins rows together based on a key value. You need to understand how the order of a KQL statement impacts your expected results.

# Use the union operator
The union operator takes two or more tables and returns the rows of all of them. Understanding how results are passed and impacted with the pipe character is essential.

Based on the time window set in the Query window:

- Query 1 returns all rows of SecurityEvent and all rows of SigninLogs
    
- Query 2 returns one row and column, which is the count of all rows of SecurityEvent and all rows of SigninLogs
    
- Query 3 returns all rows of SecurityEvent and one row for SigninLogs.
    

Run each Query separately to see the results.

Kusto

```
// Query 1

SecurityEvent 
| union SigninLogs  

// Query 2

SecurityEvent 
| union SigninLogs  
| summarize count() 
| project count_

// Query 3

SecurityEvent 
| union (SigninLogs | summarize count()| project count_)

```

The union operator supports wildcards to union multiple tables. The following KQL creates a count for the rows in all tables with names that start with Security.

Kusto

```
union Security* 
| summarize count() by Type

```

When using wildcard unions, you often need to know which source table each row came from. Use the `withsource` parameter to add a column that identifies the source table for each row.

Kusto

```
union withsource=SourceTable Security*
| summarize count() by SourceTable
```

# Use the join operator


The join operator merges the rows of two tables to form a new table by matching the specified columns' values from each table.

Syntax

LeftTable | join [JoinParameters] ( RightTable ) on Attributes

Kusto

```
SecurityEvent 
| where EventID == "4624" 
| summarize LogOnCount=count() by EventID, Account 
| project LogOnCount, Account 
| join kind = inner (
     SecurityEvent 
     | where EventID == "4634" 
     | summarize LogOffCount=count() by EventID, Account 
     | project LogOffCount, Account 
) on Account

```

The first table specified in the join is considered as the Left table. The table after the join keyword is the right table. The columns from the tables are designated, the `$left.Column` and the `$right.Column` to distinguish which tables columns you're referencing.

When joining tables, you use Join flavors to determine the joining behavior. It's essential to understand the impact of records on the left and right side based on the join flavor. The graphic below shows which records will be kept if there's or isn't a matching record in the other dataset. The **inner join** will only show records from the left side if there's a matching record on the right side. The right side will also require a left side record.

![Diagram of Example join types, showing where how joins work.](https://learn.microsoft.com/en-us/training/wwl-sci/build-multi-table-statements-kusto-query-language/media/kusto-query-language-m03-01.png)

|Join Flavor|Output Records|
|---|---|
|kind=leftanti, kind=leftantisemi|Returns all the records from the left side that don't have matches from the right|
|kind=rightanti, kind=rightantisemi|Returns all the records from the right side that don't have matches from the left.|
|kind unspecified, kind=innerunique|Only one row from the left side is matched for each value of the on key. The output contains a row for each match of this row with rows from the right|
|kind=leftsemi|Returns all the records from the left side that have matches from the right.|
|kind=rightsemi|Returns all the records from the right side that have matches from the left.|
|kind=inner|Contains a row in the output for every combination of matching rows from left and right.|
|kind=leftouter|Contains a row for every row on the **left** side, even if it has no match on the right. Unmatched right-side cells contain nulls.|
|kind=rightouter|Contains a row for every row on the **right** side, even if it has no match on the left. Unmatched left-side cells contain nulls.|
|kind=fullouter|Contains a row for every row on **both** the left and right sides, even if there's no match. Unmatched cells on either side contain nulls.

![[Pasted image 20260929173039.png]]

# Summary and resources

You have learned how Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to correlate data from different tables with a KQL statement provides the foundation to build detections in Microsoft Sentinel.

You should now be able to:

- Create queries using unions to view results across multiple tables using KQL
    
- Merge two tables with the join operator using KQL|

# Work with data in Microsoft Sentinel using Kusto Query Language

# Introduction
Kusto Query Language (KQL) is the query language used to perform analysis on data to create Analytics, Workbooks, and perform Hunting in Microsoft Sentinel. Understanding how to work with fields containing structured and unstructured string data with a KQL statement provides the foundation for extracting data used in building detections in Microsoft Sentinel.

You're a Security Operations Analyst working at a company that is implementing Microsoft Sentinel. You're responsible for performing log data analysis to search for malicious activity, display visualizations, and perform threat hunting.

To query log data, you use the Kusto Query Language (KQL). Often fields in a table store structured and unstructured string data. You write KQL statements to extract and manipulate data stored in these fields. A typical scenario is a key-value pair stored in a field, and you need to query the specific value of a key.

# Extract data from unstructured string fields
Security log data is often contained in unstructured string fields and requires parsing to extract data. There are multiple ways of pulling information from string fields in KQL. The two primary operators used are extract and parse.

## Extract

Extract gets a match for a regular expression from a text string. You may optionally convert the extracted substring to the indicated type.

Kusto

```
print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"

```

Arguments

- regex: A regular expression.
    
- captureGroup: A positive int constant indicating the capture group to extract. A "0" stands for the entire match, a "1" for the value matched by the first '('parenthesis')' in the regular expression, 2 or more for subsequent parentheses.
    
- text: A string to search.
    
- typeLiteral: An optional type literal (for example, typeof(long)). If provided, the extracted substring is converted to this type.
    

Returns

If regex finds a match in text: the substring matched against the indicated capture group captureGroup, optionally converted to typeLiteral.

If there's no match, or the type conversion fails: null.

The following example uses the extract function to pull out the Account Name from the Account field of the SecurityEvent table.

Kusto

```
SecurityEvent
| where EventID == 4672 and AccountType == 'User'
| extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account))
| summarize LoginCount = count() by Account_Name
| where Account_Name != ""
| where LoginCount < 10

```

## Parse

Parse evaluates a string expression and parses its value into one or more calculated columns. The computed columns have nulls for unsuccessfully parsed strings.

Syntax

`T | parse [kind=regex [flags=regex_flags] |simple|relaxed] Expression with * (StringConstant ColumnName [: ColumnType]) *`

Arguments

- T: The input table.
    
- kind:
    
    - simple (the default): StringConstant is a regular string value and the match is strict. All string delimiters should appear in the parsed string, and all extended columns must match the required types.
        
    - regex: StringConstant may be a regular expression and the match is strict. All string delimiters, which can be a regex for this mode, should appear in the parsed string, and all extended columns must match the required types.
        
    - flags: Flags to be used in regex mode like U (Ungreedy), m (multi-line mode), s (match new line \n), i (case-insensitive) in RE2 flags.
        
    - relaxed: StringConstant is a regular string value and the match is relaxed. All string delimiters should appear in the parsed string, but extended columns may partially match the required types. Extended columns that didn't match the required types get the value null.
        
- Expression: An expression that evaluates to a string.
    
- ColumnName: The name of a column to assign a value to, extracted from the string expression.
    
- ColumnType: Optional. The scalar value that indicates the type to convert the value to. The default is the string type.
    

Returns

The input table extended according to the list of columns that are provided to the operator.

The following statement demonstrates the parse operator, which evaluates a string expression and parses its value into one or more calculated columns. Use for structuring unstructured data.

Kusto

```
let Traces = datatable(EventText:string)
[
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=15, lockTime=02/17/2016 08:40:00, releaseTime=02/17/2016 08:40:00, previousLockTime=02/17/2016 08:39:00)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=20, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=22, lockTime=02/17/2016 08:41:01, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:01)",
"Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=16, lockTime=02/17/2016 08:41:00, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:00)"
];
Traces  
| parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices:long * "sliceNumber=" sliceNumber:long * "lockTime=" lockTime ", releaseTime=" releaseTime:date "," * "previousLockTime=" previousLockTime:date ")" *  
| project resourceName, totalSlices, sliceNumber, lockTime, releaseTime, previousLockTime
```


# Extract data from structured string data

Strings fields may also contain structured data like JSON or Key-Value pairs. KQL provides easy access to these values for further analysis.

## Dynamic Fields

Within a Log Analytics table, there are field types defined as Dynamic. Dynamic fields contain a key-value pair such as:

```
{"eventCategory":"Autoscale","eventName":"GetOperationStatusResult","operationId":"xxxxxxxx-6a53-4aed-bab4-575642a10226","eventProperties":"{\"OldInstancesCount\":6,\"NewInstancesCount\":5}","eventDataId":" xxxxxxxx -efe3-43c2-8c86-cd84f70039d3","eventSubmissionTimestamp":"2020-11-30T04:06:17.0503722Z","resource":"ch-appfevmss-pri","resourceGroup":"CH-RETAILRG-PRI","resourceProviderValue":"MICROSOFT.COMPUTE","subscriptionId":" xxxxxxxx -7fde-4caf-8629-41dc15e3b352","activityStatusValue":"Succeeded"}
```

To access the strings within a Dynamic field, use the dot notation. The DeviceDetail field from the SigninLogs table is of type dynamic. In this example, you could access the Operating System with the DeviceDetail.operatingSystem field name.

Kusto

```
SigninLogs 
| extend OS = DeviceDetail.operatingSystem

```

The query example below shows the use of Dynamic fields with the SigninLogs table.

Kusto

```
// Example query for SigninLogs showing how to break out packed fields.

SigninLogs 
| extend OS = DeviceDetail.operatingSystem, Browser = DeviceDetail.browser 
| extend StatusCode = tostring(Status.errorCode), StatusDetails = tostring(Status.additionalDetails) 
| extend Date = startofday(TimeGenerated) 
| summarize count() by Date, Identity, UserDisplayName, UserPrincipalName, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails 
| sort by Date

```

## JSON

KQL provides functions to manipulate JSON stored in string fields. Many logs submit data in JSON format, which requires you to know how to transform JSON data to queryable fields.

The example below is a list of JSON related functions and operators.

|**Function**|**Description**|
|---|---|
|parse_json() or todynamic()|Interprets a string as a JSON value and returns the value as dynamic. Use either of these functions to refer to a field: JsonField.Key or JsonField["Key"]|
|mv-expand|is applied on a dynamic-typed array or property bag column so that each value in the collection gets a separate row. All the other columns in an expanded row are duplicated. mv_expand is the easiest way to process JSON arrays.|
|mv-apply|Applies a subquery to each record and returns the union of the results of all subqueries. Apply a query to each value in an array.|

Run each query separately to see the results.

Kusto

```
SigninLogs 
| extend AuthDetails =  parse_json(AuthenticationDetails) 
| extend AuthMethod =  AuthDetails[0].authenticationMethod 
| extend AuthResult = AuthDetails[0].["authenticationStepResultDetail"] 
| project AuthMethod, AuthResult, AuthDetails 


SigninLogs 
| mv-expand AuthDetails = parse_json(AuthenticationDetails) 
| project AuthDetails

SigninLogs 
| mv-apply AuthDetails = parse_json(AuthenticationDetails) on
(where AuthDetails.authenticationMethod == "Password")
```


# Integrate external data
The externaldata operator returns a table whose schema is defined in the query itself. And whose data is read from an external storage artifact, such as a blob in Azure Blob Storage or an Azure Data Lake Storage file.

Syntax

```
 externaldata ( ColumnName : ColumnType [, ...] )
  [ StorageConnectionString [, ...] ]
  [with ( PropertyName = PropertyValue [, ...] )]
```

Arguments

- ColumnName, ColumnType: The arguments define the schema of the table. The syntax is the same as the syntax used when defining a table in. create table.
    
- StorageConnectionString: Storage connection strings that describe the storage artifacts holding the data to return.
    
- PropertyName, PropertyValue, ...: More properties that describe how to interpret the data retrieved from storage, as listed under ingestion properties.
    

Currently, supported properties are:

ARGUMENTS

|Property|Type|Description|
|---|---|---|
|format|string|Data format. If not specified, an attempt is made to detect the data format from file extension (defaults to CSV). Any of the ingestion data formats are supported.|
|ignoreFirstRecord|bool|If set to true, indicates that the first record in every file is ignored. This property is useful when querying CSV files with headers.|
|ingestionMapping|string|A string value that indicates how to map data from the source file to the actual columns in the operator result set. See data mappings.|

Returns

The externaldata operator returns a data table of the given schema with data parsed from the specified storage artifact, indicated by the storage connection string.

 Note

This example is not available in the demo environment.

Kusto

```
Users
| where UserID in ((externaldata (UserID:string) [
    @"https://storageaccount.blob.core.windows.net/storagecontainer/users.txt" 
      h@"?...SAS..." // Secret token needed to access the blob
    ]))
| ...

```

# Create parsers with functions


Parsers are functions that define a virtual table with already parsed unstructured strings fields such as Syslog data.

In the Logs window, you create a query, select the Save button, enter the Name, and select Save As Function from the drop-down. In this case, if we name the function "PrivLogins," I can then access the table using the name PrivLogins.

Kusto

```
SecurityEvent
| where EventID == 4672 and AccountType == 'User'

```

Kusto

```
PrivLogins

```

## ASIM parsers

Microsoft Sentinel extends this concept with **Advanced Security Information Model (ASIM) parsers** — pre-built functions that normalize data from different log sources into a common schema. ASIM parsers follow the same saved-function mechanism described in this unit but are deployed at the workspace level and maintained by Microsoft.

To learn how to use and create ASIM parsers, see [Normalize and analyze data with ASIM in Microsoft Sentinel](https://learn.microsoft.com/en-us/training/modules/data-normalization-microsoft-sentinel/).

![[Pasted image 20260929180959.png]]
# Summary and resources

In this module, you learned how to use Kusto Query Language (KQL) to manipulate string data ingested from log sources.

You should now be able to:

- Extract data from unstructured string fields using KQL
- Extract data from structured string data using KQL
- Create Functions using KQL
