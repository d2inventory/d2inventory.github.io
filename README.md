# easy-login
Make Github easy to login aka FUCK 2FA!!!



A solution on how to get rid of the e-mail verification:

1. Set up 2FA with OTP (not SMS)  
Follow the instructions on https://github.com/settings/security until you have to verify your secret.  
(Make sure to use OTP and not SMS!)  
Keep this page open as we proceed to set up your Github homepage to provide the verification code.

2. Set up a Githup homepage  
https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
   
3. Have your 2FA code returned by your Github page  
See my repo: https://github.com/d2inventory/d2inventory.github.io  
All you need is an index.html that loads jsOTP.min.js  
(Original jsOTP.min.js is from https://github.com/jiangts/JS-OTP)  
and a script block that uses your secret to calculate the verification code.  
Replace "BL75FC6L7UNIN4DE" in index.html with your secret you got in Step 1
index.html:
```
    <html>
    <head>
        <script src='./jsOTP.min.js'></script>
        <script>
            const MY_SECRET = "BL75FC6L7UNIN4DE";
            document.write(new jsOTP.totp().getOtp(MY_SECRET));
        </script>
    </head>

    <body></body>
    </html>
```  
4. Get your verification code for Step 1 by visiting your own Github homepage  
(in my case d2inventory.github.io)

5. Finish Step 1 (saving recovery codes etc.)
6. On every login you can now get your 2FA code from your own Github page.  
So if you have access to Github you can always get the code and don't need no stupid e-mail login.



**Security implications:**
Well it renders the second factor in 2FA completely worthless as everyone can see your secret, it's public in the index.html
But we all already knew that and just want an easy user/pass login without no dumb e-mail verification.
