# ATTACKING WEB APPLICATION WITH COMMMON VULNERABILITIES

## Objective
To simulate real-world scenarios and enhance proficiency in identifying and exploiting common vulnerabilities in web applications, thereby strengthening defensive strategies and fostering a proactive security posture


### Skills Learned
- Finding subdomian with asset finder.
- XXS Cross site scripting (dom,store and reflected).
- SQL injection using Union select and blind.
- Command injection.
- Insecure file Uploads.
- Brute force
- Attacking MFA

### Tools Used
- Asset finder for finding subdomain
- local website lab for xxs,MFA,bruteforce,Insecure uploads.
- Burpsuite for identifying POST request,bruteforce attacks from localhost and SQLmap  for SQL injection.
- https://appsecexplained.gitbook.io/appsecexplained/common-vulns/injection/command-injection  a reference book for injections
- Hydra  used for cracking hashes from users-table in the database
- Ffuf which aided cracking passwords as another option

## Steps :  Finding subdomain  with Assetfinder
-  First installed the assetfinder from github to pc
-  <img width="434" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/a4f99347-8c8a-4b04-bd7d-7cefeb3717fd">
- Next  was setting assetfinder with the domain name tesla.com which is open for bounty hunting and the results given show all tesla.com related sites
- <img width="417" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/f0e72933-9122-432b-aafb-338a7155ca6d">
- creating a file to store the above info of tesla subdomain thus tesla-subs.txt
- <img width="436" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/8a63a6ff-3c22-47b7-802b-32d1c08c3f8f">
- Creating a file called run.sh to enhance automation based on finding the subdomain after creating and modifying it, will run it with command chmod +x run.sh which will collect subdomains ----  under url /recon/final.txt which was created by run.sh code
- <img width="434" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/8fc0a877-92dc-4076-9274-24202f27ed44">
- Run the run.sh file
- <img width="433" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/122132db-7d32-4368-bddd-f739a70ae9d8">
- Running the run.sh through tesla.com website it gives a message of 'harvesting' which is generated from run.sh and in the background it creates a URL recon/final.txt where the new - --- 
  harvested subdomains are stored.
- <img width="430" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/62c13086-d5a8-4bc7-a3b0-799bb3034747">
- Now you can view the output
- <img width="428" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/c8bb1f0a-b0c1-46ed-965b-87f908dc573e">
- To view the file, call the cat command
- <img width="251" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/eff38785-41ee-47b5-861a-1899e726eedf">

## Steps :  XXS Cross site scripting: DOM
- To identify the xxs type, I used the website source code to check if any requests were available and returning from the server
- <img width="519" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/436e8b34-090c-4a9f-9440-651a4b2b29fe">
- Next, running a basic script to check for output and return thus script. 
- <img width="496" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/54c1882e-008a-4b22-888b-52f323ccbf66">
- I then uploaded an image using img src=x onerror="prompt(1)"
- <img width="551" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/90e724de-8263-40d4-abd0-cfafd75aecbe">
-  The image failed to load however I got a notification implying liability to an attack
- <img width="588" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/ecedf04e-fabd-44d6-b712-32de69c38843">

## Steps :  XXS Cross site scripting: Stored
- Pro tip, whenever testing for XXS its significant to test HTML injection and in this case, we test if the header test will be returned thus html injection applicable in this case as it gives feedback
- <img width="390" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/fa6ebbd9-e885-44b9-8cc7-68df9114b65d">
- Next , exploring the vulnerability
- <img width="572" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/fa82d52e-a208-4dc3-baab-0dfb68dee9ce">
- The output throws a notification an implication of liability to attack
- <img width="594" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/55760d97-6872-4f89-a27a-04fe6931234f">
## Steps :  SQL Injection Union select
- To begin with SQL injection, 1=1 is a statement that will always RESULT true therefore i started with it to call for all the data in the database.
- <img width="439" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/d420faea-63ca-4af1-82d4-f62d9bcefdf1">
- Union select is used to combine statements into one and in this case, called jeremy among various tables in the database
- <img width="396" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/d4866c88-0c66-4289-b7fa-d63c76c5a88c">
- Similarly, I also called the column names from the tables
- <img width="520" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/44dc437e-9b24-4f01-89dd-775e4f1cc898">

