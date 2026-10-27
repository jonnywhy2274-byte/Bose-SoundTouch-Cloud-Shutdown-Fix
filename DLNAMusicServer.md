Hi everyone,

When Bose killed the SoundTouch cloud servers back in May, thousands of us lost the ability to easily stream local music or add new NAS drives. If you are looking to get local streaming back online but don't want to drop £200+ on a dedicated Synology or QNAP enclosure just to host your MP3/FLAC library, you don't have to.

If you have an old, slow Windows laptop gathering dust in a cupboard, you can wipe it and install OpenMediaVault (OMV)—a free, extremely lightweight Linux operating system that will turn that old laptop into a rock-solid 24/7 DLNA music server for your SoundTouch ecosystem.

Because laptops have built-in batteries (effectively a free UPS) and run silently, they make fantastic, low-power media nodes.

Here is the step-by-step guide to building your own budget NAS and bypassing the usual "laptop sleep" issues.

Phase 1: The Installation
Download the free OpenMediaVault ISO from their official website.

Use a free tool like Rufus or BalenaEtcher to flash the ISO onto a USB thumb drive.

Plug the USB into your old laptop, boot from it, and follow the on-screen prompts to install the OMV operating system over the entire hard drive.

Once finished, plug the laptop directly into your broadband router using an Ethernet cable and turn it on.

Phase 1.5: The System Prep (Vital)
Because OMV is a lightweight, barebones system, we need to teach it a few basic commands before we can hack the laptop lid.

On the laptop's black text screen, log in with the username root and the password you created during setup.

Tell the system to update its app directory by typing: apt-get update and hit Enter.

Install the vital system tools by typing exactly this: apt-get install sudo nano bash-completion curl -y and hit Enter.

Let the screen scroll through the installation matrix. Once it stops, your system is fully prepped!

Phase 2: The "Lid Hack" (Crucial for Laptops)
By default, if you close a laptop lid, it goes to sleep and takes your server offline. We need to tell the server to ignore the lid completely.

Type this exact command to open the power settings: nano /etc/systemd/logind.conf

Scroll down to find the line that says #HandleLidSwitch=suspend.

Delete the # at the start, and change the word suspend to ignore. It should look exactly like this: HandleLidSwitch=ignore

Press Ctrl+O to save, hit Enter, then press Ctrl+X to exit.

Type systemctl restart systemd-logind and hit Enter.

You can now safely close the laptop lid, tuck it away next to your router, and do the rest of the setup from the web browser on your main PC!

Phase 3: The "Single Drive" Bypass
OMV is designed for massive servers and usually forbids you from putting music on the same drive that holds the operating system. Since a laptop only has one internal drive, we must bypass this constraint.

Look at the laptop screen one last time to find its IP address. Type that IP address into the web browser on your main computer.

Log into the OMV web dashboard (Default Username: admin, Password: openmediavault).

Go to System > Plugins in the left menu.

Search for sharerootfs, check the box, and click the install button (the down arrow).Note: Whenever OMV finishes a task, a yellow banner appears at the top. Always click the checkmark to apply changes.

Phase 4: Create the Music Folder & Network Share
Now we create a folder and broadcast it to your Mac or Windows PC so you can easily drag and drop your music.

Go to Storage > Shared Folders and click the + to create a folder. Name it Music.

Go to Services > SMB/CIFS > Settings and check the Enable box.

Go to Services > SMB/CIFS > Shares, click +, select your Music folder, and set Public to Guests allowed.

The Permissions Fix: If Windows/Mac won't let you copy files into the folder, go back to Storage > Shared Folders, highlight the Music folder, and click the ACL button (the gear/key icon). Scroll to the bottom and change the "Others" dropdown to Read/Write/Execute. Check Replace existing permissions and hit Save.

Phase 5: The DLNA Fix
Your computer can now see the drive, but SoundTouch speakers cannot read standard Windows (SMB) folders. They require a specific streaming protocol called DLNA.

Go to System > Plugins and search for dlna.

Install the openmediavault-minidlna plugin.

Go to Services > DLNA > Settings and check Enable.

Go to the Shares tab, click +, and select your Music folder.

Click Rescan on the Settings tab so the server indexes all your albums.

🎉 You're Done!

If you are using the Controller Pro app (or any local Marge bypass solution) to manage your system post-shutdown, just go to Settings > Browse Local NAS > Add. Your repurposed laptop will proudly appear, ready to stream your entire local collection to your speakers instantly.

Hope this helps some folks rescue their hardware without breaking the bank! Let me know if you run into any permission issues setting this up.
