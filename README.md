# Pewlett-Hackard-Analysis

An analysis of ride-share data among different populated region types over the course of several months.

## Overview of the analysis:

The purpose of this project was to help a fellow analyst, Bobby, help gather data about a wave of upcoming retirees from a company called Pewlett Hackard.  Using our knowledge of PostgreSQL and pgAdmin, it was our duty to help create then substantiate a database to gather and intepret the data about the employees of the company!

## Results:
From our deliverables in the project there are four major takeaways from the data that should be used to help Pewlett-Hackard into the future!

* As per our conclusion in the first deliverable, there are roughly 90,000 employees at the company who are born between 1952 and 1955 which puts them in a retiring age.  Of those retirees, 57,668 of them are comprised of senior engineers or senior staff!  Hiring more engineers and general staff need to be priority for the company to help create more senior staff positions or the company could face serious worker-shortage.

* Only 2 out of the massive pool of potential retirees are managers according to our data but that is also potentially a problem.  Given that so much of the company is comprised of engineers and general staff, the loss of those two suggests there probably are not that many managers to begin with so doing some additional training to help provide leadership within the company could help avoid the potential risk of there only being two managers because most of the baby-boomer employees were equipped enough in company logistics to not need a manager.

* Per our second deliverable, tre are just over 1500 employees eligbile for a mentorship position within the company.  Incentivizing these employees to help mentor new hirees or younger staff members to be better prepared for when such a large portion of the company retires will be vital in keeping the company afloat in future years.


## Summary:

* How many roles will need to be filled as the "silver tsunami" begins to make an impact? - Given the staggering number of retirees looming upon the company ( roughly over 90,000 per our deliverable 1 data table) I would say a safe number of hires would be mininum 70,000.  Given you are still down 10s of thousands in man power, the mentorship program introcued in deliverable two can hopefully help recouperate the balance of expertise in the company and make rollover less straining on employees and company alike.  Hiring that many people in a short window however seems lofty and Pewlett-Hackard may be in for a rude awakening.

* Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees? - 1549 eligible retirees within the silver tsunami demographic seems like a lot but considering you most likely will not be able to convince all of them to participate then lets be safe and say they acquire 1000 company veterans to partake.  That would leave each mentor with roughly 90 people to mentor beneath them to get a 100% turn around.  No, I do not think there are enough qualified retirement ready personnel at the company.  Incentivise this program for all older employees to avoid future pit holes of manpower removal or the company will suffer dramatically.  Each mentor should ideally work with under 10 people in a year to create an active environment in which they can instruct their successor to do the job successfully which would require probably around 8-9 thousand mentors!  However, these 1549 eligible mentors were those only born in the year 1965, though the argument within the hypothetical is that this is the age in which most mentors probably would come from a simple change to our 2nd querie in which our WHERE expression be changed to in between 1950 january first and the end of 1965 as opposed to strictly doing 1965.  This could provide a much larger pool of eligible and willing employees than those strictly born in 1965 that can be used to help ease Pewlett-Hackard weather the storm that is coming!


```
SELECT DISTINCT ON (e.emp_no) e.emp_no,
	e.first_name,
	e.last_name,
	e.birth_date,
	de.from_date,
	de.to_date,
	t.title
INTO mentorship_eligibility
FROM employees as e 
INNER JOIN dept_emp as de
ON (e.emp_no = de.emp_no)
INNER JOIN titles as t
ON (e.emp_no = t.emp_no)
WHERE (e.birth_date BETWEEN '1950-01-01' AND '1965-12-31')
AND (de.to_date = '9999-01-01')
ORDER BY emp_no;
```


