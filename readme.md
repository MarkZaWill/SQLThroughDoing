1.
SELECT FirstName, LastName , CustomerId, Country 
FROM Customer 
WHERE Country != "USA"

2.
Select FirstName, LastName, CustomerId, Country 
FROM Customer
WHERE Country = "Brazil"

3.
Select Customer.FirstName, Customer.LastName, Customer.CustomerId, Invoice.BillingCountry, Invoice.InvoiceId
FROM invoice inner join Customer
WHERE BillingCountry = "Brazil"

4.
Select "Sales Agent", FirstName, LastName
From Employee

5.
SELECT DISTINCT BillingCountry
From Invoice

6.
SELECT
e.FirstName || " " || e.LastName AS SalesAgent,
i.*
FROM Employee e
INNER JOIN Customer c 
 ON e.EmployeeID = c.SupportRepId
INNER JOIN Invoice i 
 ON c.CustomerId = i.CustomerId
WHERE e.Title = "Sales Support Agent"
ORDER BY SalesAgent

7.
SELECT
 i.Total,
 c.FirstName || " " || c.LastName AS CustName,
i.BillingCountry,
e.FirstName|| " " || e.LastName AS SaleAgent
FROM Invoice i 
INNER JOIN Customer c
 ON i.CustomerId = c.CustomerId
INNER JOIN Employee e
 ON e.EmployeeId = c.SupportRepId

8.
SELECT 

Count(Total)
From Invoice 
where InvoiceDate > '2008-12-31 23:59:59'
  and InvoiceDate <  '2010-01-01 00:00:00'

or


InvoiceDate > '2010-12-31 23:59:59'
  and InvoiceDate < '2012-01-01 00:00:00'

166


select sum(total)
from invoice
where
where InvoiceDate > '2008-12-31 23:59:59'
  and InvoiceDate <  '2010-01-01 00:00:00'
449.4600000000003

select sum(total)
from invoice
where
InvoiceDate > '2010-12-31 23:59:59'
  and InvoiceDate < '2012-01-01 00:00:00'

469.5800000000003


9.

select 
invoiceID,
count(InvoiceLineId)

from InvoiceLine
where InvoiceId = '37'
group by invoiceId


10.
select 
invoiceID,
count(InvoiceLineId)

from InvoiceLine

group by invoiceId

11.
select 
t.name,
i.InvoiceLineId

from track t
Inner Join InvoiceLine i
  on t.TrackId = i.TrackId

group by i.InvoiceLineId

12.
select 
t.name,
a.Name,
i.InvoiceLineId

from track t

Inner Join InvoiceLine i
  on t.TrackId = i.TrackId
Inner Join Album l
 on t.AlbumId = l.AlbumId
Inner Join Artist a
  on l.ArtistId = a.ArtistId

group by i.InvoiceLineId

13.
select count(i.InvoiceId),
i.BillingCountry

from Invoice i

group by BillingCountry

14.
select
 count(t.name),
p.name

from Track t
INNER JOIN PlaylistTrack pt
  on t.TrackId = pt.TrackId
INNER JOIN Playlist p
  on pt.PlaylistId = p.PlaylistId

group by p.PlaylistId

15.

select 
t.Name,
al.Title,
m.Name,
g.Name

from Track t
  INNER JOIN Album al
    on t.AlbumId = al.AlbumId
  INNER JOIN MediaType m
    on  t.MediaTypeId=m.MediaTypeId
  INNER JOIN Genre g
    on t.GenreId = g.GenreId
 
16.
select i.*,
sum(il.InvoiceLineId)

from Invoice i
inner join InvoiceLine il
  on i.InvoiceId = il.InvoiceId

group by il.invoicelineid

17.
select 
count(i.total),
e.FirstName || " " || e.LastName as FullName

from invoice i
  inner join customer c
    on i.customerId = c.customerId
  inner join Employee e
    on c.SupportRepId = e.EmployeeId

group by FullName

18.
select 
e.FirstName || " " || e.LastName as FullName,
max(i.total)

from Employee e
inner join Customer c
  on e.EmployeeId = c.SupportRepId
inner join invoice i 
  on c.customerid = i.customerid

 where
 i.InvoiceDate > '2008-12-31 23:59:59'
  and i.InvoiceDate <  '2010-01-01 00:00:00'

Answer: Margaret Park
19.
select 
e.FirstName || " " || e.LastName as FullName,
max(i.total)
from Employee e
inner join Customer c
  on e.EmployeeId = c.SupportRepId
inner join invoice i 
  on c.customerid = i.customerid

Answer: Steve Johnson

20.
select total (c.CustomerId),
e.firstname,
e.lastname

from Customer c
inner join Employee e 
  on c.SupportRepId = e.EmployeeId

group by e.FirstName
  
21.
select sum(i.total),
i.BillingCountry

from Invoice i

Group by i.BillingCountry
order by i.total desc

22.
select
t.name,
 max(i.total/il.unitprice)

from track t
inner join 
  invoiceline il
  on t.trackid = il.trackid
inner join
  invoice i
  on il.invoiceid = i.invoiceid

where
 i.InvoiceDate > '2012-12-31 23:59:59'
  and i.InvoiceDate <  '2014-01-01 00:00:00'

Answer: Insensivel

23.
select
t.name


from track t
inner join 
  invoiceline il
  on t.trackid = il.trackid
inner join
  invoice i
  on il.invoiceid = i.invoiceid
order by (i.total/il.unitprice) desc

Limit 5


24.
select
distinct a.name,
i.total


from artist a
inner join 
  album al
  on a.artistid =al.artistid
inner join
  track t
  on t.albumid = al.albumid
inner join
invoiceline il
 on t.trackid = il.trackid
inner join
invoice i
on il.invoiceid = i.invoiceid
 
order by i.total desc

limit 3

25.
select
max(m.name)


from mediatype m
inner join 
  track t
  on m.MediaTypeId =t.MediaTypeId
inner join
invoiceline il
 on t.trackid = il.trackid
inner join
invoice i
on il.invoiceid = i.invoiceid
 
order by i.total desc











