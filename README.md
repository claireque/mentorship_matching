# mentorship_matching
Optimize mentor-mentee matching using Linear Programming with `gurobipy` in Python

### Background
Finding the best way to match mentor and mentees has been a challenge. It is always a time-consuming and manual process, which often invovling a few rounds of adjustments to finalize the match results.

Using Linear Programming and optimization methodology, we are able to define 'good match' and extract all possible combinations of mentor-mentee pairs to achieve global optimum. We completed a pilot matching for the mentorship program by Women in Big Data (WiBD), Southern California Chapter.

### Summary of the procress
1) We have conduct a survey on everyone who signed up for mentorship program. Besides contact information, the survey question involves following parts.
   - Preferred meeting location (Downtown LA, West LA, Orange County etc.)
   - Perferred meeting time (Morning/breakfast, Evening/Happy Hour, Weekday, Weekends etc.)
   - Perferred mentor and/or mentee area (Technical skills, Industry insights, Career prep/resume/internship search etc.)
   - Functional expertise and interest (Consulting, Engineering, Finance etc.)
   - Industry expertise and interest (Internet/Technology, Healthcare, Manufacturing etc.)
   - Area of experise and interst in analytics(tools and software, data science, machine learning/AI etc.)
2) Convert survey results into a format that can be used in linear programming constraints in gurobipy. All participants answers on each question were represented as key-value pairs in the format of dictionary - `(participant id,content of question,option number):selected or not selected` . For example: 
   - `(12, 'AE', 1): 1` represents participant 12 identified first option (analytics tools and software) as their area of expertise
   - `(30, 'AI', 1): 1` represents participant 30 identified first option (analytics tools and software) as their area of interest
   - `(7, 'T', 1): 0` means participant 7 is not avaliable to meet during breakfast or morning time
3) Scope the problem in context of linear programming and identfy constrains and objectives.
   - Constrains:
     - Two participants can only be matched if they selected same meeting location and same meeting time.
     - Also the two participants need to have at least one of the selections in common: same mentor area and mentee area, same functional expertise and interst, same industry expertise and interest, same area of expertise and interest. 
   - Objective: allow maximun number of common matches accross all participants.

4) Run Guribo optimizer and convert output results into pair of participant ids.


### About Women in Big Data (WiBD)

Women in Big Data was founded in June 2015 by 15 incredible women in big data, with the goal to strengthen the diversity in the big data field. As part of this initiative, WiBD would like to encourage and attract more female talent to the big data & analytics field and help them connect, engage and grow.

It has gained over 2500 members from 50 companies and universities, along with chapters globally from coast to coast in the US, Europe and Latin America. 

WiBD Website: https://www.womeninbigdata.org/
<br>
SoCal Meetup: https://www.meetup.com/Women-in-Big-Data-Meetup-SoCal-Chapter/
