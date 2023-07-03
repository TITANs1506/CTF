# Challenge:

Chơi bóng bàn cùng Ethical Ping Pong Club!

FLAG Format: EHC{XXX}

# Solution:

The challenge give us only a web to ping. Try 1.1.1.1 and 8.8.8.8 not thing happen. But we can exploit it as command injection. Try a few basic payload and we get something with `%0Aid`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/c8b0710b-51a3-4d53-89ed-3c46067cd532)

`%0A` in url encode is `\n` so i try url ancode with `space` but it didn't work. So i try `horizontal tab` url encode is `%09` and it's work 🌝

![image](https://github.com/Katsumi1012/CTF/assets/90083485/69d614a7-d229-43e5-9cc2-cc1d33b0f45a)

Let's dig into this server and see what we can get. Look around for a while, notthing special. This time i think how about print all file in the system with this payload `%0Acat%09/*` and woala 😄

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/1d3b8512-dd57-448e-9c08-4524ca725e98)

# ENJOY 🤡
