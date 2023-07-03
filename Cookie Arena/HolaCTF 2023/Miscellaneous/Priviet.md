# Challenge:

Welcome to HOLA CTF

FLAG Format: EHC{XXX}

# Solution:
From the beginning, the title is "Priviet", similar to привет (privet), which means "Hello" in Russian. And the protocol that has "Hello" in its packet is TLS, so we can start investigating this protocol first.

We got a .pcap file. Open with `WireShark`, click on 1 packet and choose `Follow TCP Stream`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/e509c3bc-c3da-403f-9f57-d374930805fa)

Check `Stream` and in stream 3 we saw `This is flag` in a `TLSv1.3` packet

![image](https://github.com/Katsumi1012/CTF/assets/90083485/77a399dd-0e45-4246-99b6-d495eee5d1b0)

Using ROT on CyberChef and we get the flag 🚩

![image](https://github.com/Katsumi1012/CTF/assets/90083485/f93d38f2-defa-487e-a5f0-5b3a92550309)

# ENJOY 🤡
