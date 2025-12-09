# -HTB-Bank

## I start with the nmap 

```
nmap -p- -sVC -vv -oN nmap_scan --min-rate=5000 10.10.10.2
```

<img width="1597" height="601" alt="image" src="https://github.com/user-attachments/assets/3b6b249d-22f1-4e20-9528-739d7eb3093d" />


## After finding all the directory on the site if we vizit `balance-transfer` we will se a loot of bank transfers encrypted , but 1 with a different size studs up "68576f20e9732f1b2edc4df5b8533230.acc"


<img width="1012" height="445" alt="image" src="https://github.com/user-attachments/assets/bd01cfaa-9646-4309-b3e5-90e0b56f877f" />


<img width="858" height="349" alt="image" src="https://github.com/user-attachments/assets/46b5b90e-7403-4909-990a-b984ed662718" />

<img width="742" height="377" alt="image" src="https://github.com/user-attachments/assets/5ad60353-4439-4757-9bc0-c45f1bae0b47" />




## If we open it we will find a fail encrypted file 


<img width="526" height="334" alt="image" src="https://github.com/user-attachments/assets/dc8548dc-b52c-478f-9268-0848d846e60f" />

```
chris@bank.htb:!##HTBB4nkP4ssw0rd!##
```

## I login on the site with chris creds and we can see the Dashboard


<img width="1920" height="958" alt="image" src="https://github.com/user-attachments/assets/57a92d79-ab71-40d5-a443-93b93999d104" />


## On the support section we can upload something , we will find out on the source page that a note for debugging was left behind with an extension ".htb"


<img width="1917" height="536" alt="image" src="https://github.com/user-attachments/assets/31daf9d8-b124-41b1-8faa-94e0d0dde3cb" />


<img width="902" height="79" alt="image" src="https://github.com/user-attachments/assets/5467c738-3efa-4127-943e-9bb506d188f8" />

## I use reverse shell generator to create a php shell 

<img width="1319" height="902" alt="image" src="https://github.com/user-attachments/assets/19f19dfb-c70c-4312-9a67-c84c7f7d39c3" />

## After we submit the file and open it we get a shell 

<img width="920" height="256" alt="image" src="https://github.com/user-attachments/assets/e96845a2-b785-4608-9967-efd5b7225454" />

### On the home directory we find the user flag 

<img width="521" height="246" alt="image" src="https://github.com/user-attachments/assets/d131f42d-ed63-4a9a-bd6f-5b272d2af42d" />

## After that we move to the /tmp and we upload linpeas . We open a server and transfer the linpeas.sh to the target 


<img width="598" height="106" alt="image" src="https://github.com/user-attachments/assets/1fd24df7-038f-453a-87fd-25b5a25e44bd" />


<img width="640" height="268" alt="image" src="https://github.com/user-attachments/assets/e43aead0-5bea-413d-82cd-1c9cb444e68a" />


## We mode it and run it 

```
chmod +x linpeas.sh
```
 
## Linpeas descovert that the "/etc/passwd" it s writable , so we create a root

<img width="835" height="61" alt="image" src="https://github.com/user-attachments/assets/d375c5eb-3fe3-44d9-a863-9ec9a748e295" />


```
pw=$(openssl passwd sebi123); echo "sebi:${pw}:0:0:root:/root:/bin/bash" >> /etc/passwd
```

## And we find the root flag 

<img width="897" height="259" alt="image" src="https://github.com/user-attachments/assets/d19f07ad-7813-473c-a342-99d2ef98b8f8" />















