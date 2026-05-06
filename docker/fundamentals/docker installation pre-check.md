31. Steps to Install Docker:				
                
1.     Pre-Check(Production Mindset)				
                
Before Installation  Docker : 				
1. OS version				
2. Kernel details				
3. CPU details				
4. Archiecture Check				
                
                
                
1. OS & Kernel 				
For OS= command=uname -r				
For Kernel= cat /etc/os release				
     ![alt text](image-31.png)  

     ![alt text](image-32.png)           
             
                
2. CPU & Architecture Check				
CPU & Archtiecute =Command used= lscpu				
My machine shows : Architecture: *86_64				
CPU Shows: 2 CPU				
     ![alt text](image-33.png)           
                
3 .Memory Check				
Memory Check= Linux Command Used= free -h				
Production baseline: 				
**Minimum - 2GB				
**Recommended - 4GB+				
Swap: must exit = If swap not show: command: sudo swapon --show				
My machine shows: total 4 GB				
Available: 2.9 GB				
   ![alt text](image-34.png)  

                
4. Disk Capacity & Usage				
Disk Capacity=linux command used= df -h				
Production basline: should be minimum greater than : 10 GB free				
My machine shows: total 49 GB				
Available: 42 GB				
                
 ![alt text](image-35.png)               
                                
5. Filesytstem Type check				
Filesystem check=Linux command used= df -T /				
                
Only support:				
** ext4 				
** xfs (with d-typesupport)				
 ![alt text](image-36.png)

                
6. Cgroups Support				
Cgroups Support =linux command used = mount | grep cgroup				
                
Used for CPU and memory limits in containers				
   ![alt text](image-37.png)             
                
                
7. Namespace Support				
Namespace Support =linux command used = ls /proc/self/ns				
This is Docker isolation mechanisam				
                
   ![alt text](image-38.png)             
                
                
8. Network Stack check				
Network stack =linux command used = ip a				
IT verify:				
** interface has ip				
** internet reachable				
                
   ![alt text](image-39.png)             
                
                
9. Required Kernel Modules				
Kernel modules= linux command used = lsmod | grep overlay				
lsmod | grep br_netfilter				
 ![alt text](image-40.png)               
                
                
10. check for exisitng docker install (clean state)				
exsiting docker = linux command used = dpkg -l | grep docker				
its should be empty				
   ![alt text](image-41.png)             
                
11. Check disk inode availability				
disk inode aviabilability= linux command used = df -i				
Why: even with space, container failes if inodes are exahusted				
  ![alt text](image-42.png)              
                
                
12. Firewall Check 				
firewall chec : linux command used = sudo ufw status				
Note: docker manipulate iptables				
   ![alt text](image-43.png)             
                
                
13. system health check 				
linux command used : apt update , apt upgrade				
                
14. User Permission and sudo access				
Linux command 				
whoami				
groups				
sudo -l				
   ![alt text](image-44.png)             

    ![alt text](image-45.png)            
                
15. Time synchronization				
time sync: linux command used : timedatectl				
verify : **ntp service : active				
   ![alt text](image-46.png)             
                
                
16. Check Avilable package space				
Linux command used : df -h /var				
Why: apt+docker images both consume /var				
                
  ![alt text](image-47.png)              
                
                
17. Hostname & DNS check				
Linux command : hostnamectl = for hostname				
DNS = cat /etc/hosts				
  ![alt text](image-48.png)              
                
                  
18. Verify virutalization				
Linux command used= systemd-detect-virt				
![alt text](image-49.png)