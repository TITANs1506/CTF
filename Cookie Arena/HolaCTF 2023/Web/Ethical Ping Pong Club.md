# Challenge:

Chơi bóng bàn cùng Ethical Ping Pong Club!

FLAG Format: EHC{XXX}

# Solution:

The challenge give us only a web to ping. Try 1.1.1.1 and 8.8.8.8 not thing happen. But we can exploit it as command injection. Try a few basic payload and we get something with `%0Aid`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/1f128e6a-90a1-4726-b3f1-65b2d077c512)

`%0A` in url encode is `\n` so i try url ancode with `space` but it didn't work. So i try `horizontal tab` url encode is `%09` and it's work 🌝

![image](https://github.com/Katsumi1012/CTF/assets/90083485/93846cc3-a3d2-4899-8659-0240d51e3fdd)

Let's dig into this server and see what we can get. Look around for a while, notthing special. This time i think how about print all file in the system with this payload `%0Acat%09/*` and woala 😄 we get the Flag🚩

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/9bf86fee-5c9c-4b81-9ae3-718b99a23da9)

# ENJOY 🤡
