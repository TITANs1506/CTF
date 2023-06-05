#Password Disclosure
First, i came into page where i can see 2 function is /login and /debug
Let's take a look at debug first
In here i see php python code using flask with interesting function used to create sample database users:

Scroll down a little bit we saw a function call /reset_password use 2 methods: GET, POST

Nothing else to see here so i tried to login with user account expose in debug and it got no problem. When catch the request in Burp, i see the cookie session and thought maybe i can use JWT to change the session to admin because some first value of the cookie is same to every account but JWT can't define what decoce they use to it took me back to the function /reset_password. It took me a while because when changing password, they load current user password, when i change and submit it said complete but the pass still the same 🤣.
Look back at the description of the CTF, they point out the username value so i try when changing so i tried add more parameter in the url &username=admin and look at the response we get the value of the admin password
