# Lab Execution Steps

## 1. Create Users

sudo adduser user1
sudo adduser user2

## 2. Create Group

sudo groupadd developers

## 3. Add User to Group

sudo usermod -aG developers user1

## 4. Create Shared Directory

sudo mkdir /securedata
sudo chown root:developers /securedata
sudo chmod 770 /securedata

## 5. Verify Access

su user1
cd /securedata

## 6. Remove Unnecessary Sudo Access

sudo deluser user2 sudo
