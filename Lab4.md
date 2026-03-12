## Lab:4 DOM XSS in innerHTML sink using source location.search  




The document.getElementById() method is "tag-blind." It only cares about the ID attribute, not the type of tag. As long as the ID matches, it will work on almost any HTML element.
When you use the = sign with .innerHTML, you are telling the browser: "Throw away everything currently inside this tag and put this new stuff in instead"  
Existing Tag: <div id="myDIV">...</div> stays on the page.  
Contents: Only the stuff inside those brackets is replaced by your text variable.  

Summary of the Flow :
Browser reads the HTML and sees a <div> with id="myDIV".
JavaScript uses getElementById to "point" at that <div>.
JavaScript uses innerHTML = to wipe out "Old content here" and write "Hello Dolly".
Result: The user sees "Hello Dolly" on the screen where the div used to say something else. 
Crucial Note on Attacks: This is why it's dangerous. If the text you put in is ```<img src=x onerror=alert(1)>```, the browser "swaps" the content and then immediately tries to "read" that new HTML, which triggers the malicious script.  




<img width="936" height="281" alt="image" src="https://github.com/user-attachments/assets/49ab98a1-947b-4c2a-99ca-012e51cfbf00" />

From the source code it is evident that the .innerHTML function is being used, preceded by getbyID and folowed by the '=' operator which sets the value of that particular id att
ribute in whatever tag it exists, fact is explicitly removes the entire bocy content inside it and writes the assigned value coming from the query var,  
and suppose if my query has the value <img src=x onerror=alert(1)> what would the effective tag of the searchMessage look like.
```
<h1>
  <span>0 search results for '</span>
  <span id="searchMessage">
      <img src="idk" onerror="alert(1)"> 
  </span>
  <span>'</span>
</h1>
```
This is what would effectively happen when input is given  
the script inisde the span tags would be executed.  


The <span> tag is an inline element, which means it flows with surrounding text and doesn't force a line break before or after itself

he doSearchQuery function takes a value from the query variable and assigns it directly to the innerHTML of the element with id="searchMessage"
"Sink": The innerHTML property is what's known as a sink. It doesn't just put text between the tags; it tells the browser to parse and render that text as HTML code.

 the browser creates a new <img> element inside your <span> tags. Because the source x is invalid, the onerror event fires immediately, executing the attacker's JavaScript.


set itself right of the innerhtml function



here what is happening is that the input goes directly between the openning and closing scan tage and that is executed if an img source is placed right? but then here innerHTML plays the role of putting the input between the tag
