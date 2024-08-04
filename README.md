# Security Monitoring Data Analysis
To Check the ability of a network in collecting the security monitoring data , and to identify weaknesses in their network or systems to improve its security posture.

**Analyzing the access log data:**

1. Logged GET requests:
   Used awk to extract Ip addresses and corresponding request methods and then used pipe to send the output into grep to select the requests having GET in the access log and then used pipe again to wc command with -l option to count the total number of extracted GET request in the file.

   ![image](https://github.com/user-attachments/assets/37fb4da9-b2b4-4319-83bf-dda7f6beff5d)

2. Unique status codes returned by the server:
   Used awk and set the delimiter to ‘ “ ‘ to extract the third field which would be response status code from the server and the file size. Then we used pipe to output this to another awk to extract the status codes and used sort, uniq commands to know the unique codes, their individual count and total count of unique codes sent by the server.

   ![image](https://github.com/user-attachments/assets/a11e7012-fdbf-4beb-bf37-a32d783070e0)

3. Largest response body in bytes:
   In this case, we used awk and set the delimiter to ‘ “ ‘ to extract the third field which would be response status code from the server and the file size. Then we used pipe to output this to another awk to extract the returned object size and then used sort, uniq commands, tail commands to extract the largest response body from the server.

   ![image](https://github.com/user-attachments/assets/f4a9b5ae-41f3-474b-9428-c1af10df4fa5)

4. HTTP tunneling attempts:
   HTTP CONNECT method is the most used http tunneling method, so used AWK command to extract the request field and piped the output to grep command to find the string CONNECT and wc command to count the attempts. We had 10 http tunneling attempts. This can also be checked in VSC tool.

   ![image](https://github.com/user-attachments/assets/3bfb22dc-9806-47c4-a884-a4f987a814cc)

   ![image](https://github.com/user-attachments/assets/e8777b26-2ce1-4cde-a71c-bdfe053debd8)


5. Invalid request lines containing raw binary data:
   There are 11 invalid request lines which contain binary data, with status code 400. The user agent field is empty for all these invalid requests, which could be a potential sign of malicious traffic. AWK and Grep commands are used to extract this data as shown below.  
   ![image](https://github.com/user-attachments/assets/a5da8650-4a2d-4f7c-8200-80a520dc2b6c)

   ![image](https://github.com/user-attachments/assets/c8e6617c-6bd2-42a9-9203-290c4d71277a)

6. Unique user agents:
   There are a total of 55 unique user agents in this log file. We set the delimiter to ‘ “ ‘in awk and extracted the user agent field, and by using grep we excluded missing user agents, and then extracted the count of unique user agents piping the output to uniq and wc commands.

   ![image](https://github.com/user-attachments/assets/aa7fec79-8a0f-44a1-be8c-2b82178cab8c)

7. IP address which attempted to exploit the shellshock vulnerability:

   ![image](https://github.com/user-attachments/assets/34fd49a4-6c4b-4109-83ab-20179ef0f07e)

8.IP address that rang at the doorbell:
  ![image](https://github.com/user-attachments/assets/e0f454f0-57c4-4b42-b8f8-344b2e04be50)

9.IP address from which the server got more traffic from:
  ![image](https://github.com/user-attachments/assets/29717423-49a7-4eaa-948a-d4d9765e3073)

**Conclusion:** Network could be exposed to some critical attacks. There are some known critical vulnerabilities such as CVE-2020-8515, CVE-2014-6271, Malware/Ringing.at.your.dorbell with which an attacker can gain access to the machine executing arbitrary commands with root privileges.There is another vulnerability CVE-2020-8958 in access-1.log which allows the attacker to execute arbitrary OS commands in the destination Ip address field.  There are repetitive requests from a specific Ip address requesting the instance identity document, which can be a sign of a security breach attack.There are some malformed requests in the log files which attackers might use to probe vulnerabilities in the server.Missing user agents and agents which could be acting as malware agents are found in the logs compromising server security. 







   

   


   

   


