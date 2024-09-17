# **Character Data**
---------


>Another name for a character data is a **string**. A string is any data enclosed in single quote (' '). It could be a number or alphabet or both.


Lets have a look at some built-in functions in snowflake used in string generation,manipulation, extraction and searching 

> - (' ') - Single quotes : used to generate or create strings
> > Examples:  

```sql
select 'my name is hopelyn';

select 'I am 8 years old';

select 'a + 2';
```

! [generating codes!
](Screenshot 2024-09-17 164348.png)



> - | | or concat( ) : For concatenating or joining strings together
>> Examples:

```sql
select 'my name is hopelyn' || ' and ' || 'i am 8 years old';

select 'my name is hopelyn.' || ' ' || 'I am wealthy';

---Note: without the single quotes between the pipes, the first letter of the second string will be joined to the last letter of the first string.Your result will look this way >> my name is hopelyni am wealthy**  

--- The single quotes can be left empty or you can insert what ever you want in there.make sure to give one space before and after insertion. like this >> ' and '


lets join our strings using  the concat() function

select concat('my name is hopelyn', ' and ', 'i am 8 years old');

select concat('my name is hopelyn', ' ', 'i am 8 years old');

---here you must always insert a comma (,) after every single quotes

```

> - Char( ) : For inputting characters which do not appear on your keyboard.
>> Examples:

```sql
CONCAT('I spent', CHAR(8364),'357 in Paris')

--- Note: To do this you have to know the character's ASCII value. In computing, each character has a unique numerical code called an ASCII (American Standard Code for Information Interchange) value. This value represents the character in a computer's memory and is used for processing and storing text.

```

> - upper( ),  lower( ),  initcap( ) : These are functions used to change a string to all uppercase, lowercase or upper case for the first character of each word.
>> Examples:
```sql
select upper('goat');

select lower('GOAT');

select initcap('victor is a farmer and i like farming');

select upper(str.val),lower(str.val), initcap(str.val) from values('goat') as str(val);

```

> - Reverse ( ) : Reverses the character of a string.
>> Examples:

```sql
select reverse('nohtyp evol i');

select reverse('nohtyp htiw gnidoc nuf sti');

select reverse('sis rejoice is a pretty lady');

```

> - Translate( ) : Helps remove or replace  unwanted characters from a string
>>Examples:

```sql
select translate('(857)-234-5678','()-','');
---The result will be 8572345678

select translate(('cpoork'),'pr','');
 ---The result will be cook

select translate('cpoork','pr','o');  
---The result will be coook

```

> - ltrim( ), rtrim( ), trim( ) : for removal of spaces from the begining or ending of a string or from both ends.
>> Examples:

```sql

select ltrim(str.val), rtrim(str.val), trim(str.val) from values( '   goat   ') as str(val);

```

> - Length( ) : To show the length of a string
>> Examples:

```sql

select length(ltrim(str.val)) as str1_len, length(rtrim(str.val)) as str2_len, length(trim(str.val)) as str3_len from values( '   goat   ') as str(val);

```

>- Position( ) : To find the position of a substring within a strng
>>Example:

```sql
select position('farm',str.val) as pos1,
 position('farm',str.val,10) as pos2,
 position('like',str.val) as pos3
       from (values ('victor is a farmer and i like farming')) as str(val);

```

> - Substr( ) : Gives only the  part of a string you need. It takes a string, a starting position, and an optional number of characters.
>>Examples:

```sql
substr(str.val, 11) as rest_of_string
from (values ('operation and maintenance')) as str(val);

select substr(str.val, 2, 16) as start_of_string, 
substr(str.val, 17) as rest_of_string
from (values ('operation and maintenance')) as str(val);

select substr(str.val, 2, 16) as start_of_string, 
from (values ('operation and maintenance')) as str(val);


--You could use the position( ) function as a parameter to the substr( ) function  to determine the starting position.

select substr(str.val, position('tion',str.val))
from (values ('operation and maintenance')) as str(val);

--it returns "tion and maintenance"

```

#  **Numeric Data**
-------------

Lets have a look at some arithmetic operators and built-in functions in snowflake used in numeric calculation, conversion, generation. 


  > - (+) : for addition of numbers
  >> Examples:
