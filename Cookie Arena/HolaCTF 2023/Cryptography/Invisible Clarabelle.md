# Challenge:

Mrs. Clarabelle gave me this code but I don't know how to solve it. I spent almost 2 days 16 hours thinking. Maybe I need a quieter space so I can think of a solution. How about you?

FLAG Format: EHC{XXX}

# Solution:

File we get seem like `base64` due to the end with `=`. Decrypt it and we get the weird output:

![image](https://github.com/Katsumi1012/CTF/assets/90083485/06d52250-53ea-440b-8a2e-b60296cdb129)

Search `Mrs. Clarabelle` we got the cow in a animation movie, that a big hint. Let see they have any decode about cow?? They actually have the `Cow code` 😵‍💫. Let's try to decrypt the output with `Cow code`

![image](https://github.com/Katsumi1012/CTF/assets/90083485/1f3f43fb-41ef-4c4e-9b92-3b347367613f)

Nothing there isn't it??

![image](https://github.com/Katsumi1012/CTF/assets/90083485/bdf238eb-603c-4825-8f98-a573e01b3af1)

Or maybe it `invisible`❔. Copy the `invisible` output to dcode.fr to detect encryption and they detect a `Whitespace Language` 🙄 

![image](https://github.com/Katsumi1012/CTF/assets/90083485/67a07b70-5370-4544-8022-5b92fb37019c)

Let try with `Whitespace Language` and it work!! We get the flag 🚩

![image](https://github.com/Katsumi1012/CTF/assets/90083485/69febc32-9582-4198-8410-ec9908d45a6e)

# ENJOY 🤡
