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

Answer: The upload fails, probably due to the implementation of Content Security Policy (CSP), that block that JS code execution. However, the link can still be copied and opened in a new window, being JS code executed. But the links utilises Blob Uri Scheme, meaning that it is executing data that our browser has currently in memory, and does not refer to data existing on the host server. These URLs can only be used locally in the single instance of the browser and in the same session.

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
``



