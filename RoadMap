

# XSS Learning Roadmap Using PortSwigger Web Security Academy

## 1. Understanding the Fundamentals of XSS

The learner should begin by understanding the basic concepts of Cross-Site Scripting.

Topics to learn:

* What XSS is
* How browsers execute JavaScript
* Types of XSS:

  * Reflected XSS
  * Stored XSS
  * DOM-based XSS
* How user input flows from **source → sink**

Initial labs to complete:

* Reflected XSS into HTML context
* Stored XSS into HTML context
* DOM XSS using `document.write`

Goal:
The learner should understand **how unsanitized user input can lead to JavaScript execution in a browser**.

---

# 2. Practicing Reflected XSS

After learning the basics, the learner should practice **reflected XSS vulnerabilities**, where malicious input is reflected immediately in the response.

Skills developed:

* Identifying injection points
* Breaking out of HTML contexts
* Using JavaScript event handlers

Recommended labs:

* Reflected XSS into HTML context
* Reflected XSS into attribute context
* Reflected XSS with event handlers
* Reflected XSS inside JavaScript string
* Reflected XSS with HTML encoding

Example payloads used during practice:

```
<script>alert(1)</script>
<img src=x onerror=alert(1)>
```

Goal:
The learner becomes comfortable identifying **reflected injection points and executing simple payloads**.

---

# 3. Practicing Stored XSS

Next, the learner should move to **stored XSS vulnerabilities**, where malicious scripts are stored on the server and executed when other users view the page.

Skills developed:

* Persistent payload injection
* Exploiting user-generated content fields
* Understanding the impact on multiple users

Recommended labs:

* Stored XSS in blog comments
* Stored XSS in message boards
* Stored XSS with basic filtering

Example payload:

```
<img src=x onerror=alert(document.cookie)>
```

Goal:
The learner understands **how attackers exploit stored content to target multiple victims**.

---

# 4. Learning DOM-Based XSS

Once server-side XSS types are understood, the learner should focus on **DOM-based XSS**, which occurs entirely in the browser through client-side JavaScript.

Skills developed:

* Identifying DOM sources
* Identifying dangerous sinks
* Understanding client-side JavaScript vulnerabilities

Common vulnerable code example:

```
document.write(location.search)
```

Example payload:

```
?search=<script>alert(1)</script>
```

Recommended labs:

* DOM XSS in `document.write`
* DOM XSS in `innerHTML`
* DOM XSS with jQuery selectors

Goal:
The learner learns to **analyze JavaScript and trace data flows in the browser**.

---

# 5. Learning XSS Filter Bypass Techniques

After gaining experience with standard XSS attacks, the learner should practice bypassing input filters.

Skills developed:

* Payload obfuscation
* Using alternative HTML tags
* Exploiting weak filtering mechanisms

Example payloads:

```
<svg onload=alert(1)>
<img src=x onerror=alert(1)>
```

Recommended labs:

* XSS with blocked angle brackets
* XSS with HTML encoding
* XSS with restricted tags

Goal:
The learner develops the ability to **bypass basic defenses and exploit filtered inputs**.

---

# 6. Advanced XSS Techniques

At this stage, the learner should move on to more advanced vulnerabilities that simulate real-world bug bounty scenarios.

Topics include:

* XSS in JavaScript contexts
* Template literal injection
* Content Security Policy (CSP) bypass
* Framework-related XSS

Example payload:

```
"><svg/onload=alert(1)>
```

Goal:
The learner gains experience exploiting **complex application logic and modern defenses**.

---

# 7. Expert-Level XSS Exploitation

Finally, the learner should attempt the most difficult labs.

Topics include:

* CSP bypass techniques
* Mutation-based XSS
* Sandbox escape
* Prototype pollution leading to XSS




