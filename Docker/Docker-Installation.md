
````markdown
# ✅ Step-by-Step: Install WSL2 with Ubuntu 22.04

## 🔹 Step 1: Enable WSL and Virtualization

1. Open PowerShell as Administrator  
   Right-click **Start** → **"Windows PowerShell (Admin)"** or **"Terminal (Admin)"**.

2. Run this command to install WSL with Ubuntu 22.04 (default):

   ```powershell
   wsl --install
````

> This command does everything: installs WSL2, sets Ubuntu as default, and downloads Ubuntu 22.04.

3. Reboot our system if prompted.

---

## 🔹 Step 2: Launch Ubuntu and Set Up

* After reboot, Ubuntu will launch automatically.
  If not, search for **“Ubuntu”** in the Start Menu.

* Let it install (this takes a few minutes).

* Set our Linux **username** and **password** when prompted.

---

## 🔹 Step 3: Confirm WSL2 is Being Used

Run the following in PowerShell or CMD:

```bash
wsl --list --verbose
```

✅ Output should show:

```sql
Ubuntu-22.04    Running    2
```

If it says `1`, change it to WSL2:

```bash
wsl --set-version Ubuntu-22.04 2
```

---

## 🔹 Step 4: Update & Upgrade Ubuntu

Inside the Ubuntu terminal:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 🔹 Step 5: Install Development Tools (Optional)

For Python, AI/ML, Git, etc.:

```bash
sudo apt install python3 python3-pip git build-essential -y
```

---

## 🔹 Step 6: (Optional) Add a GUI for Ubuntu Apps

Ubuntu on WSL2 now supports GUI apps natively on **Windows 11**.

Try running:

```bash
gedit
```

> If we're on **Windows 10**, we’ll need to install an external X server like **VcXsrv**.

---

## 🔹 Step 7: (Optional) Set Resource Limits (RAM/CPU)

Create a `.wslconfig` file at:

```
C:\Users\<OurUsername>\.wslconfig
```

Example content:

```ini
[wsl2]
memory=4GB
processors=2
```

Apply changes:

```bash
wsl --shutdown
```

---

## 🔹 Step 8: Install Docker on Ubuntu (WSL2)

1. **Uninstall old versions (if any):**

   ```bash
   sudo apt remove docker docker-engine docker.io containerd runc
   ```

2. **Set up the Docker repository:**

   ```bash
   sudo apt update
   sudo apt install ca-certificates curl gnupg
   sudo install -m 0755 -d /etc/apt/keyrings
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

3. **Install Docker Engine:**

   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
   ```

4. **Start Docker and add our user to the docker group:**

   ```bash
   sudo service docker start
   sudo usermod -aG docker $USER
   ```

   > We may need to restart the terminal or run `newgrp docker` for the group change to take effect.

5. **Test Docker:**

   ```bash
   docker run hello-world
   ```

---

## 🎉 Done!

