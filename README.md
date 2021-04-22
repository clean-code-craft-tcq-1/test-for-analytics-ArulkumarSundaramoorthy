# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.


## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Opening/Reading CSV file
3. Date & Time access dependenices in microcontroller
4. Data structure Creation compactability for PDF
5. Converting Data into PDF format
6. Access to the server to store the PDF
7. Notification dependenices like Email means access to the platform

(add more if needed)

### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | Yes           | External Libraries software & Test the converter function called or not using mock/fake test function
Counting the breaches       | Yes           | This is part of the software being developed
Detecting trends            | Yes           | This is part of the software being developed
Notification utility        | Yes           | External Libraries software & Test the utility function called or not using mock/fake test function

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Write a test case to test true notifications, when new report available
4. Write a test case to test false notifications
5. Write a test case to test PDF report generated once in a week
6. Test the record trends, if reading increasing continuously for 30 mins
7. Test the Date & Time are correctly updating
8. Write a test case to count the maximum breach
9. Write a test case to count the minimum breach
10. Write a test case to count combination of minimum & maximum breach

(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | PDF file stored | Notification function call counter              | Mock function with counter
Report inaccessible server | Server address/port | Server accessable fail return               | Fack function to report server inaccessible
Find minimum and maximum   | csv data | Internal Data structure update               | None - it's a pure function
Detect trend               | csv data |Internal Data structure update               | None - it's a pure function
Write to PDF               | Internal data structure | PDF converter function call counter              | Mock function with counter
