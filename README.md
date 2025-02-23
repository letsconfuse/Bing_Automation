# Edge Profile Automation Script

## 🚀 Overview
This PowerShell script automates opening **Microsoft Edge** with multiple profiles, performing **Bing searches**, and closing the browser after a set time. It is useful for automating browsing tasks, testing, or research purposes.

## 📂 Features
- ✅ Opens Microsoft Edge with **specific profiles**.
- ✅ Performs **randomized Bing searches**.
- ✅ Waits for a **set duration** before closing Edge.
- ✅ Closes only the Edge instances launched by the script.
- ✅ Uses an **external search terms file** for better randomness.

## 📑 Prerequisites
- **Windows OS** with **PowerShell 5.1+**.
- **Microsoft Edge installed** at the default location (`C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe`).
- **Ensure Edge Profiles Exist:** Check `C:\Users\YourUserName\AppData\Local\Microsoft\Edge\User Data` for profile names.
- **Create a `search_terms.txt` file** containing a list of words (one per line) for Bing searches.

## 🛠 Installation & Setup
### **1️⃣ Clone the Repository**
```sh
 git clone https://github.com/letsconfuse/edge-automation.git
 cd edge-automation
```

### **2️⃣ Update the Script (If Needed)**
- Modify the **Edge path** if it differs from the default location.
- Update the **profile names** to match your Edge profile directories.

### **3️⃣ Run the Script**
```sh
powershell -ExecutionPolicy Bypass -File edge_automation.ps1
```

## ⚙ Configuration
The script contains a list of profiles and sleep durations:
```powershell
$profiles = @(
    @{ ProfileName = "Profile 10"; SleepDuration = 600 },
    @{ ProfileName = "Profile 11"; SleepDuration = 600 }
)
```
- **ProfileName**: The name of the Edge profile to use.
- **SleepDuration**: How long the browser stays open before closing (in seconds).

## 🔥 How It Works
1. **Opens Edge** with a given profile.
2. **Performs a Bing search** with a random word from `search_terms.txt`.
3. **Keeps the session open** for the defined time.
4. **Closes only the Edge windows** related to the session.
5. **Repeats for the next profile** in the list.

## 🛠 Troubleshooting
### **Issue: Edge profile not opening?**
✅ Ensure the **profile name is correct** (Check `C:\Users\YourUserName\AppData\Local\Microsoft\Edge\User Data`).

### **Issue: Edge closes all windows?**
✅ Modify the `Stop-Process` command to only close relevant instances.

### **Issue: Script blocked by execution policy?**
✅ Run:
```sh
Set-ExecutionPolicy Bypass -Scope Process -Force
```

## 📜 License
This project is licensed under the **MIT License**.

## 🤝 Contributing
Feel free to submit **issues** or **pull requests** to improve this script.

---
### 👨‍💻 Author
[My Profile](https://github.com/letsconfuse)

