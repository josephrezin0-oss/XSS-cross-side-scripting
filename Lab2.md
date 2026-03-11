## Lab:2 Stored XSS into HTML context with nothing encoded  
<img width="837" height="100" alt="image" src="https://github.com/user-attachments/assets/5fb18251-0e7d-4f53-877e-874a6f32b8fe" />


To create a Stored XSS attack (also known as Persistent XSS), you use the same basic payload—<script>alert(1)</script>—but you change where you submit it.   
Unlike Reflected XSS, where the script is bounced back to you immediately, Stored XSS happens when your script is saved to the website's database permanantlybecause it isn't properly sanitizing (cleaning) the input.  
Every time any user (including an admin) visits the page where that data is displayed, their browser retrieves your script from the database and executes it automatically  

```
payload: <script> alert("hacked") </script>

```
This lab is of the same payload except the workflow of the attack is different.  
