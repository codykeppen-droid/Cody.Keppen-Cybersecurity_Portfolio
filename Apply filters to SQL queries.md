# Apply filters to SQL queries

## Project description

This project is to demonstrate using SQL filters to review different databases  in cyber security like scenarios.

## Retrieve after hours failed login attempts

In a scenario where I will need to review failed login attempts in after hours, I would use the following command.<br><br> 

`MariaDB [organization]> clear`<br>
`MariaDB [organization]> SELECT *`<br>
       `->FROM login_in_attempts`<br>
       `->WHERE login_time > '18:00:00' AND success =0;`

By using ‘SELECT \*’, I am returning all columns in the database.  
The second line ‘FROM log\_in\_attempts’ specifies the table to return these columns from.  
The last line, ‘WHERE login\_time \> ‘18:00:00’ AND success \= 0;’, filters to return only the login time after 7pm that had a failed login attempt. 

## Retrieve login attempts on specific dates

In this scenario, as a cyber security analyst, I am reviewing the login attempts on two different dates.

`MariaDB [organization]> SELECT *` <br>
`-> FROM log_in_attempts` <br>
`-> WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';` <br>

This is returning all columns in the log\_in\_attempts database. The WHERE line is specified to only return data on the two dates, 2022-05-09 and 2022-05-08 by using the OR statement.

## Retrieve login attempts outside of Mexico

In this scenario, I am reviewing all login attempts outside of Mexico as a routine cyber security check.

`MariaDB [organization]> SELECT *` <br>
` -> FROM log_in_attemps` <br>
 `-> WHERE NOT country Like 'MEX%';` <br>

With the code above, I am using the NOT filter to remove the following condition of any country that is LIKE “MEX%’. Using LIKE  and ‘%’ as a wildcard, it will remove any entry in the country column of the database that starts with the letters ‘MEX’. This is because the combination of LIKE and ‘MEX%’ includes any abbreviations or full spellings of the country, Mexico.

## Retrieve employees in Marketing

In this scenario, I am reviewing all employees in the Marketing department, who are in the east building. This is due to a project to update these employees machines.

`MariaDB [organization]> SELECT *` <br>
`-> FROM employees` <br>
`-> WHERE department = 'Marketing' and office LIKE 'East%';` <br>

The above is pulling all columns from the employees database, with the department filtered to only return those in the Marketing department in any of the east buildings. This is also taking advantage of the ‘%’ wildcard to return any of the east buildings.

## Retrieve employees in Finance or Sales

In this scenario, I will be reviewing all employees in the Finance or Sales department to perform updates on their computers.

`MariaDB [organization]> SELECT *` <br>
`-> From employyes` <br>
`-> WHERE department = 'Finance' or department = 'Sales';`<br>

The code above is pulling all columns in the employees database. Using the OR statement to filter only those in the Finance or the Sales department.

## Retrieve all employees not in IT

In this scenario, another update is needed but not for IT personnel.

`MariaDB [organization]> SELECT *` <br>
`-> From employees` <br>
`-> WHERE department NOT LIKE 'Information Technology';` <br>

Using this code, I am pulling all rows of data from the employees database. Using the NOT LIKE statement, all departments with be returned except the Information Technology department.

## Summary

This project was used to simulate basic SQL filtering. These steps included,

* Pulling in data from a database  
* Using these filters to pull specific data for different actions  
  * AND  
  * OR  
  * NOT  
  * LIKE  
  * ‘%’ Wildcard

These actions were used to simulate tasks like reviewing logs outside of regular work shifts.  Filtering specific personnel to prepare for computer maintenance. Filtering off unnecessary data to review important data efficiently or to have on hand a checklist of computers that need maintenance in different buildings or departments.  
