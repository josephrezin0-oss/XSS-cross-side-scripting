# XSS LABS

## Lab:1  Reflected XSS into HTML context with nothing encoded  

This lab contains a simple reflected cross-site scripting vulnerability in the search functionality.  
To solve the lab, perform a cross-site scripting attack that calls the alert function.  
```
payload: <script> alert("hacked") </script>
```


The HTML <script> tag is used to embed executable code (typically JavaScript) within an HTML document or to link to an external script file  
External Scripting: You can link to a separate JavaScript file using the src attribute.  
eg: 
<script src="path/to/your/script.js"></script>  

* Reflected XSS: This occurs when an application receives data in an HTTP request (like a search query) and immediately includes that data in the response. The script "reflects" off the server back to your own browser rather than being permanently stored.

* Input is being placed directly between standard HTML tags ```(e.g., <div>YOUR_INPUT</div> or <h1>YOUR_INPUT</h1>).  ```
Nothing Encoded: This is the critical vulnerability. The website does not sanitize or "encode" special characters like < or > into safe formats like &lt; and &gt;. This allows the browser to   interpret your input as actual HTML code rather than plain text  

The <script> Tag: In HTML, this tag tells the browser: "Stop reading this as text and start executing it as JavaScript code". In XSS, it is the primary container used to smuggle executable code onto a page.
The alert() Function: This is a built-in JavaScript function that creates a pop-up dialog box in the browser with a specified message.  

Result: If the page is vulnerable, the server will send back the HTML containing your tag. Your browser sees the <script> tag, stops rendering the page, and executes the alert() function, popping up your message  
