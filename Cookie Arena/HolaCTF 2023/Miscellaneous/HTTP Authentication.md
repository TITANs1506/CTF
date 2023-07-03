# Challenge:

Fame or Frame?

FLAG Format: EHC{XXX}

# Solution:

Open the challenge's file, we got something that looks like hexa table when open file in HexEditor

![image](https://github.com/Katsumi1012/CTF/assets/90083485/4d9bbc8a-0d8b-4b1b-87a0-5e7267559eb2)

Decode on cyber chef with recipe is `From Hex` and got this good-looking output seems like header of a http request

![image](https://github.com/Katsumi1012/CTF/assets/90083485/6d375a32-825a-46c9-bd6a-b311d5068f28)

In the `Authorization` we get the suspicious code seem to be `base64`. Decode it `From base64` and we get the flag🚩

![image](https://github.com/Katsumi1012/CTF/assets/90083485/c59a472c-49c2-4a51-b23e-1497663c6f02)

# ENJOY 🤡
