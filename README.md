# Hack the Box_Inject.htb

 - [ ] IP Address: 10.10.11.204
 - [ ] Host Name: inject.htb

# LFI-Vulnerability_01  
**Local File Inclusion (LFI)** allows an attacker to include files on a server through the web browser. This vulnerability exists when a web application includes a file without correctly sanitising the input, allowing and attacker to manipulate the input and inject path traversal characters and include other files from the web server. 
## Steps: 

 **1. Upload the image file**
 
 <img width="796" alt="image" src="https://user-images.githubusercontent.com/65080702/232567902-2c343c2a-b59e-4d6f-9cca-bf6db34e1da6.png">
 
 **2. Intercept the Request from Burp**
 
 <img width="718" alt="image" src="https://user-images.githubusercontent.com/65080702/232568107-e2d257b5-1ffd-459d-ab45-4fa79c7b5cb9.png">

**3. Next copy the url and enter the below command:**

```curl http://inject.htb:8080/show_image?img=malicious.jpg | jq```

<img width="844" alt="image" src="https://user-images.githubusercontent.com/65080702/232568925-be4bcf49-eb33-4308-84e1-ba553e2e5f41.png">

**4. We got the location of file's upload so, we can try to get the root folder access using below command:**

``../`` 

**5. Change the request into burp and try to access the root file**

<img width="635" alt="image" src="https://user-images.githubusercontent.com/65080702/232574833-dbb25a8d-de33-44dd-bc5a-debff4a74b69.png">

**6. Get the sensitive information using the **LFI****

- [ ] User name and password 

<img width="694" alt="image" src="https://user-images.githubusercontent.com/65080702/232574084-0d5348fa-f76b-4c2e-837f-10b4595714bb.png">

- [ ] server information(vulnerable springframework,java-version etc.)

<img width="743" alt="image" src="https://user-images.githubusercontent.com/65080702/232580003-459316aa-34d3-43b2-908d-21e56d324020.png">



**Successfully Exploit LFI**


