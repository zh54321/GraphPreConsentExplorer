# GraphPreConsentExplorer 🔍

During security assessments, I often rely on various pre-consented permissions for the Microsoft Graph API. To use these permissions, I need to know which Client IDs have specific pre-consented permissions on the Graph API. Additionally, as more organizations restrict the Device Code Flow, it is crucial to identify which clients still allow authentication via the OAuth Code Flow. This requires knowing which clients support different authentication methods, including:
- Device Code Flow
- OAuth Code Flow
- Special Refresh Flows (FOCI / BRK)

To address this, I used [EntraTokenAid](https://github.com/zh54321/EntraTokenAid) to perform thousands of authentication attempts using ~1200 first party clients. This process helped identify which clients work with specific authentication flows and their corresponding pre-consented permissions on the Microsoft Graph API.

The result is a fairly large list of nearly 200 Client IDs that have pre-consented permissions on the Graph API and can be used to authenticate without a client secret.  
All the information is stored in a YAML file, and there is a simple HTML GUI for easy search and filter navigation. It also provides easy copy-and-paste authentication commands for use with [EntraTokenAid](https://github.com/zh54321/EntraTokenAid).

If you know of additional first-party clients or authentication methods, feel free to contribute!  
Note: The goal is not to list every valid redirect URL, but to have at least one usable example for each client.

## 🚀 Features

**Data:**
- Nearly 1200 enabled clients
- 1071 present in my test tenant
- Almost 200 clients with usable pre-consented permissions for the Microsoft Graph API


**GUI**:
- Load and visualize Entra ID first party clients from YAML files
- Display pre-consented Graph API permissions assigned to each application
- Filter, search and sorting capabilities (by name, client ID, FOCI, Auth Flow, etc.)
- [EntraTokenAid](https://github.com/zh54321/EntraTokenAid) authentication command generator (OAuth, Device Code, BrkRefresh, etc.)
- No external dependencies (All local, simple HTML + JavaScript)


## 📷 Screenshots
Main table:

![alt text](images/mainview.png)

Detail view of the app. Includes copy and paste authentication commands:

![alt text](images/appdetails.png)

Usage of the copy and paste commands to use with [EntraTokenAid](https://github.com/zh54321/EntraTokenAid):
![alt text](images/EntraTokenAid.png)

## 📥 Installation


### Clone the Repository
```bash
git clone https://github.com/yourusername/GraphPermExplorer.git
```

## 📌 Usage
1. **Open the HTML File**
2. **Load a YAML File:** Click on `📂 Load YML File` to load the YAML file.



## 📖 YAML Format
```yaml
apps:
  - name: "App One"
    client_id: "1234-5678-9101"
    enabled: "True"
    graph_api_permissions: ["User.Read", "Directory.Read.All"]
    auth_code: "Enabled"
    device_code: "Enabled"
    brk_refresh: "Enabled"
    foci: "True"
    reply_addresses:
      - "https://whatever/callback"
    notes: "This property is optional"
```
