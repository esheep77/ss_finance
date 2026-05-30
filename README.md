# Skysource Finance (ss_finance)
Project to improve Skysource finance processes and analysis

Key Features
-------------
Automatic process to load the existing AceMoney export file (*.xml) into our finance DB.

Design Rationale
-------------
1. Should the source XML file stored in SQL Server?
Since the nature of our source files are full snapshots, and we are not currently doing delta analysis between them.
Also, full transaction details are extracted and stored in the relational tables, so there are no additional benefit 
for storing the source files additionally in DB.

2. What tool used for loading source XML files into SQL Server?
A generic framework is expected to be agreed and developed to handle different automation processes in Skysource.
Before the decision on the framework is made, minimum efforts should be a primary considered for the temporary 
automation script / tool selection.
Xquery in T-SQL is selected as the tool of choice, because its native tool in SQL Server.

Run Script
-------------
1. go to directory `misc\finance\Scripts\`
2. run `.\Setup.ps1`
3. if rebuild database is required, then run `rebuildDB` function.
4. for loading a source file, make sure it is located and with the format of `misc\finance\SourceData\skysource_yyyymmdd.xml`. Run `monthlyLoad` function, then provid the source file date in yyyymmdd format.
