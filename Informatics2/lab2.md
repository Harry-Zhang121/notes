# Laboratory report
|name|Qianhao Zhang|
|----|--|
|NEPTUN Code|CP4IRF|
|Lab number|Lab2|
|Lab time| 2022-10-03|


---

## Task1
>  List the names of all countries in the Middle East, sorted by the 2004 population count in descending order.

### Answer
```sql
select name from country 
where region = "Middle East" and year = 2004
order by population desc
```
### Reasoning
Output name of all the rows
filtered by region and year
Then sort by population in descending order.

---

## Task2
> List the names, area and GDP of any European countries with a 2009 population of more than 10,000,000.

### Answer
```sql
select name,area,gdp from country
where region like '%Europe%' and year = 2009 and population > 10000000
```

### Reasoning
select will output name, area and gdp.
`region like '%Europe%' ` will filter region with subsrting "Europe" in it.
Then filter by year and population greater than 10000000

---

## Task3
>  List the names and regions of countries with an area larger than 2,000,000 but smaller than 5,000,000, sorted in descending order by 2002 GDP.

### Answer
```sql
select name, region from country
where year = 2002 and area between 2000000 and 5000000
order by gdp desc;
```

### Reasoning
`between` operation filter the area greater than 2000000 but smaller than 5000000

---

## Task4
> List the regions (without duplicates) of all countries whose
names start with 'S' (uppercase).

### Answer
```sql
select distinct region from country
where name like 'S%';
```

### Reasoning
`select distinct` will list regions without duplication.
`like 'S%'` filters all countary with name start with S.

---

## Task5
> Insert a new row with country name "SQLvania", with year = 2004, area = 4707 and population = 65550.
> check with SELECT.

### Answer
```sql
insert into country (name, year, area, population)
values ("SQLvania", 2004, 4707, 65550);

select * from country
where name = "SQLvania";
```

### Reasoning
The standerd insert and select syntax.
filter by name which is "SQLvania"

---

## Task6
> Add 15,000 to the 2007 population of all countries with an area less than 10,000.
> Check with SELECT before and after your changes.

### Answer
```sql
select * from country where year = 2007 and area < 10000;

update country
set population = population + 15000
where year = 2007 and area < 10000
```

### Reasoning
update population equals itself + 15000
Countries affected are thoes with year 2007 and area < 10000.

---

## Task7
> Delete all rows that have a negative GDP.
> Count the number of rows before and after deletion.

### Answer
```sql
select count(*) from country;

delete from country where gdp < 0;
```
### Reasoning
number of rows before delete is 4141
after delete is 3616

---


## Task8
>  List a country with the biggest population in 2010.
> The resulting table should contain name, region, and population.

### Answer
```sql
select name, region, max(population) from country
where year = 2010;
```

### Reasoning
max function returns the biggest value of population.

---

## Task9
> List three Asian countries with the smallest total GDP growth for all years.
> The resulting table should contain name and total GDP.

### Answer
```sql
select name, sum(gdp) as total_gdp from country
where region = "Asia"
group by name
order by total_gdp asc
limit 3;
```

### Reasoning
`select sum(gdp) as total_gdp` get the sum of gdp and rename it as "total_gdp"
use sum together with group by gives us the total gdp of each countary

`where region = "Asia"` filter only asian countries.

`order by total_gdp asc limit 3` sort the total_gdp in ascending order and only output the first 3.

---

## Task10
> List any countries with total GDP growth greater than 1.4.
> The resulting table should contain name, region and total GDP.

### Answer
```sql
select name, region, sum(gdp) as total_gdp from country
group by name
having total_gdp >1.4
```

### Reasoning
`where` cannot be used with aggregate function
So we use `having` to filter total_gdp

