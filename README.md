# ATTACKING WEB APPLICATIONS WITH COOMMON VULNERABILITIES

## Objective
To simulate real-world scenarios and enhance proficiency in identifying and exploiting common vulnerabilities in web applications, thereby strengthening defensive strategies and fostering a proactive security posture


### Skills Learned
- Finding subdomian with asset finder.
- XXS Cross site scripting (dom,store and reflected.
- SQL injection using Union select and blind.
- Command injection.
- Insecure file Uploads.
- Brute force
- Attacking MFA

### Tools Used
- Asset finder for finding subdomain
- local website lab for xxs,MFA,bruteforce,Insecure uploads.
- Burpsuite for identifying POST request,bruteforce attacks from localhost and SQLmap  for SQL injection.
- https://appsecexplained.gitbook.io/appsecexplained/common-vulns/injection/command-injection  a reffernce book for injections
- Hydra which i used for cracking hashes from userstable in the database
- ffuf which aided cracking passwords as another option

## Steps :  Finding subdomain  with Asset finder
-  First installed the assetfinder from github to pc
-  <img width="434" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/a4f99347-8c8a-4b04-bd7d-7cefeb3717fd">
- Next i was able to run assetfinder with the domain name tesla.com which is open for bounty hunting and the results given show all tesla.com related sites
- <img width="417" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/f0e72933-9122-432b-aafb-338a7155ca6d">
- creating a file to store the above info of tesla subdomain thus tesla-subs.txt
- <img width="436" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/8a63a6ff-3c22-47b7-802b-32d1c08c3f8f">
- Creating a file called run.sh to enhance automation based on finding the subdomain after creating and modifiying it, will run it with command chmod +x run.sh which will collect subdomains ----  under url /recon/final.txt which was created by run.sh code
- <img width="434" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/8fc0a877-92dc-4076-9274-24202f27ed44">
- Run the run.sh file
- <img width="433" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/122132db-7d32-4368-bddd-f739a70ae9d8">
- Notice i run the run.sh through tesla.com website it gives a massagge of harvesting which is generated from run.sh and in the background it creates a URL recon/final.txt where the new - --- 
  harvested subdomains are stored.
- <img width="430" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/62c13086-d5a8-4bc7-a3b0-799bb3034747">
- Now you can view the output
- <img width="428" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/c8bb1f0a-b0c1-46ed-965b-87f908dc573e">
- To view the file, call the cat command
- <img width="251" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/eff38785-41ee-47b5-861a-1899e726eedf">

## Steps :  XXS Cross site scripting: DOM
- To identify the xxs type, i used the website source code to if any requests were available and returning from the server
- <img width="519" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/436e8b34-090c-4a9f-9440-651a4b2b29fe">
- Next, running a basic script to check for output and return thus script(open) prompt(1) script(close) and that didnt work
- <img width="496" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/54c1882e-008a-4b22-888b-52f323ccbf66">
- will now try to uplaod an image using <img src=x onerror="prompt(1)">
- <img width="551" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/90e724de-8263-40d4-abd0-cfafd75aecbe">
- ones it runs the image fails to load however i got a notification implying liability to an attack
- <img width="588" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/ecedf04e-fabd-44d6-b712-32de69c38843">

## Steps :  XXS Cross site scripting: Stored
- Pro tip, whenever testing for XXS its significant to test HTML injection and in this case, we test if the header test will be returned thus html injection applicable iin this case as it gives feedback
- <img width="390" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/fa6ebbd9-e885-44b9-8cc7-68df9114b65d">
- Next , am exploring the vulnerability
- <img width="572" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/fa82d52e-a208-4dc3-baab-0dfb68dee9ce">
- The output thhrows a notification thus a good sign of reliability to attack
- <img width="594" alt="image" src="https://github.com/chromosems/attacking-web-application-with-common-vulnerabilities/assets/44053943/55760d97-6872-4f89-a27a-04fe6931234f">










   

