# Configuring Active Directory within Azure VMs  

This repository demonstrates how to configure **Active Directory (AD)** within Azure Virtual Machines (VMs).  
It covers creating a domain controller, joining clients to the domain, and managing users/groups within the AD environment.  

---

## 🖥️ Environments and Technologies Used  
- **Microsoft Azure** (Resource Groups, Virtual Networks, Virtual Machines)  
- **Remote Desktop (RDP)**  
- **Active Directory Domain Services (AD DS)**  
- **Server Manager & Group Policy Management**  

---

## 💻 Operating Systems Used  
- **Windows Server 2022** (Domain Controller VM)  
- **Windows 10/11** (Client VM)  

---

## 📋 Configuration Steps  

### 1. Provision Azure VMs  
- Create two VMs in Azure:  
  - **Domain Controller (Windows Server 2022)**  
  - **Client Machine (Windows 10/11)**  
- Ensure both are on the same **Virtual Network (VNet)**.  

📸   
<img width="1914" height="440" alt="Screenshot 2025-09-17 170922" src="https://github.com/user-attachments/assets/4f14fd9e-6dc7-4f57-af34-739c3573507d" />


---

### 2. Configure Domain Controller  
- Set a **static private IP address** on the Domain Controller.  
- Rename the server (e.g., `DC-1`).  
- Install **Active Directory Domain Services (AD DS)** via Server Manager.  
- Promote the server to a **Domain Controller** (e.g., domain: `mydomain.com`).  

📸 **Screenshot:**  
<img width="1452" height="649" alt="Screenshot 2025-09-17 171227" src="https://github.com/user-attachments/assets/9bb5d231-d4f8-4bb0-89a6-9f4a1fb35f44" />
<img width="1215" height="287" alt="Screenshot 2025-09-17 171251" src="https://github.com/user-attachments/assets/9f669852-000d-4826-b76f-371b3425aa3b" />


---

### 3. Create Organizational Units (OUs)  
- Open **Active Directory Users and Computers (ADUC)**.  
- Create OUs such as:  
  - `_EMPLOYEES`  
  - `_ADMINS`  
- Helps organize accounts and apply group policies.  

📸 **Screenshot:**  
![OU Creation](images/step3_ou.png)  

---

### 4. Create Users and Groups  
- Add new user accounts (e.g., *John Doe*, *Jane Smith*).  
- Assign to appropriate groups (e.g., Domain Admins, Standard Users).  

📸 **Screenshot:**  
![User Creation](images/step4_users.png)  

---

### 5. Join Client VM to Domain  
- On the **Windows 10 Client VM**:  
  - Update **DNS** settings to point to the Domain Controller’s private IP.  
  - Join the computer to `mydomain.com`.  
  - Restart the client machine.  

📸 **Screenshot:**  
![Domain Join](images/step5_client_join.png)  

---

### 6. Verify Domain Login  
- Log into the **Client VM** using a domain account.  
- Confirm access to domain resources and policies.  

📸 **Screenshot:**  
![Domain Login](images/step6_login.png)  

---

### 7. Configure Group Policy  
- Open **Group Policy Management** on the Domain Controller.  
- Create and link a GPO (Group Policy Object).  
- Example: Force desktop background, password policies, or software restrictions.  

📸 **Screenshot:**  
![Group Policy](images/step7_gpo.png)  

---

## 📂 Repository Structure  
