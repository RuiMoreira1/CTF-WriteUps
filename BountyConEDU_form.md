### **Team Name**

* AugustoCanario


### **Which terms are related to information security and bug bounties?**

- [ ] XML Extended Entry != XML Extended Entity
- [ ] Renaissance
- [x] Content Security Policy -> Stop Cross-site scripting, click-bot or code injection.
- [ ] Cross Script Leak != Cross-Site Leak
- [ ] User Traversal Attacks != Directory Traversal Attacks
- [ ] Insecure Deletion Object Redirect != Insecure Direct Object Reference
- [x] Server Side Request Forgery
- [ ] CCRF != CRF 
- [ ] Code Software Signing != Code Signing Certificate
- [ ] Arbitrary Intent Execution ? Android?
- [x] Side channel attack
- [x] Man in the disk (MITD)
- [ ] Certificate Spinning != Certificate Pinning 
- [x] IPC
- [x] Trust on first User (TOFU)
- [x] Insecure data storage 
- [x] ASLR
- [ ] Fizzing != Fuzzing
- [x] Out of band read != Out of band data
- [ ] Kernel Overflow ?! Buffer Overflow ??
- [ ] Memory spoilage ??
- [x] Segmentation faul
- [x] Use After Free
- [x] Null Pointer Derefence

### Case Study Of the Option Below must only choose 1 answer maximum 250 words

```question
	Web

	A security researcher is reporting that when uploading an SVG file containing javascript on Facebook the upload will fail, however they can still copy the preview link to the SVG and open it in a new window which results in the javascript being executed. 

	These preview links utilise the Blob URI Scheme (https://en.wikipedia.org/wiki/Blob_URI_scheme) which upload data locally to reduce overhead.
	 

	Does this pose a security risk?
	
```

Answer: The upload fails, probably due to the implementation of a Web Application firewall (WAF), that block possible payloads. However, the link can still be copied and opened in a new window, leading to JS code execution. But the links generated utilise Blob Uri Scheme, meaning that it is executing data that our browser has currently in memory, and does not refer to data existing on the host server. These URLs can only be used locally in the single instance of the browser and in the same session. 
	To conclude this does not pose a security risk, since the preview link to the SVG, leading to JS being executed, is only reachable locally, in the current browser session, not leading to any confidential information leakage or damages in the host server.

**Links:** 
* https://stackoverflow.com/questions/30864573/what-is-a-blob-url-and-why-it-is-used
* https://superuser.com/questions/948738/what-is-the-blobhttp-prefix-and-where-can-i-learn-more-about-this
* https://research.securitum.com/do-you-allow-to-load-svg-files-you-have-xss/

```question 
	A security researcher has reported that they can bypass Android permissions by using the following Java code in an exported Activity

	Intent incomingIntent = getIntent();
	String extraData = incomingIntent.getStringExtra("key");
	if (extraData.equals("notification")) {
	 Intent newIntent = new Intent();
	 newIntent.setData(incomingIntent.getData());
	 startActivity(newIntent);
	}

	Does this pose a security risk?
```

```question
	Native
	 

	A researcher reported that, when sending an image via a POST request to the /apply_img_filter API, if a query parameter named 'size' is increased the server will return some garbage data just after the processed image.
	Could this be a security issue ? If yes, describe how you would exploit it. If no, justify why not.

	We don’t know yet what is causing this, but we know that this service relies on some legacy C++ code.
```

Answer: When sending an image via POST request to the /apply_img_filter API, we are probably verifying the integrity of the uploaded image, to reduce the exposure to cyber attacks through, injection or running arbitrary code by image uploading (XML Injection, SQL injection...). Given that if the query parameter 'size' is increased and the server returns some garbage data after the processed image, and knowing that this services rely on C++ legacy code, we are probably experiencing more allocated memory than the real size of the image. Therefore returning garbage, server memory allocated right after the image, that contains information from the server that shouldn't be public, such as user sensitive information, even server private keys. Very similar to the Heartbleed Bug. 
	This could pose a security issue, and we could exploit it by changing the value of size, up to a limit that doesn't cause any crashes. And upload images, repeatedly, allowing us to retrieve different fragments of the server's memory each time. In the process, we can gain a wealth of sensitive data.  


