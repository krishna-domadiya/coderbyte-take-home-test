# Ticket Breakdown
We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads:

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**


Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".


You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here

Ticket 1: Save shift wise agent info 

1. Create new function to save custom agent id along with shift id in new table (agent_shifts)
-> When a staffing company books an agent for given shift, that will fetch agent id first
-> Fetched agent id will be customized i.e. agent id = 12 will become agent id = f12 or f_12 based on the requirements
-> This new agent id will be saved in new table (agent_shifts) along with corresponding shift id
2. Now, if a user want to fetch agent details, a foreign key (shift id) present in Facilities table will be used to get data from agent_shifts table.


Ticket 2: Generate report

1. Create a new function which will calculate how many hours for each agent for given quarter
-> Shift related information can be fetched using getShiftById existing function
-> Now, using that shift details, we can fetch agent details 
-> After getting shift and agent details, we can count how many hours used by that agent for given quarter
-> The report can be generated now using those details
