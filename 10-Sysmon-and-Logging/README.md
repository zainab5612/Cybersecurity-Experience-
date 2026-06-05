## Sysmon Installation and Log collection

## Objective
Install Sysmon on Windows 11 machine endpoint visibility and collect detailed telemerty. the logs provide visibility into process, network, conections, and system activity, supporting future detection, threat hunting, and incident response.

## Skills Demonestrated.




## STEPS
install sysmon on windows 11 machine 
download swiftonsecurity configuration this is used  for learning.   Then Save it as *C:\Users\zaina\Downloads\Sysmonrs\zaina\Downloads\Sysmon\sysmonconfig.xml*
install sysmon on powershell *.\Sysmon64.exe -accepteula -i sysmonconfig.xml*
<img width="1149" height="466" alt="image" src="https://github.com/user-attachments/assets/494c2a11-fb7d-4d75-8e99-5550cc05bb07" />

On Event Log check Sysmon
Event IDs 1 , 13, 22
<img width="1209" height="593" alt="image" src="https://github.com/user-attachments/assets/1bf483fb-cc6f-40f1-99fb-9b3fa22e32e1" />

Generating an event to investigate it.
Scenario
user lanuches poweshell 
find who launchedit? when? from where? what commands were executed?

Event ID = 1  Process Creation
<img width="1041" height="638" alt="image" src="https://github.com/user-attachments/assets/f0842a4f-5660-48ac-9128-bc89300aae89" />
<img width="1104" height="704" alt="image" src="https://github.com/user-attachments/assets/0821d2d5-71b7-4a94-8063-ea2700a82313" />

Event ID = 3 Network Connections