## Steps :  SQL Injection (Blind)
- In this case both the username and password are given
- <img width="631" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/6dc83893-74ba-44a2-b54b-0d611d949abe">
- Using burpsuite, i was able to identify the Post request, set cookies and username and password which i used to attempt to login
- <img width="328" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/d007a83e-7c30-4e0b-9420-12c1183f85af">
- Its important to notice the welcome page as well as the content length of the page
- <img width="214" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/15024120-7c29-417d-bd66-4b1790ee4717">
- To begin the injection tests, a post request was sent to repeater and  reapeater enables modification of comparisons as requests are sent. for example I change the password , however its important to watch out for the content length as it determines if its sucess or validity and in this case,  experiment was invalid
- <img width="372" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/6c80e89b-c315-4c4c-aeb0-465172723f5f">
- <img width="283" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/e57043e7-934b-4e6e-8dbc-13b1638c5c5c">
- To enhance the attack, performing checks by encoding the username coresponding with the password
- <img width="304" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/7826a912-827b-4511-8cca-58218d6c6ae5">
- Similarly , created a request.txt file of RAW, which I was able to run using sqlmap which showed both username and password as non injectable
- <img width="254" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/1aa60218-8b78-48c8-aba3-53c2010a5ff8">
- <img width="365" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/f7eb3fa4-6a5d-4b16-ad1a-e95dedd7a2b9">
- Thw solution here was using session cookies, therefore if any letter is added to session cookies, the content length changes and you wont find a match of the home page
- <img width="247" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/7bbf0460-5d19-4f04-8183-3ce6052cdc08">
- To resolve the conflict, i used the 1=1 (alway true statement) hence adding the statement to session cookies
- <img width="308" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/12c30704-68d0-428a-8593-8ef4491f509f">
- Next, was using substrings in substitute to the above and it works perfectly
- <img width="289" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/0c500d64-ba35-492f-8d52-7bcede2f26e8">
- Finding the version of the database using substring, works perfectly as well
- <img width="400" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/7bf4d13c-735e-4e5d-997c-286b960c50cc">


## Steps :  Command Injection

- A reference book  I used here was appsecexplained https://appsecexplained.gitbook.io/appsecexplained/common-vulns/injection/command-injection thus some injection commands begin with ;ls -la etc, in this case i run a website through the lab and try to pop a shell by performing a grep based on whoami or hostname of the website
- <img width="480" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/d60a1549-2177-4745-8298-890e348d9b43">
- At this point, its not providing the whoami information therefore adding http echo will call out the required data
- <img width="459" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/990d74c7-ab5c-497a-b9ca-e38d0c89304a">
- Next filtering the view to only  whoami  by using asd for output
- <img width="309" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/4fa4593f-b8bd-4f91-a8bb-bccdeef55bfb">
- Poping a shell identify the bash with (bash;asd). and  reverse shell cheatsheet https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#bash-tcp  finding this bash
-  <img width="312" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/1dc42dbb-cab5-40c0-b088-4affc35e14b4">
- Then setting up a listening port
- <img width="305" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/e9f5a4ea-3ec2-4dc0-80c5-108fcd81481a">
- Using php reverse from reverseshell cheatsheet to pop a shell connected to  port listening and updated the ip and port to match my personal network and the shell was succesfull
-  <img width="298" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/e3a07efb-9ee0-4263-aec5-1e6fa5e13d91">
- <img width="327" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/519c3e04-73b5-4cf1-981b-4e7bc02428d7">
- <img width="292" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/830d3623-d45c-43a5-9a60-c45916cb5402">
- <img width="291" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/6c9ae258-601f-4f46-80fc-e1918824e7e5">



























   

