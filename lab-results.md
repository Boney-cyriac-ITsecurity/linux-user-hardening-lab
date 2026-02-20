# Lab Results – User Hardening Experiment

## Initial Situation (Insecure Configuration)

- Created two users: user1 and user2
- Both users were added to the sudo group
- Created directory /companydata
- Applied permission 777 (world writable)

Result:
Both users were able to create files inside /companydata.
This represents an insecure configuration.

Example:
touch /companydata/hacked.txt
→ File creation succeeded for user2

---

## Hardening Actions Performed

1. Removed unnecessary sudo access from user2
   sudo deluser user2 sudo

2. Created a restricted group
   sudo groupadd developers

3. Added only user1 to developers group
   sudo usermod -aG developers user1

4. Changed directory ownership
   sudo chown root:developers /companydata

5. Applied secure permissions
   sudo chmod 770 /companydata

---

## Final Verification

Test as user2:
touch /companydata/test.txt
→ Permission denied

Test as user1:
touch /companydata/allowed.txt
→ File creation successful

---

## Security Principle Applied

Principle of Least Privilege:
Users should only have the minimum permissions necessary to perform their tasks.

user2 was not root and not part of the developers group.
Therefore access was denied by the Linux permission model.
