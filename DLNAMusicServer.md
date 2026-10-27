Markdown
## 💻 Bonus Guide: The £0 / $0 SoundTouch NAS (Repurposing an Old Laptop)

When Bose permanently shut down the SoundTouch cloud servers in May 2026, thousands of users lost the ability to easily stream local music or link new NAS drives. If you want to get local FLAC/MP3 streaming back online without spending £200+ on a dedicated Synology or QNAP enclosure, you can repurpose any old Windows laptop gathering dust in a cupboard.

By wiping the old laptop and installing **OpenMediaVault (OMV)**—a free, lightweight Linux server OS—you can turn it into a silent, 24/7 dedicated DLNA music server for your SoundTouch ecosystem (complete with its own built-in battery backup!).

---

### Phase 1: The Installation
1. Download the free **OpenMediaVault ISO** from their official website (`openmediavault.org`).
2. Use a free tool like **Rufus** or **BalenaEtcher** to flash the ISO onto a USB thumb drive.
3. Plug the USB into your old laptop, boot from it, and follow the on-screen prompts to install the OMV operating system over the entire hard drive.
4. Once finished, plug the laptop directly into your broadband router using an Ethernet cable and turn it on.

---

### Phase 1.5: The System Prep (Vital)
Because OMV is a lightweight, barebones system, we need to install a few basic utilities before we can configure the laptop lid.

1. On the laptop's black terminal screen, log in with the username `root` and the password you created during setup.
2. Update the package directory by typing:
   ```bash
   apt-get update
Install the required system tools by typing:

Bash
apt-get install sudo nano bash-completion curl -y
Once the installation finishes scrolling, your system is prepped.

Phase 2: The "Lid Hack" (Crucial for Laptops)
By default, closing a laptop lid puts the machine to sleep and takes your music server offline. Here is how to make the server ignore the lid completely:

Open the systemd power configuration file:

Bash
nano /etc/systemd/logind.conf
Scroll down to find the line that says #HandleLidSwitch=suspend.

Delete the # at the start and change suspend to ignore so it reads:

Ini, TOML
HandleLidSwitch=ignore
Press Ctrl+O to save, hit Enter, and press Ctrl+X to exit.

Restart the power service to apply the change:

Bash
systemctl restart systemd-logind
You can now safely close the laptop lid, tuck it away next to your router, and complete the rest of the setup from a web browser on your main computer!

Phase 3: The "Single Drive" Bypass
OMV is designed for multi-bay servers and normally prevents you from storing media on the same drive that holds the operating system. Since a laptop usually has a single internal drive, we use an official plugin to bypass this:

Check the laptop screen one last time to note its local IP address (e.g., 192.168.1.x) and type that IP into the web browser on your main PC/Mac.

Log into the OMV web dashboard (Default Username: admin | Default Password: openmediavault).

Navigate to System > Plugins in the left menu.

Search for sharerootfs, check the box, and click the Install button (the down arrow icon).

Note: Whenever OMV finishes a task, a yellow banner appears at the top of the screen. Always click the checkmark to apply changes.

Phase 4: Create the Music Folder & Network Share (SMB)
Now we create a shared folder so you can drag and drop music files from your Windows PC or Mac over Wi-Fi:

Go to Storage > Shared Folders and click + to create a new folder. Name it Music and select your main root file system.

Go to Services > SMB/CIFS > Settings and check the Enable box.

Go to Services > SMB/CIFS > Shares, click +, select your Music folder, and set Public to Guests allowed.

The Permissions Fix: If Windows or macOS won't let you copy files into the folder, go back to Storage > Shared Folders, select the Music folder, and click the ACL button (the gear/key icon). Scroll to the bottom, change the Others dropdown to Read/Write/Execute, check Replace existing permissions, and click Save.

Phase 5: Enable the Bose DLNA Server
Bose SoundTouch speakers require the UPnP/DLNA streaming protocol to browse and play tracks:

Go to System > Plugins and search for dlna.

Install the openmediavault-minidlna plugin.

Navigate to Services > DLNA > Settings and check Enable.

Switch to the Shares tab, click +, and select your Music folder.

Click Rescan on the Settings tab so the server indexes your albums and tracks.

🎉 Linking Your New NAS to SoundTouch
Open the Controller Pro app (with your Controller Cube or Controller Cube OS active on the network), navigate to Settings (Gear Icon) > Browse Local NAS > + Add, and tap your new OpenMediaVault server. Our Smart NAS Injector will permanently lock the DLNA UUID into your SoundTouch speakers!
