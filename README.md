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

📸  
<img width="1452" height="649" alt="Screenshot 2025-09-17 171227" src="https://github.com/user-attachments/assets/9bb5d231-d4f8-4bb0-89a6-9f4a1fb35f44" />
<img width="1215" height="287" alt="Screenshot 2025-09-17 171251" src="https://github.com/user-attachments/assets/9f669852-000d-4826-b76f-371b3425aa3b" />
<img width="1192" height="1019" alt="Screenshot 2025-09-17 174219" src="https://github.com/user-attachments/assets/ad28d447-cbcc-4dbf-a569-e8eed6b984f9" />


---

### 3. Create Organizational Units (OUs)  
- Open **Active Directory Users and Computers (ADUC)**.  
- Create OUs such as:  
  - `_EMPLOYEES`  
  - `_ADMINS`  
- Helps organize accounts and apply group policies.  

📸 
<img width="585" height="329" alt="Screenshot 2025-09-17 174532" src="https://github.com/user-attachments/assets/46503828-460a-4e78-883d-da4e73e65f80" />


---

### 4. Create Users and Groups  
- Add new user accounts (e.g., *John Doe*, *Jane Smith*).  
- Assign to appropriate groups (e.g., Domain Admins, Standard Users).  

📸  
<img width="578" height="522" alt="Screenshot 2025-09-17 174613" src="https://github.com/user-attachments/assets/ca923f33-71d4-40f8-9a16-a8c2004907f6" />


---

### 5. Join Client VM to Domain  
- On the **Windows 10 Client VM**:  
  - Update **DNS** settings to point to the Domain Controller’s private IP.  
  - Join the computer to `mydomain.com`.  
  - Restart the client machine.  

📸  
<img width="477" height="309" alt="Screenshot 2025-09-17 173731" src="https://github.com/user-attachments/assets/735db839-136a-41ce-8560-4eb998823388" />
 

---

### 6. Verify Domain Login  
- Log into the **Client VM** using a domain account.  
- Confirm access to domain resources and policies.  

📸 
<img width="691" height="990" alt="Screenshot 2025-09-17 174959" src="https://github.com/user-attachments/assets/b0841d11-0e19-492b-ac4c-8f06daf70eea" />

---

### 7. Configure Group Policy  
- Open **Group Policy Management** on the Domain Controller.  
- Create and link a GPO (Group Policy Object).  
- Example: Force desktop background, password policies, or software restrictions.  

📸 
<img width="727" height="895" alt="Screenshot 2025-09-17 175915" src="https://github.com/user-attachments/assets/4506a17c-6757-4cd1-aad6-5cb5a483582d" />


---

## 📂 Repository Structure  
