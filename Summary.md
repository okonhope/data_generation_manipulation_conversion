# **Character Data**
---------


>Another name for a character data is a **string**. A string is any data enclosed in single quote (' '). It could be a number or alphabet or both.


Lets have a look at some built-in functions in snowflake used in string generation,manipulation, etraction and searching 

> - (' ') - Single quotes : used to generate or create strings
> > Examples:  

```sql
select 'my name is hopelyn';

select 'I am 8 years old';

select 'a + 2';
```

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

> - ltrim( ), rtrim( ), trim( ) : for removal of spaces from the begining or ending of a string or from both ends.
>> Examples:

```sql
select ltrim(str.val), rtrim(str.val), trim(str.val) from values( '   goat   ');

```


