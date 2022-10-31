# Install-Printer_Artix-Linux

## Complete & step-by-step procedure
**Note:** All command "code" will be executed as Admin/"ROOT" apart `paru`-command, the AUR-Helper "Paru" (or another one you like) should be installed before you start with printer installation. When you are ready, open a terminal and become "ROOT"/Admin with [code]: `sudo -i`, insert your password when asked and be carefully **!** 

### 1.  Install prerequisite packages with: 
```
pacman -S --needed cups-openrc cups-pdf  cups print-manager system-config-printer
```

### 2. Detect service is installed, added with:
* Following [code] will show you the start-time, e.g. `default`

```
rc-update -v show | grep avahi-daemon

rc-update -v show | grep cupsd
```
### 3. Enable service-s with:
* In case one or both the services are not yet added>>

```
rc-update add avahi-daemon default

rc-update add cupsd default
```
* You can countercheck if successful with commands in **§ 2.**

### 4. Check if "daemon-s" are already running (normally `avahi-daemon` is it).
```
rc-status | grep avahi-daemon

rc-status | grep cupsd
```
* To see all service-s_status alphabetically sorted and in "verbose"-mode use:
```
rc-status --servicelist -s | sort -n
```
* To see all service-s not sorted but in "verbose"-mode btw. you can use the "search"-function of terminal after result with keys-combination [SHIFT + CTRL + F] and inserting the name of the service>>

```
rc-status --servicelist -s
```

### 5. If a "daemon" is not yet started, start service-s with: 
```
rc-service avahi-daemon start

rc-service cupsd start
```
* If all going well, recheck the status as in **§ 4.** shown.

### 6. In case of errors by start of service-s, use following command-s:
```
rc-service --debug avahi-daemon start

rc-service --debug cupsd start
```
* Use the output of above two commands for asking support in the forum

* Check services `cupsd` and `avahi-daemon` are up and running as in **§ 4.** shown **!**
### 7. Install Printer-Drivers (in case) from AUR with:
**Note:** Use `paru` as `$USER` and not as `$ADMIN`, even don't use `sudo`, the app will ask you for the password when is time to install.
```
paru -S --needed brother-hl3152cdw
```
* In case you know only the manufacturer or model of your printer, use the search function of AUR-Helper (paru) as follow:

```
paru brother

paru hl3152cdw

paru hl3152
```

* Your printer-name or -model can be different **!** 

### 8. Configure printer-s over `systemsettings` or `http://localhost:631`
* System-Settings can be called different depending of your Desktop-Environment
* I prefer to configure the printes over `systemsettings`
#### 8.1. Configure Hardware-Printer
1. Open `systemsettings`/`Printers` and click on `Add Printer`, choose your printer and select/follow the recommendations.
2. Ones the printer is added, you can `Configure` page-size, printing-quality, etc..
3. Under menu `Maintenance` you can choose to print a test-page.
#### 8.2. Configure Software-Printer (Virtual_PDF)
* For this follow the instruction as for **§ 8.1.** but... either all printing come to `$HOME`, `$USER` or to `/var/spool/cups-pdf/<UserName>/`
1. asd

- [x] **Done & Enjoy !**
