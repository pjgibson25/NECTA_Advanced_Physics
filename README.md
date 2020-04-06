# <u>README</u>


## This file is designed to explain my project to transcribe and database Tanzania Advanced Physics NECTA questions.  Sections include:
<ol> 
    <li> Background </li>
    <li> Methodology </li>
    <li> Python Files </li>
</ol>

##### * Note that this repository is incomplete and is continually being updated.  When finished, this message will be deleted *


## 1.)  Background

#### <b>Bio</b>
My name is PJ Gibson and I was a Peace Corps Education Volunteer in Tanzania from July 2019 - March 2020 when all Peace Corps volunteers worldwide were evacuated because of the COVID-19 pandemic.  I taught Form 5 advanced level physics at Tosamaganga to over 200 bright Tanzanian boys aged anywhere between 18-23.  

#### <b>Inspiration</b>
As a teacher, I wished for a more accessible and organized online catalog of physics learning materials.  Specifically, I wanted an online database of previous Tanzanian NECTA examinations.  The NECTA is a national exam in Tanzania that has a large influence on your future life-path. Having the questions accessible online would allow teachers to easily share NECTA-level material with their students and help them adequately prepare for an objectively difficult final examination.  If organized by sub-topic, teachers could plan lessons around giving students the physics knowledge and english literacy skills to solve related NECTA-level questions, many of which appear more than once throughout the past few years.

#### <b>Goal</b> 
I want to use the existing [Maktaba](https://maktaba.tetea.org/) resources to electronically transcribe advanced Physics NECTA examination questions.  After transcribing each question from all accessable years, I will tag each question with its respective: NECTA year, topic, sub-topic.  In cooperation with [Maktaba](https://maktaba.tetea.org/), I hope to make this sortable database publically accessable online.

Potential additional tags include: respective syllabus objective, definition flag (0 or 1), marks.  These will be completed time-permitting.

#### <b>Additional Notes</b> 
<ul>
<li>
    I would like to thank Peace Corps for the opportunity to allow me to volunteer teaching secondary education in Tanzania.  
</li>
<li>
I would like to thank Maktaba by TATEA for the work they do to help provide accessable online study material for Tanzanian students.  
</li>
<li>
No thanks to COVID-19 for causing us to evacuate.  That being said, stay smart and safe.
</li>
</ul>

## 2.)  Methodology

<ol>
    <li>
        Create the following folders:
        <ul>
            <li> csv_files </li>
            <li> docx </li>
            <li> finished_texts </li>
            <li> OCR_outs </li>
            <li> pdfs </li>
            <li> python_files </li>
        </ul>
    <li> 
        Manually download all Advanced Physics NECTA questions from <a href="https://maktaba.tetea.org/past-exams/acsee/#physics">Makataba</a>.  I put these into the <i>pdfs</i> folder.
    </li>
    <li> 
        Sift these question files through an online OCR tool geared to scrape text from picture files. I do this by running the python program 'PDF pics to text.ipynb'.  Let run until finished.  This will output text files to the <i>OCR_outs</i> folder.  
    </li>
    <li>
        Manually edit the resulting text files by visually comparing them to the pictures.  This is tedious but faster than transcribing from scratch.  I edit by creating a .docx version of the text file simply because it is easier to read and it is always nice to have multiple copies of files in case of accidental slipups.
    </li>
    <li>
        Save the finished, edited version to the folder called <i>finished_texts</i>.  Move the corresponding pdf to the <i>pdfs/finished</i> folder.  Move the corresponding OCR scraped text file to the <i>OCR_outs/finished</i>
    </li>
    <li>
        After all tests are edited, use the python file called 'NECTA_onebyone.ipynb' to create a CSV that tags each question with its respective NECTA year, Topic, Subtopic.  Send this CSV file to the folder called <i>csv_files</i>.  
    </li>
</ol>

<b> WHEN TRANSCRIBING QUESTIONS: </b>
    <ul>
        <li> I do not preserve numbering formatting, only raw questions. </li>
        <li> In text files, different questions are seperated by 2 paragraphs.  Questions depending on one another or deemed to be extremely related are kept together as one multiple-part question. </li>
        <li> I do not transcribe images/tables/diagrams.  Instead, each question depending on these will contain six hash marks - ######.  This unique tag will aid in cataloging them later, perhaps at the very end. </li>
        <li> Each equation and variable within a problem is created using a consistant format that I may play with later on down the line to make look prettier </li>
    </ul>

## 3.)   Python Files

Python is a computer programming language that is free and awesome.  You can use it to make your life easier in most imaginable situations.  For the sake of describing this project's python files, let's first start with two bits of relevant information.

<b>OCR</b> - Web based Optical Character Recognition (OCR) tools are used to scrape text from images of papers.  Upon being fed an image, the tool scans for recognizable characters and attempts to recreate the image into copyable text. The one that I use is called [Free Online OCR](https://www.newocr.com/)

<b>Selenium</b> - [Selenium](https://www.selenium.dev/) is a Python library that allows you to navigate websites.  As it says on the webpage, it automates browsers.  By recognizing patterns in the hidden HTML of a webpage, you can create a program using Selenium that automates an otherwise very tedious job.  Massive shouts out to Selenium, it's freaking awesome.


#### <u>PDF pics to text.ipynb</u>

<b>Input:</b>  Images of NECTA examinations.  These are stored in the <i>pdfs</i> folder and all have a file ending in .pdf even though many of them are simply images.

<b>Process:</b>  Using Selenium, this program submits an examination file into an online OCR, waits for it to process, copies and saves the outputted scraped text, moves on to the next page of the examination until complete (can only run an OCR for one page).  After completing all pages, it moves onto the next examination until all examinations have been scraped.

<b>Output:</b>  Text files with the same names as the examination original '.pdf' files, but now ending in '.txt' and saved to the <i>OCR_outs</i> folder.


#### <u>NECTA_onebyone.ipynb</u>

This file has not been practiced on much and will likely be edited further.

<b>Input:</b>  An examination text file from the <i>finished_texts</i> folder.

<b>Process:</b>  The program shows the user the text for a question.  The user must input the cooresponding sub-topic code. Sub-topic codes can be easily found using the 'subtopic_codes.odt' file within this same folder.  After submitting the sub-topic code, the program jumps to the next question until all are complete.  

Human errors in sub-topic code labelling are troubleshooted at the end until all inputted codes match those in 'subtopics_and_codes.txt'.

<b>Output:</b>  After going through and inputting each question's subtopic code, the program will output a CSV file to the <i>csv_files</i> directory.  
