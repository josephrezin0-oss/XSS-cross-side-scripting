## Lab:3

 document.write() referred to as a sink—a place where untrusted data "lands" and gets executed

```
payload: '">');<script>alert(1)</script>

```

On research, DOM changes (including document.write()) are per user session, not global.  
Anything that modifies the DOM in the browser only affects:
The single user’s browser tab
Their loaded page instance
Their session only  
Because the DOM lives:  
Inside the user's browser memory  
NOT on the server  

What document.write() Actually Does: The current document stream being rendered in THAT browser
Server HTML file = blueprint
Browser DOM = personal copy of blueprint

JavaScript edits = writing on your copy only  


document.write() is a JavaScript DOM method that writes text or HTML directly into the webpage while it is being loaded  
It inserts content into the browser’s current HTML parsing stream.  
Think of it as  
“Inject this content into the page right now during load.”    

Browser reads HTML
→ encounters <script>
→ runs JavaScript
→ document.write injects content
→ browser continues parsing 

document.write() works correctly only while the page is loading.

KEYNOTE: Because document.write() doesn’t insert “text” — it inserts “HTML to be parsed.”
That one difference explains everything. 
It happens because document.write() feeds the string into the HTML parser, not the text renderer — so tags become real elements and scripts execute
document.write() always treats input as HTML first — not as guaranteed plain text.  
string → HTML parser → no tags found → text node → display


<img width="863" height="192" alt="image" src="https://github.com/user-attachments/assets/d74255f4-57fe-4252-9418-b36dc46115f0" />

Now understanding all these facts, on viewing the source code i found out that this is how the 'document.write' function is being used in this lab,  
the query is being pasted into the image path and so if simply a script attack is tried, it will simply fail because it just fails to fetch such a result because it stays trapped inside the  
src attribute as part of the file path    
but then analyse it and close the desired opening delimitters of the img src path check and simiply inside the document.write itself we forge the new ;   
script using the script tags,  and use the alert finction as that is what the level requires us to do.  

So keenly craft a payload so as to close the required openers and then follow it with the script.  
That should so it for the level.  


```
payload: '"><script>alert(1)</script>
```
location.search:  
Whatever you typed after search= in the URL is now stored in the query variable, ready to be passed to the dangerous document.write() sink.  
<img width="618" height="60" alt="image" src="https://github.com/user-attachments/assets/97345a02-c945-4c5d-830b-04531109f95f" />     
^ here is an example of The console tab where the window.location returns ths following value.  


  
<img width="876" height="605" alt="image" src="https://github.com/user-attachments/assets/1b79f8ae-f847-4c17-9d18-e1579b4e9fd1" />
Yes, you can definitely select only a part of a string by using built-in JavaScript functions. Since window.location.search is a string property, you can chain these methods directly to it to "cut" out exactly what you want.  
window.location.search.substring(1) etc   

finally i dont exactly understand the usage of alias "sink" for the document.write function
In web security, especially XSS analysis, we track data flow:
User input → travels through code → ends somewhere dangerous
That “dangerous endpoint” is called a:
Sink — a place where data gets executed, rendered, or interpreted in a risky way.  
A function is called a sink when:
It sends data into an interpreter (HTML / JS / CSS / URL) that can change behavior or execute code.



window.location.search: Gets the whole string after the ?.
.get('search'): Grabs the specific value you want from that string.


?search=hello, the built-in .get() function returns the string "hello"  




why because found out that this was a function that was being called effectively,  

DOM-Based XSS: This is the most common vulnerability involving this function. If a website takes a part of the URL (like a search term) and passes it directly into document.write() without sanitizing it, an attacker can inject a script.
Example Payload: If the site code is document.write("Results for: " + query), an attacker could set the query to:
"><script>alert(1)</script>
The browser would then write this directly into the HTML, causing the alert to trigger