```sql

select 10 + 10;

---Answer: 20

select 10 as Eric, 20 as Rejoice, 30 as debby, 40 as miky, Eric + Rejoice + debby +  miky as answer;

--- the result is 100

```
  > - (-): Subtraction
  >> Example:
  ```sql
  select 50 - 40;
  ```
  > - (*) : for multiplication
  >>Examples:

  ```sql
  select 40 * 10;
---Answer: 400

  --- To calculate the circumference of a circle = 2πr
  select 10 as radius, 3.142 as pi, 2 * pi * radius as circumference;

  ---Answer :62.840

  --To calculate the area of a circle = (πr²)
  select 10 as radius, 3.142 as pi, pi * power(radius,2) as circumference;

  ---Answer : 314.2
  ```
 
 > - (/) : Division
 >> Example:

 ```sql
 select 10/20;
 ---Answer : 0.5000
 ```

 > - BODMAS
 >>Example:

 ```sql
 select ((10 * 40) + 10 - 30)/20;

 ---Answer: 19

 select 3 * 6 - 10 / 2 + 2;
 ---Answer : 15
 ```

 >- Power( ) function : used to raise a number to any number of multiple
 >> Example:

 ```sql
 select power(4,2) as four squared;


 select 10 as A, B as 4, A * power(A,B);


 ```
 > - Pi ( ) function = 3.14159
 >> Example:
 ```sql
 
 select 2 * pi()

 ```

> - Mod ( ) function : Gives the remainder of a division
>> Example:

```sql
select mod(70,9);

```
> - Sign( ) and abs( )function: The sign() function is used to determine if a number is positive or negative or zero. The abs( )function returns the absolute value
>>Example

```sql
select sign(-7.5233), abs(-7.5233);

```

When dealing with non integers (real numbers i.e decimal numbers ), the following functions apply
> - trunc( ) :  used to remove decimals
> - round up( ):used to round up to the nearest value
> - floor( ) :  used to round to the nearest lowerinteger
> - ceil( ) :   used to round to the nearest higher integer


Here's an example:
```sql
Select trunc(6.49), round(6.4955,2), floor(6.49), ceil(6.49)

```
![result](trunc,round,fxn.png)

# **Numeric Conversion**

numeric Strings can be converted to a numbers
> - imlicit conversion:  Here snowflake sees the need for the conversion and attempts to do so. It could return an error if the conversion fails

Heres an example
```sql
select 123.45 as real_num union  select '678.90' as real_num;

```

```sql
select 123.45 as real_num union select 'AAA.BB' as real_num;
```


> - explicit conversion :  Here you are able to specify that the string be converted using the following functions


>>>>>* The cast( ) function
>>>>>* The cast operator : :
>>>>>* A specific conversion function such as to_decimal ( )

Here's an example using all three options;
we will be converting a string into decimal value of type **number(7,2)** 7 stands for the whole number part of a decimal and 2 stands for the number of decimal places


```sql
Select cast(str.val as number(7,2)) as cast_val,
str.val::number(7,2) as cast_opr_val,
to_decimal(str.val, 7,2) as to_dec_val
from(values('15873.26')) as str(val);

```

NOte : The cast() function and the cast operator will return an error if the number contains any non numeric character only the to_decimal will not but with a formatting string

Here's an example;

```sql
select to_decimal(str.val,'$99999.99',7,2) as to_dec_val from (values ('$15873.26')) as str(val);

```

# **Number Generation**
For fabricating and generating all types of data
> - generator( ) function : A table function used to generate rows of data.
> - random( ) function : generates a random number for each row

Here's an example;

```sql

Select random() from table(generator(rowcount=>5));

```

> - seq1( ) function : Used to display sequence of numbers rather than a random set

Here's an example:

```sql

Select seq1() from table(generator(rowcount => 5));

```

Here's an example that generates date values corresponding to the first day of the month for every month in 2024

```sql

select to_date('01/' ||  to_char(seq1() + 1) || 
'/2024','DD/MM/YYYY') as first_of_month
from table(generator(rowcount => 12));

```

# **TEMPORAL DATA**

Date and Timestamp Generation

Dates and time can be generated using the following functions

* date_from_parts( )
* time_from_parts() 
* timestamp_from_parts( )

Here's an example:

```sql
select date_from_parts(2024, 9, 12) as my_date,
 time_from_parts(10, 22, 47) as my_time;


select timestamp_from_parts(date_from_parts(2024, 9, 12),
time_from_parts(10, 22, 47)) as my_timestamp;

```