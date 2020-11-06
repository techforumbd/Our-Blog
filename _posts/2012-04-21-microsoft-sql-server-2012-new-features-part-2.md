---
layout: post
title: Microsoft SQL Server 2012 New Features Part-2
date: 2012-04-21 21:06
author: techforumugm
comments: true
categories: [MS SQLServer]
---
<span><br style="page-break-before:always;" /></span><span><strong>EOMONTH </strong></span><br /><span>We have to face problem whenever we are going to identify the end date of month no built in function was there but now that problem has over in SQL Server 2012, EOMONTH return the date of the month</span><br /><span>SELECT EOMONTH (‘05/02/2012’) ‘EOM Processing Date</span><br /><span>Output: 2012-02-29</span><br /><span>You can specify number of month with EOMONTH function also and it can be negative value</span><br /><span>SELECT EOMONTH ( Getdate(), -1 ) AS 'Last Month'</span><br /><span>Output: 2012-01-31</span><br /><br /><strong><span>CHOOSE </span></strong><br /><span>Using this you can find out the specific item from a list of values.</span><br /><span>SELECT CHOOSE ( 4, 'CTO', 'GM', 'DGM', 'AGM', ’Manager’ )</span><br /><span>Output: AGM</span><br /><br /><strong><span>CONCAT</span></strong><br /><span>This function is concatenating two or more string</span><br /><span>SELECT CONCAT( emp_name,’Joining Date’, joingdate)</span><br /><span>Output: Rahman Joining Date 01/12/2001</span><br /><span><br /></span><strong><span>LAST_VALUE and FIRST_VALUE</span></strong><br /><span>Using the function you can last value among the set of ordered values according to specified ordered &amp; partitioned criteria. First value return the first value in an ordered set of values.</span><br /><span>Insert into result(Department ,ID ,Marks ) values (1,103,70), (1,104,58) (2,203,65) (2,201,85)</span><br /><span>Select   Department,Id ,Marks, last_value(Marks) over (Partition by Department order By Marks) as</span><br /><span>‘Marks Sequence’ ,first_value (Marks) over (Partition by Department order By Marks) as ‘First value’</span><br /><span>from result</span><br /><span>OutPut</span><br /><span>Department   Id        Marks      Marks Sequence      First value’</span><br /><span>1                 104       58            58                           58</span><br /><span>1                 103       70            70                           58</span><br /><span>2                 203       65            65                           65</span><br /><span>2                 201       85            85                           65</span><br /><span><br /></span><strong><span>LEAD</span></strong><br /><span>Using the function you can accesses data from a subsequent row in the same result set without the use of a self-join.</span><br /><span>SQL:</span><br /><span>SELECT BusinessEntityID, YEAR(QuotaDate) AS SalesYear, SalesQuota AS CurrentQuota,</span><br /><span>LEAD(SalesQuota, 1,0) OVER (ORDER BY YEAR(QuotaDate)) AS PreviousQuota</span><br /><span>FROM Sales.SalesPersonQuotaHistory</span><br /><span>WHERE BusinessEntityID = 275 and YEAR(QuotaDate) IN ('2005','2006');</span><br /><span>OutPut:</span><br /><span>BusinessEntityID SalesYear   CurrentQuota          NextQuota</span><br /><span>---------------- ----------- --------------------- ---------------------</span><br /><span>275              2005        367000.00             556000.00</span><br /><span>275              2005        556000.00             502000.00</span><br /><span>275              2006        502000.00             550000.00</span><br /><span>275              2006        550000.00             1429000.00</span><br /><span>275              2006        1429000.00            1324000.00</span><br /><span>275              2006        1324000.00            0.00</span><br /><span><br /></span><strong><span>File Group Enhancement:</span></strong><br /><span>A FILESTREAM filegroup can contain more than one file. For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files.</span>