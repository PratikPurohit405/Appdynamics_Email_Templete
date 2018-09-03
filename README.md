Appdynamics Email Template

Requirement: - One Template for One application.

Description: 
  
This Email Template is design to work with below health Rules :
1.	Infra Alerts (CPU, Memory, Heap, GC, Connection pool, Threads, Disk )
2.	Agent Availability 
3.	Process Monitoring
4.	URL Monitoring
5.	SQL Monitoring 
This template is design and develop in order to save time in creation and maintaining of multiple Health Rules. 

Pre-Requisite: 

•	Health Rule :
1.	Recommended to use one Health rule of one type for all the nodes (e.g. Memory utilization of all nodes should be in one HR).
2.	Name: HR name will be displayed as event name. (e.g. Heap utilization)
For process monitoring and URL monitoring, HR name should contain “Process :” and “Page :” respectively. For SQL monitoring HR name “<Event message>: SQL” format should be followed. For Agent availability HR name should contain “Agent Availability”.
For Disk alerts HR name should contain ‘Disk’.
Note:- all text are case sensitive. 
3.	Health Rule affect: Try to select node Specific. (all nodes in the application/these specified nodes etc)
4.	Condition: Unit will be captured from event message so it is mandatory to put unit in condition textbox. 
Format to put unit is “condition 1 [unit=GB]”
Note : text box should contain “[unit=ms]”  if no unit is mentioned then blank unit value  will be displayed on Email. Hence for alerts which does not have any unit, don’t put “[unit=]” in that text box 
 
•	Changes in Template 
1.	 “#set($separator_Between_hostname_and_JVM='-')”
This variable is used to separate IP and JVM name/Service name from node name.
Value of this variable is the separator between IP and name. (Eg. ‘_’ for java application or ‘–‘ for .net application) it is totally depend upon the node name, hence check node name and then set its value.
Note :- Recommended to give <IP>_<JVM> name as node name.
2.	“#set($Take_hostname_from_Health_Rule_sparator='-')”
This variable is used take IP from health rule. If you want to get IP from your health rule then separator between event message and IP is this variable 
(Eg. If hr name is Heap Utilization - 10.20.33.173 then value of this variable is ‘-’) 
3.	“#set($Take_hostname_from_Health_Rule='0')”
If you desperately want to take IP from health rule and not from node then this variable come into the picture.
Default value for this variable is ‘0’ if you want to take IP from HR then change it to ‘1’
 
Conditions
1.	Case 1 - Node name contains IP also HR name contains IP 
In the above case Template will take IP from Node name.
2.	Case 2 – Node name contain hostname and HR name contain IP
First template will check IP from Node name if it failed to detect then it will search for HR name. In this case template will find IP from HR name and print it.
3.	Case 3 – Node Name contains Hostname and HR name not contain IP 
In this case first hostname will be saved in one variable and then it will check for IP in HR name. Since HR name does not contain any IP will print Host name.
4.	Case 4 – variable “Take_hostname_from_Health_Rule” is set to 1
For above case it will simply take IP from HR name and does not look for node name. 
Note: - If HR name does not contain IP then Template will fail, Hence suggested to set this variable when User desperately want IP to be parse from HR Name.

Known Issues
1.	Template fail if u set HR on baseline.

Design and Developed by 
1.	Pratik Purohit
2.	Namrata Adavkar

Reviewed By 
1.	Swathi Iyer
2.	Hitesh Paunikar 


