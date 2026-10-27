## 💻 Bonus Guide: The £0 SoundTouch NAS (Repurposing an Old Laptop)

When Bose permanently shut down the SoundTouch cloud servers in May 2026, thousands of users lost the ability to easily add or manage network music drives. If you want local FLAC/MP3 streaming back online—including saving albums to your 6 physical preset buttons—you do not need to spend £200+ on dedicated Synology or QNAP NAS hardware.

If you have an old Windows laptop gathering dust in a cupboard, you can wipe it and install **OpenMediaVault (OMV)**—a free, lightweight, rock-solid Linux operating system that turns an old laptop into a silent, 24/7 dedicated DLNA music server (with its own built-in battery backup!).

Here is the step-by-step guide to building your own £0 SoundTouch NAS.

---

### Phase 1: The Installation
1. Download the free **OpenMediaVault ISO** from their [official website](https://www.openmediavault.org/).
2. Use a free tool like **Rufus** or **BalenaEtcher** to flash the ISO onto a USB thumb drive.
3. Plug the USB into your old laptop, boot from it, and follow the on-screen prompts to install the OMV operating system over the entire hard drive.
4. Once finished, unplug the USB drive, plug the laptop directly into your broadband router using an Ethernet cable, and turn it on.

---

### Phase 1.5: The System Prep (Vital)
Because OMV is a lightweight, barebones system, we need to install a few basic utilities before we can disable the laptop lid sleep switch.

1. On the laptop's black text screen, log in with the username `root` and the password you created during setup.
2. Update the package directory by typing:
   ```bash
   apt-get update
   ```
3. Install the required system tools by typing:
   ```bash
   apt-get install sudo nano bash-completion curl -y
   ```
4. Once the installation text stops scrolling, your system is prepped.

---

### Phase 2: The "Lid Hack" (Crucial for Laptops)
By default, closing a laptop lid puts the machine to sleep and takes your music offline. We need to tell the server to ignore the lid completely.

1. Open the power configuration file by typing:
   ```bash
   nano /etc/systemd/logind.conf
   ```
2. Use the down arrow key to find the line that says `#HandleLidSwitch=suspend`.
3. Delete the `#` at the start, and change `suspend` to `ignore` so it looks exactly like this:
   ```ini
   HandleLidSwitch=ignore
   ```
4. Press `Ctrl+O` to save, hit `Enter` to confirm, and press `Ctrl+X` to exit.
5. Restart the power service by typing:
   ```bash
   systemctl restart systemd-logind
   ```
You can now safely close the laptop lid, tuck it away next to your router, and finish the rest of the setup from a web browser on your main PC or Mac!

---

### Phase 3: The "Single Drive" Bypass
OMV is designed for multi-bay servers and normally prevents you from storing media on the same drive that holds the operating system. Since most laptops only have one internal drive, we use an official plugin to bypass this.

1. Check the laptop screen one last time to note its local IP address (e.g., `192.168.1.x`), and type that IP address into the web browser on your main computer.
2. Log into the OMV web dashboard:
   * **Username:** `admin`
   * **Password:** `openmediavault`
3. Go to **System > Plugins** in the left-hand menu.
4. Search for `sharerootfs`, check the box for `openmediavault-sharerootfs`, and click the **Install** button (the down arrow icon at the top).
> **Note:** Whenever OMV finishes a task, a yellow banner appears at the top of the screen. Always click the **Checkmark** icon to apply and save your changes.

---

### Phase 4: Create the Music Folder & Network Share (SMB)
Now we create a folder and broadcast it over your home network so you can drag and drop music files from your Windows PC or Mac.

1. Go to **Storage > Shared Folders** and click `+` (Create). Name it `Music`, select your main root filesystem under **File system**, and save.
2. Go to **Services > SMB/CIFS > Settings**, check the **Enable** box, and save.
3. Go to **Services > SMB/CIFS > Shares**, click `+` (Create), select your `Music` folder, and set **Public** to `Guests allowed`.
4. **The Permissions Fix:** If Windows or macOS won't let you copy files into the folder, go back to **Storage > Shared Folders**, select the `Music` row, and click the **Access Control List (ACL)** button (the folder/key icon). Scroll to the bottom, change the **Others** dropdown to `Read/Write/Execute`, check **Replace existing permissions**, and click Save.

---

### Phase 5: The Bose DLNA Fix
Your computer can now drag-and-drop music onto the laptop, but Bose SoundTouch speakers require the **DLNA/UPnP** streaming protocol to browse and play tracks.

1. Go to **System > Plugins** and search for `dlna`.
2. Install the `openmediavault-minidlna` plugin and apply the yellow configuration banner.
3. Go to **Services > DLNA > Settings**, check **Enable**, and save.
4. Go to **Services > DLNA > Shares**, click `+` (Create), select your `Music` folder, and set Content Type to `Audio`.
5. Click **Rescan** on the DLNA Settings tab so the server indexes your albums.

---

### 🎉 You're Done!
Open the **Controller Pro** app (with your **Controller Cube** or **Controller Cloud** active), go to **Settings (Gear Icon) > Browse Local NAS > + Add**, and tap your new OpenMediaVault server! Our Smart NAS Injector will permanently lock the drive into your SoundTouch speakers over Wi-Fi.
