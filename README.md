# PowerBI_8th_Grade_Assessment_Dashboard_-2024-2025-
Class Assessment Dashboard made for educators to analyze class and student data. 

## 🔢 Project Overview
The 8th Grade Assessment Dashboard offers a comprehensive view of student assessment performance over the 2024–2025 school year. Built in Power BI and currently focused on 1st Period, it uses slicers and DAX formulas to allow dynamic filtering by Student ID, turning the dashboard into a personalized data portfolio for each student.

## 🌟 Key Benefits
* Stakeholder Friendly: Easily presentable to administrators, students, and parents.


* Personalized: Enables student-specific analysis and intervention planning.


* Time-Saving: Reduces data organization time by ~40 minutes, allowing more time for instruction and planning.


* Insightful: Quickly identifies trends and struggles to inform reteaching and tutorials.

## 📊 Assessment Details
Students begin with their 7th Grade STAAR score and take assessments every three weeks:
* Blue Assessments: Mid-six weeks; 8–10 questions covering 1–2 TEKS.


* White Assessments: End-of-six weeks; 12–18 questions covering all TEKS learned to date.


* Benchmark Exam: Mid-year mock STAAR; ~70% of TEKS taught.


This pattern reveals performance differences as students move from short-term to cumulative testing. White tests and Benchmark are often more challenging.

## 🔰 Student Demographics & Coding
30–40% of students are in special populations:
* 5: 504 Program


* S: Special Education


* D: Dyslexia


* L: English Learner


* A: At-Risk


Students may have multiple codes. All student names/IDs are anonymized.
Example: "John Doe" is coded as "AS" and receives SPED services with accommodations for autism, including proximity seating, note copies, breaks, and counseling access.

## 🎯 Dashboard Components

![1st Period Assessment Dashboard](https://github.com/user-attachments/assets/96ff5aa2-2eee-431c-a3b7-5dee6cb6b61e)

1. KPI: Assessment Average
* Use: Tracks average performance per test and per student.


* Student Insight: John Doe averages 34%, 17% below class average.


DAX Sample:
TestAverages =
UNION(
  ROW("Test", "1st White", "AverageScore", AVERAGEX('1ST PERIOD', '1ST PERIOD'[1st White]), "TestOrder", 1),
  ...
)


2. KPI: Overall Growth
* Compares student/class growth from early to late assessments.


* John Doe grew 14% over the year, supported by interventions.


DAX Sample:
SmartOverallGrowth =
VAR SelectedStudent = SELECTEDVALUE('1ST PERIOD'[ID NUMBER])
VAR StartScore = IF(SelectedStudent, SELECTEDVALUE('1ST PERIOD'[1st White]), AVERAGE('1ST PERIOD'[1st White]))
VAR EndScore = IF(SelectedStudent, SELECTEDVALUE('1ST PERIOD'[5th White]), AVERAGE('1ST PERIOD'[5th White]))
RETURN FORMAT(EndScore - StartScore, "0.0%")


3. Highest & Lowest Assessment Scores
* Identifies top/bottom test for each student or the class.


* Useful for identifying successful TEKS and areas of need.


DAX Sample for Highest:
SmartHighestTest = ...

DAX Sample for Lowest:
SmartLowestTest = ...


4. Assessment Trend Visual
Shows class and individual trajectories across the year. John Doe's trend shows steady progress, with a peak at 2nd Blue.
5. Comparison Charts: 7th STAAR vs. 8th Benchmark
* Visually compare prior STAAR with mid-year benchmark.


* John Doe improved from 26% (7th grade) to 33% (8th grade benchmark).


DAX for Comparison Chart:
SlicerAwareBarChartScore =
VAR SelectedStudent = SELECTEDVALUE('1ST PERIOD'[ID NUMBER])
... RETURN SWITCH(...)

## 🔄 Progress by Performance Category
Benchmarks analyzed by category (Did Not Meet, Approaches, Meets, Masters) based on district cutoffs:
* Red: 0–37%


* Yellow: 38–53%


* Blue: 54–76%


* Green: 78–100%


Custom Table Snippet (DAX):
DidNotMeetProgressTable = DATATABLE(...)

Insight: John Doe met 89% of Did Not Meet, 62% of Approaches, etc.

## 📊 Future Goals
* Add growth deltas (+/-) to predictive vs. actual charts.


* Create semester-specific predictive models.


* Enable live grading sync for real-time dashboards.


* Expand dashboards to all periods and other subjects.


* Add TEKS-specific insights and remediation content.


* Build student-access portals and admin overview dashboards.



## 🚀 Final Thoughts
This Power BI dashboard was created not just for data analysis but to empower educators with insights, save time, and promote equity for students who need it most. By combining predictive modeling, targeted KPIs, and dynamic filtering, this dashboard provides a powerful tool for planning, intervention, and academic growth.
