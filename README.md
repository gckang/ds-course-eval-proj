# Student Subjectivity in Course Evaluations
## Contents
### Goal Statement
The aim of this project is to evaluate whether students use more extreme language when providing reviews to other students compared to faculty members. 
### Research Question
Is there a significant difference of language extremity in UVA undergraduate student reviews on theCourseForum compared to SET course evaluations to the professor and department dean for the same class?
## Section 1: Software and Platform
This project utilized Python, Jupyter Notebook, and GitHub. Both a Mac and Windows computer were used for this project, but this project can run on any platform that has the required installations. <br />
The packages needed for this project include pandas, seaborn, nltk, wordcloud, matplotlib, requests, beautifulsoup4, and scipy. <br /><br />
The SET data was provided to us in a pdf; in order to convert the pdf into a csv file, the app Tabula (https://tabula.technology/) was downloaded to extract the comments for the csv. Tabula can run on Windows, Mac, and Linux. <br />
## Section 2: map of documentation
```bash
ds-course-eval-proj <br />
├── DATA <br />
│   ├── cleaned <br />
│   │   ├── cleaned-set.csv <br />
│   │   ├── cleaned-tcf.csv <br />
│   │   └── student_eval_data.csv <br />
│   └── source <br />
│       ├── ECON 2010-F23-Course Comments.pdf <br />
│       ├── Report for ECON 2010 - 090 Principles of Econ Microecon ECON 2010 - 091 Principles of Econ Microecon Kenneth  Elzing_c7e1b9b5-65a9-4b0f-90a9-047a67313099.pdf <br />
│       └── tabula-ECON 2010-F23-Course Comments.csv <br />
├── OUTPUT <br />
│   ├── SET Compound Score Density.png <br />
│   ├── SET Compound Score Distribution.png <br />
│   ├── SET Extremity Score Density.png <br />
│   ├── SET Extremity Score Distribution.png <br />
│   ├── SET Most Frequent Adjectives.png <br />
│   ├── tCF Compound Score Density.png <br />
│   ├── tCF Compound Score Distribution.png <br />
│   ├── tCF Extremity Score Density.png <br />
│   ├── tCF Extremity Score Distribution.png <br />
│   └── tCF Most Frequent Adjectives.png <br />
├── SCRIPTS <br />
│   ├── webscraping.ipynb <br />
│   └── course_evals_proj.ipynb <br />
├── LICENSE.md <br />
└── README.md <br />
```

## Section 3: instructions for reproducing results
### Acquiring the Data:
From the original “Report for ECON 2010 - 090…” PDF file, we extracted specifically the pages that provided comments to the question “What would you like the instructor and university administrators to know about your experience in this course?” into a new PDF with less pages using Adobe Acrobat. This file is named “ECON 2010-F23-Course Comments.pdf”. <br /><br />
From there, we used the Tabula app to scrape the comments from the pdf file into a csv file simply by uploading the pdf file within the app. The resulting csv file is named “tabula-ECON 2010-F23-Course Comments.csv”. <br /><br />
To clean the scraped PDF file table, follow the script “webscraping.ipynb” and run the cells related to creating a cleaned SET evaluation csv file. The script takes “tabula-ECON 2010-F23-Course Comments.csv” and then removes extra headers (rows that only say “Comments”) and empty reviews (reviews that contain null, nothing, or just say no). It saves this clean data set into “clean-set.csv” for future analysis. <br /><br />
This script will also web scrape theCourseForum reviews for Professor Kenneth Elzinga’s ECON 2010 class using Beautifulsoup. It takes in the data from the website which not only includes the review and semester date, but also the anonymous students’ rating of the professor, its difficulty, and enjoyability. Afterwards, it saves the data into “clean-tcf.csv” for future analysis.  <br />
### Analyzing the Data:
The cleaned-set.csv and cleaned-tcf.csv data should be downloaded and saved to a folder accessible to your IDE. The script “course_evals_proj.ipynb” should be run. This will establish the data frames, run sentiment analysis on the reviews, and provide scores for the language extremity for each review. <br /><br />
Lines 11-27 can be run for exploratory analysis on the data: The script produces plots of the language extremity scores, the most common adjectives, and the score density. <br /><br />
Lastly, this script will perform a two-sided Welch’s t-test on the “Extremity” data for each data set to determine if there is a significant difference in language extremity between the reviews from theCourseForum compared to SET Reviews. 
