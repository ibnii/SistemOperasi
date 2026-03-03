<style>
:root {
  --bg-0: #090d18;
  --bg-1: #0f172a;
  --bg-2: #111827;
  --ink: #e6edf9;
  --muted: #a3afc5;
  --panel: rgba(17, 25, 44, 0.78);
  --accent: #22d3ee;
  --accent-2: #10b981;
  --line: #25324a;
  --code-bg: #060c1a;
  --code-ink: #d8e3f8;
  --shadow: rgba(0, 0, 0, 0.48);
}

body {
  margin: 0 auto;
  max-width: 1024px;
  padding: 2.5rem 2rem 3.5rem;
  font-family: "Avenir Next", "Trebuchet MS", "Segoe UI", sans-serif;
  color: var(--ink);
  line-height: 1.75;
  color-scheme: dark;
  background:
    radial-gradient(circle at 8% -12%, rgba(34, 211, 238, 0.22), transparent 38%),
    radial-gradient(circle at 100% 8%, rgba(16, 185, 129, 0.18), transparent 34%),
    linear-gradient(165deg, var(--bg-0) 0%, var(--bg-1) 48%, var(--bg-2) 100%);
}

h1,
h2,
h3,
h4,
h5,
h6 {
  color: #f4f8ff;
  line-height: 1.3;
  letter-spacing: 0.01em;
}

h1 {
  font-size: clamp(2rem, 3vw, 2.8rem);
  margin: 0 0 0.8rem;
  padding: 1rem 1.2rem;
  border-radius: 16px;
  background: linear-gradient(120deg, rgba(34, 211, 238, 0.2), rgba(16, 185, 129, 0.16));
  border: 1px solid rgba(125, 211, 252, 0.32);
  color: #f8fbff;
  box-shadow: 0 18px 34px var(--shadow);
  backdrop-filter: blur(2px);
}

h2 {
  margin-top: 2rem;
  padding: 0.6rem 0.9rem;
  border-left: 6px solid var(--accent);
  border-radius: 10px;
  background: linear-gradient(90deg, rgba(8, 47, 73, 0.78), rgba(8, 47, 73, 0.25));
}

h3,
h4,
h5,
h6 {
  margin-top: 1.4rem;
  color: #dbe7ff;
}

hr {
  border: 0;
  height: 1px;
  margin: 2rem 0;
  background: linear-gradient(90deg, transparent, #355174, transparent);
}

p,
li {
  color: var(--muted);
}

strong {
  color: #f8fbff;
}

blockquote {
  margin: 1rem 0;
  padding: 0.8rem 1rem;
  border-left: 5px solid var(--accent-2);
  background: rgba(17, 25, 44, 0.88);
  border: 1px solid rgba(71, 85, 105, 0.5);
  border-radius: 10px;
}

pre {
  padding: 1rem 1.1rem;
  border-radius: 14px;
  border: 1px solid #334155;
  background: var(--code-bg);
  color: var(--code-ink);
  overflow-x: auto;
  box-shadow: 0 12px 25px rgba(2, 6, 23, 0.55);
}

code {
  font-family: "JetBrains Mono", "Fira Code", "Consolas", monospace;
  font-size: 0.92em;
}

p code,
li code,
td code,
th code {
  padding: 0.16rem 0.42rem;
  border-radius: 6px;
  color: #7dd3fc;
  background: rgba(3, 25, 43, 0.78);
  border: 1px solid rgba(56, 189, 248, 0.35);
}

table {
  width: 100%;
  border-collapse: collapse;
  overflow: hidden;
  margin: 1rem 0;
  border-radius: 12px;
  box-shadow: 0 10px 20px var(--shadow);
}

th,
td {
  padding: 0.75rem;
  border: 1px solid var(--line);
}

th {
  color: #eff6ff;
  background: rgba(8, 47, 73, 0.85);
}

td {
  background: rgba(15, 23, 42, 0.82);
  color: #cbd5e1;
}

a {
  color: #67e8f9;
  text-decoration: none;
  border-bottom: 1px dashed rgba(103, 232, 249, 0.52);
}

a:hover {
  color: #34d399;
  border-bottom-color: #34d399;
}

img {
  display: block;
  max-width: min(100%, 920px);
  height: auto;
  margin: 1rem auto;
  border-radius: 12px;
  border: 1px solid rgba(51, 65, 85, 0.8);
  box-shadow: 0 12px 28px var(--shadow);
}

::-moz-selection {
  color: #f8fbff;
  background: rgba(56, 189, 248, 0.35);
}

::selection {
  color: #f8fbff;
  background: rgba(56, 189, 248, 0.35);
}

@media (max-width: 800px) {
  body {
    padding: 1.25rem 1rem 2.25rem;
    line-height: 1.65;
  }

  h1 {
    padding: 0.85rem 1rem;
    border-radius: 12px;
  }

  h2 {
    margin-top: 1.4rem;
  }

  pre {
    border-radius: 10px;
  }
}
</style>
# Latihan 1.11
---
## Latihan 3.1

**Code** : 
```bash
sudo du -ah /var/log/ 2> error.log | sort -rh | head -n 10 | tee large-logs.txt
```
**Output** : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ sudo du -ah /var/log/ 2> error.log | sort -rh | head -n 10 | tee large-logs.txt
[sudo: authenticate] Password: 
164M	/var/log/
153M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040
153M	/var/log/journal
17M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064c1d52e587fc-5ef42ff014f628a2.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-60578.journal
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-1000@00064b8fc0103810-cff94e2a21a5401f.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-1000.journal
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b8fbe8c872c-be8487526acd0267.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b8736bfe1fe-cb01d9c1ac590429.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b69439b140b-de4223a8dea00cc1.journal~
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ ls
error.log  large-logs.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ cat error.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ cat large-logs.txt
164M	/var/log/
153M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040
153M	/var/log/journal
17M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064c1d52e587fc-5ef42ff014f628a2.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-60578.journal
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-1000@00064b8fc0103810-cff94e2a21a5401f.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/user-1000.journal
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b8fbe8c872c-be8487526acd0267.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b8736bfe1fe-cb01d9c1ac590429.journal~
8.1M	/var/log/journal/1aca63e713ba459fa935a6afa6e7a040/system@00064b69439b140b-de4223a8dea00cc1.journal~
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ 
```
---
## Latihan 3.2

**Code** : 
```bash
cut -d: -f1 /etc/passwd | sort | tee sorted-users.txt
```

**Output** :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ cut -d: -f1 /etc/passwd | sort | tee sorted-users.txt
_apt
_chrony
avahi
backup
bin
colord
cups-browsed
cups-pk-helper
daemon
dhcpcd
dnsmasq
fwupd-refresh
games
gdm
geoclue
gnome-initial-setup
gnome-remote-desktop
hplip
ibennn
irc
list
lp
mail
man
messagebus
news
nm-openvpn
nobody
pipewire
polkitd
proxy
root
rtkit
saned
speech-dispatcher
sssd
sync
sys
syslog
systemd-network
systemd-oom
systemd-resolve
tcpdump
tss
usbmux
uucp
uuidd
whoopsie
www-data
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ ls
error.log  large-logs.txt  sorted-users.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ cat sorted-users.txt
_apt
_chrony
avahi
backup
bin
colord
cups-browsed
cups-pk-helper
daemon
dhcpcd
dnsmasq
fwupd-refresh
games
gdm
geoclue
gnome-initial-setup
gnome-remote-desktop
hplip
ibennn
irc
list
lp
mail
man
messagebus
news
nm-openvpn
nobody
pipewire
polkitd
proxy
root
rtkit
saned
speech-dispatcher
sssd
sync
sys
syslog
systemd-network
systemd-oom
systemd-resolve
tcpdump
tss
usbmux
uucp
uuidd
whoopsie
www-data
```

---
## Latihan 3.3

**Code** : 

Membuat file Script
```bash
nano monitor.sh
```
Isi Script
```bash
for i in {1..12}
do
    echo "--- $(date) ---" | tee -a monitoring.log
    top -bn1 | grep "Cpu(s)" | tee -a monitoring.log
    free -m | grep "Mem" | tee -a monitoring.log
    echo "" | tee -a monitoring.log
    sleep 5
done
```
Beri izin
```bash
chmod +x monitor.sh
```
Run Script
```bash
./monitor.sh
```

**Output** : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ nano monitor.sh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ chmod +x monitor.sh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ ./monitor.sh
--- Tue Mar  3 19:11:29 WIB 2026 ---
%Cpu(s):  9.1 us,  4.5 sy,  0.0 ni, 86.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1811         355         128        1490        1571

--- Tue Mar  3 19:11:34 WIB 2026 ---
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:11:39 WIB 2026 ---
%Cpu(s):  0.0 us,  2.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:11:44 WIB 2026 ---
%Cpu(s):  0.0 us,  2.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:11:50 WIB 2026 ---
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:11:55 WIB 2026 ---
%Cpu(s):  0.0 us,  2.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:12:00 WIB 2026 ---
%Cpu(s):  2.3 us,  2.3 sy,  0.0 ni, 95.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:12:05 WIB 2026 ---
%Cpu(s):  2.2 us,  2.2 sy,  0.0 ni, 95.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         354         128        1491        1570

--- Tue Mar  3 19:12:11 WIB 2026 ---
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1812         353         128        1491        1570

--- Tue Mar  3 19:12:16 WIB 2026 ---
%Cpu(s):  0.0 us,  2.3 sy,  0.0 ni, 97.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1813         353         128        1491        1569

--- Tue Mar  3 19:12:21 WIB 2026 ---
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1813         353         128        1491        1569

--- Tue Mar  3 19:12:26 WIB 2026 ---
%Cpu(s):  0.0 us,  2.2 sy,  0.0 ni, 97.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
Mem:            3382        1813         353         128        1491        1569

```

---
## Latihan 3.4

**Code** :
```bash
find / -name "*.conf" 2> /dev/null | tee config-files.txt | wc -l
```

**Output** : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ find / -name "*.conf" 2> /dev/null | tee config-files.txt | wc -l
2740
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ ls
config-files.txt  error.log  large-logs.txt  monitor.sh  monitoring.log  sorted-users.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ cat config-files.txt
/home/ibennn/.config/btop/btop.conf
/home/ibennn/.config/neofetch/config.conf
/home/ibennn/snap/prompting-client/105/.config/fontconfig/fonts.conf
/home/ibennn/snap/snapd-desktop-integration/346/.config/fontconfig/fonts.conf
/home/ibennn/snap/snapd-desktop-integration/316/.config/fontconfig/fonts.conf
/var/log/installer/curtin-install/subiquity-curthooks.conf
/var/log/installer/curtin-install/subiquity-extract.conf
/var/log/installer/curtin-install/subiquity-initial.conf
/var/log/installer/curtin-install/subiquity-partitioning.conf
/var/log/installer/curtin-install/subiquity-curtin-apt.conf
/var/lib/ucf/cache/:etc:chrony:chrony.conf
/var/lib/ucf/cache/:etc:rsyslog.d:50-default.conf
/var/snap/prompting-client/common/fontconfig/fonts.conf
/var/snap/snap-store/common/fontconfig/fonts.conf
/var/snap/firefox/common/fontconfig/fonts.conf
/var/snap/snapd-desktop-integration/common/fontconfig/fonts.conf
/var/snap/desktop-security-center/common/fontconfig/fonts.conf
/usr/share/kdump-tools/kdump-tools.conf
/usr/share/dbus-1/session.conf
/usr/share/dbus-1/system.conf
/usr/share/dbus-1/system.d/org.freedesktop.UPower.PowerProfiles.conf
/usr/share/dbus-1/system.d/org.freedesktop.locale1.conf
/usr/share/dbus-1/system.d/dnsmasq.conf
/usr/share/dbus-1/system.d/org.freedesktop.GeoClue2.Agent.conf
/usr/share/dbus-1/system.d/bluetooth.conf
/usr/share/dbus-1/system.d/org.freedesktop.hostname1.conf
/usr/share/dbus-1/system.d/wpa_supplicant.conf
/usr/share/dbus-1/system.d/org.freedesktop.RealtimeKit1.conf
/usr/share/dbus-1/system.d/com.canonical.UbuntuAdvantage.conf
/usr/share/dbus-1/system.d/obex.conf
/usr/share/dbus-1/system.d/org.gnome.Sysprof3.conf
/usr/share/dbus-1/system.d/org.freedesktop.timedate1.conf
/usr/share/dbus-1/system.d/org.freedesktop.ModemManager1.conf
/usr/share/dbus-1/system.d/org.gnome.RemoteDesktop.conf
/usr/share/dbus-1/system.d/nm-priv-helper.conf
/usr/share/dbus-1/system.d/org.freedesktop.systemd1.conf
/usr/share/dbus-1/system.d/org.freedesktop.PolicyKit1.conf
/usr/share/dbus-1/system.d/org.freedesktop.Accounts.conf
/usr/share/dbus-1/system.d/nm-openvpn-service.conf
/usr/share/dbus-1/system.d/org.freedesktop.UDisks2.conf
/usr/share/dbus-1/system.d/org.freedesktop.NetworkManager.conf
/usr/share/dbus-1/system.d/nm-dispatcher.conf
/usr/share/dbus-1/system.d/net.hadess.SwitcherooControl.conf
/usr/share/dbus-1/system.d/net.hadess.PowerProfiles.conf
/usr/share/dbus-1/system.d/org.freedesktop.bolt.conf
/usr/share/dbus-1/system.d/org.freedesktop.GeoClue2.conf
/usr/share/dbus-1/system.d/net.reactivated.Fprint.conf
/usr/share/dbus-1/system.d/org.freedesktop.resolve1.conf
/usr/share/dbus-1/system.d/org.freedesktop.network1.conf
/usr/share/dbus-1/system.d/snapd.system-services.conf
/usr/share/dbus-1/system.d/io.netplan.Netplan.conf
/usr/share/dbus-1/system.d/avahi-dbus.conf
/usr/share/dbus-1/system.d/net.hadess.SensorProxy.conf
/usr/share/dbus-1/system.d/org.freedesktop.PackageKit.conf
/usr/share/dbus-1/system.d/gdm.conf
/usr/share/dbus-1/system.d/org.freedesktop.UPower.conf
/usr/share/dbus-1/system.d/systemd-localed-read-only.conf
/usr/share/dbus-1/system.d/org.freedesktop.login1.conf
/usr/share/dbus-1/system.d/org.freedesktop.ColorManager.conf
/usr/share/dbus-1/system.d/org.freedesktop.oom1.conf
/usr/share/dbus-1/system.d/com.ubuntu.UnattendedUpgrade.conf
/usr/share/dbus-1/system.d/nm-pptp-service.conf
/usr/share/dbus-1/system.d/org.freedesktop.fwupd.conf
/usr/share/dbus-1/session.d/snapd.session-services.conf
/usr/share/gnome-remote-desktop/grd.conf
/usr/share/chrony/chrony.conf
/usr/share/defaults/at-spi2/accessibility.conf
/usr/share/gnome-initial-setup/vendor.conf
/usr/share/sssd/sssd.api.conf
/usr/share/sssd/sssd.api.d/sssd-ipa.conf
/usr/share/sssd/sssd.api.d/sssd-simple.conf
/usr/share/sssd/sssd.api.d/sssd-krb5.conf
/usr/share/sssd/sssd.api.d/sssd-proxy.conf
/usr/share/sssd/sssd.api.d/sssd-files.conf
/usr/share/sssd/sssd.api.d/sssd-ldap.conf
/usr/share/sssd/sssd.api.d/sssd-ad.conf
/usr/share/wireplumber/wireplumber.conf.d/alsa-vm.conf
/usr/share/wireplumber/wireplumber.conf
/usr/share/xdg-desktop-portal/gnome-portals.conf
/usr/share/upstart/sessions/session-migration.conf
/usr/share/im-config/data/60_thai.conf
/usr/share/im-config/data/80_kinput2.conf
/usr/share/im-config/data/30_maliit.conf
/usr/share/im-config/data/23_fcitx5.conf
/usr/share/im-config/data/24_uim.conf
/usr/share/im-config/data/25_hime.conf
/usr/share/im-config/data/02_cjkv.conf
/usr/share/im-config/data/22_fcitx.conf
/usr/share/im-config/data/01_auto.conf
/usr/share/im-config/data/90_missing.conf
/usr/share/im-config/data/26_gcin.conf
/usr/share/im-config/data/00_default.conf
/usr/share/im-config/data/48_scim.conf
/usr/share/im-config/data/90_custom.conf
/usr/share/im-config/data/78_none.conf
/usr/share/im-config/data/90_bogus.conf
/usr/share/im-config/data/80_xsunpinyin.conf
/usr/share/im-config/data/79_xim.conf
/usr/share/im-config/data/21_ibus.conf
/usr/share/im-config/data/09_REMOVE.conf
/usr/share/ufw/ufw.conf
/usr/share/ipp-usb/quirks/blacklist.conf
/usr/share/ipp-usb/quirks/HP.conf
/usr/share/ipp-usb/quirks/default.conf
/usr/share/ipp-usb/quirks/Pantum.conf
/usr/share/ipp-usb/quirks/Canon.conf
/usr/share/pipewire/client.conf.avail/20-upmix.conf
/usr/share/pipewire/pipewire.conf
/usr/share/pipewire/pipewire-avb.conf
/usr/share/pipewire/client.conf
/usr/share/pipewire/jack.conf
/usr/share/pipewire/pipewire-pulse.conf
/usr/share/pipewire/pipewire.conf.avail/10-rates.conf
/usr/share/pipewire/pipewire.conf.avail/20-upmix.conf
/usr/share/pipewire/pipewire.conf.avail/50-raop.conf
/usr/share/pipewire/pipewire-aes67.conf
/usr/share/pipewire/pipewire-pulse.conf.avail/20-upmix.conf
/usr/share/pipewire/filter-chain/sink-make-LFE.conf
/usr/share/pipewire/filter-chain/source-rnnoise.conf
/usr/share/pipewire/filter-chain/sink-eq6.conf
/usr/share/pipewire/filter-chain/sink-upmix-5.1-filter.conf
/usr/share/pipewire/filter-chain/demonic.conf
/usr/share/pipewire/filter-chain/sink-matrix-spatialiser.conf
/usr/share/pipewire/filter-chain/source-duplicate-FL.conf
/usr/share/pipewire/filter-chain/sink-virtual-surround-5.1-kemar.conf
/usr/share/pipewire/filter-chain/sink-mix-FL-FR.conf
/usr/share/pipewire/filter-chain/sink-dolby-surround.conf
/usr/share/pipewire/filter-chain/sink-virtual-surround-7.1-hesuvi.conf
/usr/share/pipewire/minimal.conf
/usr/share/pipewire/filter-chain.conf
/usr/share/dnsmasq-base/trust-anchors.conf
/usr/share/speech-dispatcher/conf/modules/espeak-ng.conf
/usr/share/speech-dispatcher/conf/modules/cicero.conf
/usr/share/speech-dispatcher/conf/modules/espeak.conf
/usr/share/speech-dispatcher/conf/modules/festival.conf
/usr/share/speech-dispatcher/conf/modules/espeak-ng-mbrola.conf
/usr/share/speech-dispatcher/conf/speechd.conf
/usr/share/speech-dispatcher/conf/clients/emacs.conf
/usr/share/libc-bin/nsswitch.conf
/usr/share/appstream/appstream.conf
/usr/share/spa-0.2/bluez5/bluez-hardware.conf
/usr/share/drirc.d/00-mesa-defaults.conf
/usr/share/drirc.d/00-radv-defaults.conf
/usr/share/rsyslog/50-default.conf
/usr/share/doc/sssd-common/examples/sssd-example.conf
/usr/share/doc/rsync/examples/rsyncd.conf
/usr/share/doc/openvpn/examples/sample-config-files/client.conf
/usr/share/doc/openvpn/examples/sample-config-files/server.conf
/usr/share/doc/libnet-ssleay-perl/examples/req.conf
/usr/share/doc/sudo/examples/syslog.conf
/usr/share/doc/sudo/examples/sudo_logsrvd.conf
/usr/share/doc/sudo/examples/pam.conf
/usr/share/doc/sudo/examples/cvtsudoers.conf
/usr/share/doc/sudo/examples/sudo.conf
/usr/share/doc/busybox-static/examples/udhcp/udhcpd.conf
/usr/share/doc/busybox-static/examples/mdev_fat.conf
/usr/share/doc/busybox-static/examples/mdev.conf
/usr/share/doc/dhcpcd-base/examples/DHCPv6-PD_dhcpcd.conf
/usr/share/doc/libcups2t64/examples/client.conf
/usr/share/doc/cups-daemon/examples/cups-socket.public.conf
/usr/share/doc/cups-daemon/examples/cups-socket.localhost.conf
/usr/share/doc/wpasupplicant/examples/ieee8021x.conf
/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf
/usr/share/doc/wpasupplicant/examples/wpa2-eap-ccmp.conf
/usr/share/doc/wpasupplicant/examples/wpa-roam.conf
/usr/share/doc/wpasupplicant/examples/wep.conf
/usr/share/doc/wpasupplicant/examples/plaintext.conf
/usr/share/doc/wpasupplicant/examples/openCryptoki.conf
/usr/share/doc/wpasupplicant/examples/udhcpd-p2p.conf
/usr/share/doc/wpasupplicant/examples/wpa-psk-tkip.conf
/usr/share/doc/apt/examples/apt.conf
/usr/share/doc/rsyslog/examples/rsyslog.d/xconsole.conf
/usr/share/doc/rsyslog/examples/rsyslog.d/console.conf
/usr/share/doc/rsyslog/examples/tmpfiles.d/xconsole.conf
/usr/share/doc/network-manager/examples/nm-conf.d/30-anon.conf
/usr/share/doc/network-manager/examples/nm-conf.d/31-mac-addr-change.conf
/usr/share/doc/network-manager/examples/server.conf
/usr/share/doc/adduser/examples/adduser.conf
/usr/share/doc/adduser/examples/adduser.local.conf
/usr/share/doc/adduser/examples/deluser.conf
/usr/share/doc/gpgconf/examples/gpgconf.conf
/usr/share/doc/gnupg/examples/common.conf
/usr/share/doc/gnupg/examples/gpgconf.conf
/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
/usr/share/pnm2ppa/pnm2ppa.conf
/usr/share/fontconfig/conf.avail/11-lcdfilter-none.conf
/usr/share/fontconfig/conf.avail/10-scale-bitmap-fonts.conf
/usr/share/fontconfig/conf.avail/69-language-selector-zh-tw.conf
/usr/share/fontconfig/conf.avail/49-sansserif.conf
/usr/share/fontconfig/conf.avail/60-generic.conf
/usr/share/fontconfig/conf.avail/urw-nimbus-sans.conf
/usr/share/fontconfig/conf.avail/10-autohint.conf
/usr/share/fontconfig/conf.avail/70-yes-bitmaps.conf
/usr/share/fontconfig/conf.avail/urw-z003.conf
/usr/share/fontconfig/conf.avail/05-reset-dirs-sample.conf
/usr/share/fontconfig/conf.avail/urw-gothic.conf
/usr/share/fontconfig/conf.avail/10-hinting-slight.conf
/usr/share/fontconfig/conf.avail/70-no-bitmaps.conf
/usr/share/fontconfig/conf.avail/urw-fallback-backwards.conf
/usr/share/fontconfig/conf.avail/urw-d050000l.conf
/usr/share/fontconfig/conf.avail/urw-p052.conf
/usr/share/fontconfig/conf.avail/10-hinting-medium.conf
/usr/share/fontconfig/conf.avail/48-spacing.conf
/usr/share/fontconfig/conf.avail/10-no-antialias.conf
/usr/share/fontconfig/conf.avail/urw-nimbus-mono-ps.conf
/usr/share/fontconfig/conf.avail/40-nonlatin.conf
/usr/share/fontconfig/conf.avail/10-sub-pixel-rgb.conf
/usr/share/fontconfig/conf.avail/11-lcdfilter-light.conf
/usr/share/fontconfig/conf.avail/69-language-selector-zh-cn.conf
/usr/share/fontconfig/conf.avail/60-latin.conf
/usr/share/fontconfig/conf.avail/09-autohint-if-no-hinting.conf
/usr/share/fontconfig/conf.avail/69-unifont.conf
/usr/share/fontconfig/conf.avail/45-generic.conf
/usr/share/fontconfig/conf.avail/65-fonts-persian.conf
/usr/share/fontconfig/conf.avail/urw-fallback-generics.conf
/usr/share/fontconfig/conf.avail/90-synthetic.conf
/usr/share/fontconfig/conf.avail/64-language-selector-cjk-prefer.conf
/usr/share/fontconfig/conf.avail/urw-c059.conf
/usr/share/fontconfig/conf.avail/99-language-selector-zh.conf
/usr/share/fontconfig/conf.avail/70-force-bitmaps.conf
/usr/share/fontconfig/conf.avail/70-no-bitmaps-and-emoji.conf
/usr/share/fontconfig/conf.avail/80-delicious.conf
/usr/share/fontconfig/conf.avail/10-hinting-none.conf
/usr/share/fontconfig/conf.avail/10-sub-pixel-vbgr.conf
/usr/share/fontconfig/conf.avail/70-no-bitmaps-except-emoji.conf
/usr/share/fontconfig/conf.avail/10-sub-pixel-bgr.conf
/usr/share/fontconfig/conf.avail/70-fonts-noto-cjk.conf
/usr/share/fontconfig/conf.avail/10-unhinted.conf
/usr/share/fontconfig/conf.avail/65-khmer.conf
/usr/share/fontconfig/conf.avail/51-local.conf
/usr/share/fontconfig/conf.avail/45-latin.conf
/usr/share/fontconfig/conf.avail/53-monospace-lcd-filter.conf
/usr/share/fontconfig/conf.avail/urw-nimbus-roman.conf
/usr/share/fontconfig/conf.avail/11-lcdfilter-legacy.conf
/usr/share/fontconfig/conf.avail/10-sub-pixel-vrgb.conf
/usr/share/fontconfig/conf.avail/71-ubuntulegacy.conf
/usr/share/fontconfig/conf.avail/25-unhint-nonlatin.conf
/usr/share/fontconfig/conf.avail/65-nonlatin.conf
/usr/share/fontconfig/conf.avail/69-language-selector-zh-sg.conf
/usr/share/fontconfig/conf.avail/30-metric-aliases.conf
/usr/share/fontconfig/conf.avail/69-language-selector-zh-mo.conf
/usr/share/fontconfig/conf.avail/30-cjk-aliases.conf
/usr/share/fontconfig/conf.avail/10-yes-antialias.conf
/usr/share/fontconfig/conf.avail/20-unhint-small-vera.conf
/usr/share/fontconfig/conf.avail/11-lcdfilter-default.conf
/usr/share/fontconfig/conf.avail/69-language-selector-zh-hk.conf
/usr/share/fontconfig/conf.avail/10-sub-pixel-none.conf
/usr/share/fontconfig/conf.avail/10-hinting-full.conf
/usr/share/fontconfig/conf.avail/69-language-selector-ja.conf
/usr/share/fontconfig/conf.avail/urw-standard-symbols-ps.conf
/usr/share/fontconfig/conf.avail/urw-fallback-specifics.conf
/usr/share/fontconfig/conf.avail/56-language-selector-prefer.conf
/usr/share/fontconfig/conf.avail/35-lang-normalize.conf
/usr/share/fontconfig/conf.avail/50-user.conf
/usr/share/fontconfig/conf.avail/urw-bookman.conf
/usr/share/glycin-loaders/2+/conf.d/glycin-jxl.conf
/usr/share/glycin-loaders/2+/conf.d/glycin-svg.conf
/usr/share/glycin-loaders/2+/conf.d/glycin-heif.conf
/usr/share/glycin-loaders/2+/conf.d/glycin-image-rs.conf
/usr/share/debconf/debconf.conf
/usr/share/ModemManager/mm-foxconn-t77w968-carrier-mapping.conf
/usr/share/alsa-card-profile/mixer/profile-sets/maudio-fasttrack-pro.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-komplete-audio6.conf
/usr/share/alsa-card-profile/mixer/profile-sets/cmedia-high-speed-true-hdaudio.conf
/usr/share/alsa-card-profile/mixer/profile-sets/hdmi-ac3.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktorkontrol-s4.conf
/usr/share/alsa-card-profile/mixer/profile-sets/default.conf
/usr/share/alsa-card-profile/mixer/profile-sets/sb-omni-surround-5.1.conf
/usr/share/alsa-card-profile/mixer/profile-sets/asus-xonar-se.conf
/usr/share/alsa-card-profile/mixer/profile-sets/usb-gaming-headset.conf
/usr/share/alsa-card-profile/mixer/profile-sets/dell-dock-tb16-usb-audio.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio2.conf
/usr/share/alsa-card-profile/mixer/profile-sets/simple-headphones-mic.conf
/usr/share/alsa-card-profile/mixer/profile-sets/texas-instruments-pcm2902.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio8dj.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-korecontroller.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio6.conf
/usr/share/alsa-card-profile/mixer/profile-sets/analog-only.conf
/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-audio-module.conf
/usr/share/alsa-card-profile/mixer/profile-sets/audigy.conf
/usr/share/alsa-card-profile/mixer/profile-sets/9999-custom.conf
/usr/share/alsa-card-profile/mixer/profile-sets/sennheiser-gsx.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio4dj.conf
/usr/share/alsa-card-profile/mixer/profile-sets/steelseries-arctis-common-usb-audio.conf
/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-120w-g2.conf
/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker.conf
/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio10.conf
/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker-and-int-mic.conf
/usr/share/alsa-card-profile/mixer/profile-sets/kinect-audio.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-headset-mic.conf
/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-game-common.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-5.conf
/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-mono.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-headphone-mic.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-tvtuner.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-1.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-video.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-mic-line.conf
/usr/share/alsa-card-profile/mixer/paths/audigy-analog-output.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-chat.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-front-mic.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-6.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones-2.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-dock-mic.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones.conf
/usr/share/alsa-card-profile/mixer/paths/virtual-surround-7.1.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-7.conf
/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-stereo.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic-always.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-linein.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-rear-mic.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-8.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-mono.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-aux.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-0.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-3.conf
/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-chat-common.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-9.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-fm.conf
/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-input.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input.conf
/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-output.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-mic.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-4.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-lineout.conf
/usr/share/alsa-card-profile/mixer/paths/audigy-analog-output-mirror.conf
/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-input.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-10.conf
/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker-always.conf
/usr/share/alsa-card-profile/mixer/paths/hdmi-output-2.conf
/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic.conf
/usr/share/alsa/cards/RME9652.conf
/usr/share/alsa/cards/pistachio-card.conf
/usr/share/alsa/cards/CMI8338.conf
/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/usr/share/alsa/cards/AU8820.conf
/usr/share/alsa/cards/VIA8233.conf
/usr/share/alsa/cards/CS46xx.conf
/usr/share/alsa/cards/Echo_Echo3G.conf
/usr/share/alsa/cards/USB-Audio.conf
/usr/share/alsa/cards/ATIIXP-MODEM.conf
/usr/share/alsa/cards/CA0106.conf
/usr/share/alsa/cards/FireWave.conf
/usr/share/alsa/cards/ATIIXP.conf
/usr/share/alsa/cards/ICH.conf
/usr/share/alsa/cards/PC-Speaker.conf
/usr/share/alsa/cards/ICH-MODEM.conf
/usr/share/alsa/cards/VIA8233A.conf
/usr/share/alsa/cards/PMac.conf
/usr/share/alsa/cards/HDA-Intel.conf
/usr/share/alsa/cards/FM801.conf
/usr/share/alsa/cards/AACI.conf
/usr/share/alsa/cards/AU8810.conf
/usr/share/alsa/cards/PMacToonie.conf
/usr/share/alsa/cards/VXPocket440.conf
/usr/share/alsa/cards/Audigy.conf
/usr/share/alsa/cards/YMF744.conf
/usr/share/alsa/cards/Aureon71.conf
/usr/share/alsa/cards/CMI8788.conf
/usr/share/alsa/cards/CMI8338-SWIEC.conf
/usr/share/alsa/cards/EMU10K1.conf
/usr/share/alsa/cards/RME9636.conf
/usr/share/alsa/cards/CMI8738-MC6.conf
/usr/share/alsa/cards/PS3.conf
/usr/share/alsa/cards/ENS1370.conf
/usr/share/alsa/cards/aliases.conf
/usr/share/alsa/cards/ENS1371.conf
/usr/share/alsa/cards/GUS.conf
/usr/share/alsa/cards/VX222.conf
/usr/share/alsa/cards/Audigy2.conf
/usr/share/alsa/cards/AU8830.conf
/usr/share/alsa/cards/ICE1712.conf
/usr/share/alsa/cards/Aureon51.conf
/usr/share/alsa/cards/Maestro3.conf
/usr/share/alsa/cards/VXPocket.conf
/usr/share/alsa/cards/SB-XFi.conf
/usr/share/alsa/cards/FWSpeakers.conf
/usr/share/alsa/cards/NFORCE.conf
/usr/share/alsa/cards/ICE1724.conf
/usr/share/alsa/cards/ICH4.conf
/usr/share/alsa/cards/CMI8738-MC8.conf
/usr/share/alsa/cards/HdmiLpeAudio.conf
/usr/share/alsa/cards/VIA8237.conf
/usr/share/alsa/cards/Loopback.conf
/usr/share/alsa/cards/EMU10K1X.conf
/usr/share/alsa/cards/ES1968.conf
/usr/share/alsa/cards/TRID4DWAVENX.conf
/usr/share/alsa/cards/vc4-hdmi.conf
/usr/share/alsa/cards/SI7018.conf
/usr/share/alsa/cards/VIA686A.conf
/usr/share/alsa/topology/bxtrt298/bxt_i2s.conf
/usr/share/alsa/topology/broadwell/broadwell.conf
/usr/share/alsa/topology/sklrt286/skl_i2s.conf
/usr/share/alsa/topology/hda-dsp/skl_hda_dsp_generic-tplg.conf
/usr/share/alsa/pcm/dmix.conf
/usr/share/alsa/pcm/surround71.conf
/usr/share/alsa/pcm/iec958.conf
/usr/share/alsa/pcm/default.conf
/usr/share/alsa/pcm/surround50.conf
/usr/share/alsa/pcm/rear.conf
/usr/share/alsa/pcm/surround41.conf
/usr/share/alsa/pcm/side.conf
/usr/share/alsa/pcm/surround51.conf
/usr/share/alsa/pcm/dsnoop.conf
/usr/share/alsa/pcm/surround40.conf
/usr/share/alsa/pcm/surround21.conf
/usr/share/alsa/pcm/dpl.conf
/usr/share/alsa/pcm/hdmi.conf
/usr/share/alsa/pcm/front.conf
/usr/share/alsa/pcm/modem.conf
/usr/share/alsa/pcm/center_lfe.conf
/usr/share/alsa/alsa.conf.d/50-pipewire.conf
/usr/share/alsa/alsa.conf.d/99-pipewire-default.conf
/usr/share/alsa/ctl/default.conf
/usr/share/alsa/alsa.conf
/usr/share/alsa/ucm2/Allwinner/A64/PinePhone/PinePhone.conf
/usr/share/alsa/ucm2/Allwinner/A64/PinePhone/VoiceCall.conf
/usr/share/alsa/ucm2/Allwinner/A64/PinePhone/HiFi.conf
/usr/share/alsa/ucm2/AMD/acp3x-es83xx/HiFi.conf
/usr/share/alsa/ucm2/AMD/acp3x-es83xx/acp3x-es83xx.conf
/usr/share/alsa/ucm2/AMD/acp5x/HiFi.conf
/usr/share/alsa/ucm2/AMD/acp5x/acp5x.conf
/usr/share/alsa/ucm2/AMD/acp3xalc5682m98/HiFi.conf
/usr/share/alsa/ucm2/AMD/acp3xalc5682m98/acp3xalc5682m98.conf
/usr/share/alsa/ucm2/AMD/acpd7219m98357/acpd7219m98357.conf
/usr/share/alsa/ucm2/AMD/acpd7219m98357/HiFi.conf
/usr/share/alsa/ucm2/blobs/sof/product_configs/AAEON/UPX-TGL01.conf
/usr/share/alsa/ucm2/Librem_5/Librem_5.conf
/usr/share/alsa/ucm2/Librem_5/wm8962.conf
/usr/share/alsa/ucm2/Librem_5/HiFi.conf
/usr/share/alsa/ucm2/Samsung/snow/HiFi.conf
/usr/share/alsa/ucm2/Samsung/snow/snow.conf
/usr/share/alsa/ucm2/Rockchip/max98090/HiFi.conf
/usr/share/alsa/ucm2/Rockchip/max98090/max98090.conf
/usr/share/alsa/ucm2/Rockchip/es8316/es8316.conf
/usr/share/alsa/ucm2/Rockchip/es8316/HiFi.conf
/usr/share/alsa/ucm2/Rockchip/rk3588-es8316/HiFi.conf
/usr/share/alsa/ucm2/Rockchip/rk3588-es8316/rk3588-es8316.conf
/usr/share/alsa/ucm2/Rockchip/rk3399-gru-sound/HiFi.conf
/usr/share/alsa/ucm2/Rockchip/rk3399-gru-sound/rk3399-gru-sound.conf
/usr/share/alsa/ucm2/Rockchip/rk817-sound/HiFi.conf
/usr/share/alsa/ucm2/Rockchip/rk817-sound/rk817-sound.conf
/usr/share/alsa/ucm2/ucm.conf
/usr/share/alsa/ucm2/module/snd_soc_omap_abe_twl6040.conf
/usr/share/alsa/ucm2/module/snd_soc_sdm845.conf
/usr/share/alsa/ucm2/module/snd_soc_apq8096.conf
/usr/share/alsa/ucm2/module/snd_soc_tegra_alc5632.conf
/usr/share/alsa/ucm2/module/snd_soc_apq8016_sbc.conf
/usr/share/alsa/ucm2/module/snd_soc_tegra_max98090.conf
/usr/share/alsa/ucm2/module/snd_soc_rk3399_gru_sound.conf
/usr/share/alsa/ucm2/module/snd_soc_rockchip_max98090.conf
/usr/share/alsa/ucm2/module/snd_soc_snow.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/abe-twl6040.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/FMAnalog.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/Voice.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/HiFiLP.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/SDP4430.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/VoiceCall.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/HiFi.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/SDP4430/Record.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/FMAnalog.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/Voice.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/HiFiLP.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/VoiceCall.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/Pandaboard.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/HiFi.conf
/usr/share/alsa/ucm2/OMAP/abe-twl6040/Pandaboard/Record.conf
/usr/share/alsa/ucm2/PineTab/HiFi.conf
/usr/share/alsa/ucm2/PineTab/PineTab.conf
/usr/share/alsa/ucm2/lib/card-init.conf
/usr/share/alsa/ucm2/lib/ctl-remap.conf
/usr/share/alsa/ucm2/lib/generic.conf
/usr/share/alsa/ucm2/conf.d/SOF/SOF.conf
/usr/share/alsa/ucm2/conf.d/chtmax98090/chtmax98090.conf
/usr/share/alsa/ucm2/conf.d/sm8650/SM8650-QRD.conf
/usr/share/alsa/ucm2/conf.d/sm8650/SM8650-MTP.conf
/usr/share/alsa/ucm2/conf.d/broxton-rt298/broxton-rt298.conf
/usr/share/alsa/ucm2/conf.d/sof-essx8336/sof-essx8336.conf
/usr/share/alsa/ucm2/conf.d/sdm845/DB845c.conf
/usr/share/alsa/ucm2/conf.d/sdm845/LENOVO-81JL-LenovoYOGAC630_13Q50-LNVNB161216.conf
/usr/share/alsa/ucm2/conf.d/mt8192_mt6359/mt8192_mt6359_rt1015p_rt5682.conf
/usr/share/alsa/ucm2/conf.d/amd-soundwire/amd-soundwire.conf
/usr/share/alsa/ucm2/conf.d/sof-mt8390-evk/sof-mt8390-evk.conf
/usr/share/alsa/ucm2/conf.d/bytcr-rt5651/bytcr-rt5651.conf
/usr/share/alsa/ucm2/conf.d/tegra-hda/tegra-hda.conf
/usr/share/alsa/ucm2/conf.d/sof-m8195_r1019/sof-m8195_r1019_5682s.conf
/usr/share/alsa/ucm2/conf.d/sof-ehl-rt5660/sof-ehl-rt5660.conf
/usr/share/alsa/ucm2/conf.d/acp-pdm-mach/acp-pdm-mach.conf
/usr/share/alsa/ucm2/conf.d/bytcr-wm5102/bytcr-wm5102.conf
/usr/share/alsa/ucm2/conf.d/sc8280xp/sc8280xp.conf
/usr/share/alsa/ucm2/conf.d/mt8365-evk/mt8365-evk.conf
/usr/share/alsa/ucm2/conf.d/sm8250/Qualcomm-RB5-WSA8815-Speakers-DMIC0.conf
/usr/share/alsa/ucm2/conf.d/sof-hda-dsp/sof-hda-dsp.conf
/usr/share/alsa/ucm2/conf.d/sof-hda-dsp/sof-skl_hda_card.conf
/usr/share/alsa/ucm2/conf.d/mtk-rt5650/mtk-rt5650.conf
/usr/share/alsa/ucm2/conf.d/hda-dsp/hda-dsp.conf
/usr/share/alsa/ucm2/conf.d/DB820c/DB820c.conf
/usr/share/alsa/ucm2/conf.d/acp3x-es83xx/acp3x-es83xx.conf
/usr/share/alsa/ucm2/conf.d/HDA-Intel/HDA-Intel.conf
/usr/share/alsa/ucm2/conf.d/acp62/acp62.conf
/usr/share/alsa/ucm2/conf.d/mt8390-evk/mt8390-evk.conf
/usr/share/alsa/ucm2/conf.d/rockchip_es8316/rockchip_es8316.conf
/usr/share/alsa/ucm2/conf.d/bdw-rt5677/bdw-rt5677.conf
/usr/share/alsa/ucm2/conf.d/USB-Audio/USB-Audio.conf
/usr/share/alsa/ucm2/conf.d/broadwell-rt286/broadwell-rt286.conf
/usr/share/alsa/ucm2/conf.d/cht-bsw-rt5672/cht-bsw-rt5672.conf
/usr/share/alsa/ucm2/conf.d/DB410c/DB410c.conf
/usr/share/alsa/ucm2/conf.d/sof-mt8365-evk/sof-mt8365-evk.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus Transformer Pad TF300TL RT5631.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus Transformer Infinity TF700T RT5631.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus Transformer Prime TF201 RT5631.conf
/usr/share/alsa/ucm2/conf.d/tegra/Acer Iconia Tab A500 WM8903.conf
/usr/share/alsa/ucm2/conf.d/tegra/GoogleNyanBlaze.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus EeePad Slider WM8903.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus Transformer Pad TF300T WM8903.conf
/usr/share/alsa/ucm2/conf.d/tegra/LG Optimus Vu MAX98089.conf
/usr/share/alsa/ucm2/conf.d/tegra/LG Optimus 4X HD MAX98089.conf
/usr/share/alsa/ucm2/conf.d/tegra/GoogleNyanBig.conf
/usr/share/alsa/ucm2/conf.d/tegra/ASUS Google Nexus 7 ALC5642.conf
/usr/share/alsa/ucm2/conf.d/tegra/Compal PAZ00.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus EeePad Transformer WM8903.conf
/usr/share/alsa/ucm2/conf.d/tegra/Asus Transformer Pad TF300TG RT5631.conf
/usr/share/alsa/ucm2/conf.d/sof-mt8395-evk/sof-mt8395-evk.conf
/usr/share/alsa/ucm2/conf.d/acp5x/Valve-Jupiter-1.conf
/usr/share/alsa/ucm2/conf.d/SC7180/sc7180-rt5682-max98357a-1mic.conf
/usr/share/alsa/ucm2/conf.d/SC7180/sc7180-adau7002-max98357a.conf
/usr/share/alsa/ucm2/conf.d/simple-card/rk817_ext.conf
/usr/share/alsa/ucm2/conf.d/simple-card/rk817_int.conf
/usr/share/alsa/ucm2/conf.d/simple-card/Librem 5 Devkit.conf
/usr/share/alsa/ucm2/conf.d/simple-card/PinePhone.conf
/usr/share/alsa/ucm2/conf.d/simple-card/Librem 5.conf
/usr/share/alsa/ucm2/conf.d/simple-card/rockchip,es8316-codec.conf
/usr/share/alsa/ucm2/conf.d/rk3588-es8316/rk3588-es8316.conf
/usr/share/alsa/ucm2/conf.d/x1e80100/X1E80100-CRD.conf
/usr/share/alsa/ucm2/conf.d/VEYRON-I2S/VEYRON-I2S.conf
/usr/share/alsa/ucm2/conf.d/chtrt5650/chtrt5650.conf
/usr/share/alsa/ucm2/conf.d/mt8395-evk/mt8395-evk.conf
/usr/share/alsa/ucm2/conf.d/chtnau8824/chtnau8824.conf
/usr/share/alsa/ucm2/conf.d/kblrt5660/kblrt5660.conf
/usr/share/alsa/ucm2/conf.d/sof-glkda7219ma/sof-glkda7219ma.conf
/usr/share/alsa/ucm2/conf.d/bytcht-cx2072x/bytcht-cx2072x.conf
/usr/share/alsa/ucm2/conf.d/mt8370-evk/mt8370-evk.conf
/usr/share/alsa/ucm2/conf.d/bytcr-rt5640/bytcr-rt5640.conf
/usr/share/alsa/ucm2/conf.d/sof-soundwire/sof-soundwire.conf
/usr/share/alsa/ucm2/conf.d/acp3xalc5682m98/acp3xalc5682m98.conf
/usr/share/alsa/ucm2/conf.d/sof-mt8195_r101/sof-mt8195_r1019_5682.conf
/usr/share/alsa/ucm2/conf.d/mt8195_demo/mt8195_demo.conf
/usr/share/alsa/ucm2/conf.d/gx-sound-card/LIBRETECH-CC.conf
/usr/share/alsa/ucm2/conf.d/gx-sound-card/GXL-P241.conf
/usr/share/alsa/ucm2/conf.d/skylake-rt286/skylake-rt286.conf
/usr/share/alsa/ucm2/conf.d/acp63/acp63.conf
/usr/share/alsa/ucm2/conf.d/acpd7219m98357/acpd7219m98357.conf
/usr/share/alsa/ucm2/conf.d/bytcht-es8316/bytcht-es8316.conf
/usr/share/alsa/ucm2/conf.d/acp/acp.conf
/usr/share/alsa/ucm2/conf.d/chtrt5645/chtrt5645.conf
/usr/share/alsa/ucm2/conf.d/acp6x/acp6x.conf
/usr/share/alsa/ucm2/conf.d/rk3399-gru-soun/rk3399-gru-soun.conf
/usr/share/alsa/ucm2/Qualcomm/sc7180/adau7002-max98357a/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sc7180/adau7002-max98357a/sc7180-adau7002-max98357a.conf
/usr/share/alsa/ucm2/Qualcomm/sc7180/rt5682-max98357a/sc7180-rt5682-max98357a-1mic.conf
/usr/share/alsa/ucm2/Qualcomm/sc7180/rt5682-max98357a/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sc7180/rt5682-max98357a/init.conf
/usr/share/alsa/ucm2/Qualcomm/sm8650/QRD/SM8650-QRD.conf
/usr/share/alsa/ucm2/Qualcomm/sm8650/QRD/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sm8650/MTP/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sm8650/MTP/SM8650-MTP.conf
/usr/share/alsa/ucm2/Qualcomm/sdm845/sdm845.conf
/usr/share/alsa/ucm2/Qualcomm/sdm845/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sdm845/HiFi-MM1.conf
/usr/share/alsa/ucm2/Qualcomm/sdm845/HDMI.conf
/usr/share/alsa/ucm2/Qualcomm/sdm845/Lenovo-YOGA-C630-13Q50.conf
/usr/share/alsa/ucm2/Qualcomm/sc8280xp/sc8280xp.conf
/usr/share/alsa/ucm2/Qualcomm/sc8280xp/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sc8280xp/LENOVO-X13s.conf
/usr/share/alsa/ucm2/Qualcomm/sm8250/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/sm8250/HDMI.conf
/usr/share/alsa/ucm2/Qualcomm/sm8250/Qualcomm-RB5-WSA8815-Speakers-DMIC0.conf
/usr/share/alsa/ucm2/Qualcomm/apq8096/apq8096.conf
/usr/share/alsa/ucm2/Qualcomm/apq8096/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/apq8096/HDMI.conf
/usr/share/alsa/ucm2/Qualcomm/apq8016-sbc/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/apq8016-sbc/HDMI.conf
/usr/share/alsa/ucm2/Qualcomm/apq8016-sbc/apq8016-sbc.conf
/usr/share/alsa/ucm2/Qualcomm/x1e80100/HiFi.conf
/usr/share/alsa/ucm2/Qualcomm/x1e80100/X1E80100-CRD.conf
/usr/share/alsa/ucm2/Amlogic/p241/p241-HiFi.conf
/usr/share/alsa/ucm2/Amlogic/p241/p241.conf
/usr/share/alsa/ucm2/USB-Audio/GoXLR/GoXLR-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/GoXLR/GoXLR.conf
/usr/share/alsa/ucm2/USB-Audio/USB-Audio.conf
/usr/share/alsa/ucm2/USB-Audio/Arturia/Minifuse-4.conf
/usr/share/alsa/ucm2/USB-Audio/Arturia/Minifuse-12.conf
/usr/share/alsa/ucm2/USB-Audio/Arturia/Minifuse-12-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Arturia/Minifuse-4-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Sony/Inzone-H9-H7-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Sony/Inzone-H9-H7.conf
/usr/share/alsa/ucm2/USB-Audio/Audient/Audient-iD4-0009.conf
/usr/share/alsa/ucm2/USB-Audio/Audient/Audient-iD4-HiFi-0003.conf
/usr/share/alsa/ucm2/USB-Audio/Audient/Audient-iD4-HiFi-0009.conf
/usr/share/alsa/ucm2/USB-Audio/Audient/Audient-iD4-0003.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC204HD.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC202HD.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC404HD-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/Flow8-Recording.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/Flow8-Recording-Hifi.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC204HD-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC202HD-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/Flow8-Streaming.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/UMC404HD.conf
/usr/share/alsa/ucm2/USB-Audio/Behringer/Flow8-Streaming-Hifi.conf
/usr/share/alsa/ucm2/USB-Audio/AllenAndHeath/Zedi10-Hifi.conf
/usr/share/alsa/ucm2/USB-Audio/AllenAndHeath/Zedi10.conf
/usr/share/alsa/ucm2/USB-Audio/UniversalAudio/Volt2-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/UniversalAudio/Volt2.conf
/usr/share/alsa/ucm2/USB-Audio/Roland/BridgeCast-Hifi.conf
/usr/share/alsa/ucm2/USB-Audio/Roland/BridgeCast.conf
/usr/share/alsa/ucm2/USB-Audio/Realtek/ALC4080.conf
/usr/share/alsa/ucm2/USB-Audio/Realtek/ALC1220-VB-Desktop-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Realtek/ALC4080-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Realtek/ALC1220-VB-Desktop.conf
/usr/share/alsa/ucm2/USB-Audio/Gigabyte/Aorus-Master-Main-Audio.conf
/usr/share/alsa/ucm2/USB-Audio/Gigabyte/Aorus-Master-Main-Audio-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M2-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M6.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M2.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M4-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M6-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/MOTU/M4.conf
/usr/share/alsa/ucm2/USB-Audio/SolidStateLabs/SSL2.conf
/usr/share/alsa/ucm2/USB-Audio/SolidStateLabs/SSL2-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Focusrite/Scarlett-2i-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Focusrite/Scarlett-2i.conf
/usr/share/alsa/ucm2/USB-Audio/Lenovo/ThinkStation-P620-Main.conf
/usr/share/alsa/ucm2/USB-Audio/Lenovo/ThinkStation-P620-Rear.conf
/usr/share/alsa/ucm2/USB-Audio/Lenovo/ThinkStation-P620-Rear-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Lenovo/ThinkStation-P620-Main-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/Desktop-Front.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/WD15-Dock.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/Desktop-Rear.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/Desktop-Rear-Line.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/Desktop-Front-Speaker-Headset.conf
/usr/share/alsa/ucm2/USB-Audio/Dell/WD15-Dock-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Rane/SL-1-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Rane/SL-1.conf
/usr/share/alsa/ucm2/USB-Audio/Digidesign/Digidesign-Mbox-3-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Digidesign/Digidesign-Mbox-3.conf
/usr/share/alsa/ucm2/USB-Audio/Steinberg/UR24C.conf
/usr/share/alsa/ucm2/USB-Audio/Steinberg/UR44-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Steinberg/UR44.conf
/usr/share/alsa/ucm2/USB-Audio/Steinberg/UR24C-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Common/HeadphonesOnly-HiFi.conf
/usr/share/alsa/ucm2/USB-Audio/Common/HeadphonesOnly.conf
/usr/share/alsa/ucm2/USB-Audio/NativeInstruments/Traktor-Kontrol-Z1-Mixer.conf
/usr/share/alsa/ucm2/USB-Audio/NativeInstruments/Traktor-Kontrol-Z1.conf
/usr/share/alsa/ucm2/platforms/bytcr/PlatformDisableSeq.conf
/usr/share/alsa/ucm2/platforms/bytcr/PlatformEnableSeq.conf
/usr/share/alsa/ucm2/HDA/HiFi.conf
/usr/share/alsa/ucm2/HDA/HiFi-analog.conf
/usr/share/alsa/ucm2/HDA/HiFi-acp.conf
/usr/share/alsa/ucm2/HDA/HDA-Capture-value.conf
/usr/share/alsa/ucm2/HDA/Hdmi.conf
/usr/share/alsa/ucm2/HDA/init.conf
/usr/share/alsa/ucm2/HDA/DualCodecs/DualCodecs.conf
/usr/share/alsa/ucm2/HDA/DualCodecs/HiFi.conf
/usr/share/alsa/ucm2/HDA/HDA.conf
/usr/share/alsa/ucm2/MediaTek/mt8195-sof/mt6359-rt1019-rt5682/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8195-sof/mt6359-rt1019-rt5682/init.conf
/usr/share/alsa/ucm2/MediaTek/mt8195-sof/mt6359-rt1019-rt5682/sof-mt8195-mt6359-rt1019-rt5682.conf
/usr/share/alsa/ucm2/MediaTek/mt8195-sof/init.conf
/usr/share/alsa/ucm2/MediaTek/mt8365-evk/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8365-evk/mt8365-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8365-evk/sof/SOF.conf
/usr/share/alsa/ucm2/MediaTek/mt8365-evk/sof/sof-mt8365-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8365-evk/init.conf
/usr/share/alsa/ucm2/MediaTek/mtk-rt5650/mtk-rt5650.conf
/usr/share/alsa/ucm2/MediaTek/mtk-rt5650/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mtk-rt5650/HDMI.conf
/usr/share/alsa/ucm2/MediaTek/mtk-rt5650/init.conf
/usr/share/alsa/ucm2/MediaTek/mt8390-evk/mt8390-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8390-evk/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8390-evk/sof/sof-mt8390-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8390-evk/init.conf
/usr/share/alsa/ucm2/MediaTek/sof-mt8395-evk/sof-mt8395-evk.conf
/usr/share/alsa/ucm2/MediaTek/sof-mt8395-evk/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8192/mt6359-rt1015p-rt5682/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8192/mt6359-rt1015p-rt5682/mt8192_mt6359_rt1015p_rt5682.conf
/usr/share/alsa/ucm2/MediaTek/mt8192/mt6359-rt1015p-rt5682/init.conf
/usr/share/alsa/ucm2/MediaTek/mt8395-evk/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8395-evk/mt8395-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8370-evk/mt8370-evk.conf
/usr/share/alsa/ucm2/MediaTek/mt8370-evk/HiFi.conf
/usr/share/alsa/ucm2/MediaTek/mt8195_demo/mt8195_demo.conf
/usr/share/alsa/ucm2/MediaTek/mt8195_demo/HiFi.conf
/usr/share/alsa/ucm2/NXP/iMX8/Librem_5/Librem 5.conf
/usr/share/alsa/ucm2/NXP/iMX8/Librem_5/HiFi.conf
/usr/share/alsa/ucm2/NXP/iMX8/Librem_5_Devkit/Librem 5 Devkit.conf
/usr/share/alsa/ucm2/NXP/iMX8/Librem_5_Devkit/HiFi.conf
/usr/share/alsa/ucm2/codecs/rt5672/DMIC1.conf
/usr/share/alsa/ucm2/codecs/rt5672/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5672/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/rt5672/MonoSpeaker.conf
/usr/share/alsa/ucm2/codecs/rt5672/DMIC2.conf
/usr/share/alsa/ucm2/codecs/rt5672/Speaker.conf
/usr/share/alsa/ucm2/codecs/rt5672/HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/rt715-sdca/init.conf
/usr/share/alsa/ucm2/codecs/wsa883x/SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa883x/init.conf
/usr/share/alsa/ucm2/codecs/wsa883x/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa883x/SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/DMIC0DisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/DMIC0EnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/HeadphoneMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/HeadphoneMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/SoundwireMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/SoundwireMic1EnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/tx-macro/SoundwireMic0EnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/Wsa1SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/four-speakers/init.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/Wsa2SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/Wsa2SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/init.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/wsa-macro/Wsa1SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/rx-macro/HeadphoneDisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/rx-macro/HeadphoneEnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/rx-macro/init.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/va-macro/DMIC0DisableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/va-macro/DMIC0EnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/va-macro/DMIC1EnableSeq.conf
/usr/share/alsa/ucm2/codecs/qcom-lpass/va-macro/DMIC1DisableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa884x/four-speakers/SpeakerSeq.conf
/usr/share/alsa/ucm2/codecs/wsa884x/four-speakers/init.conf
/usr/share/alsa/ucm2/codecs/wsa884x/four-speakers/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa884x/two-speakers/SpeakerSeq.conf
/usr/share/alsa/ucm2/codecs/wsa884x/two-speakers/init.conf
/usr/share/alsa/ucm2/codecs/wsa884x/two-speakers/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/hda/hdmi.conf
/usr/share/alsa/ucm2/codecs/max98090/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/max98090/InternalMic.conf
/usr/share/alsa/ucm2/codecs/max98090/Speaker.conf
/usr/share/alsa/ucm2/codecs/max98090/Headphones.conf
/usr/share/alsa/ucm2/codecs/max98090/HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/cs35l56/init.conf
/usr/share/alsa/ucm2/codecs/cs42l43-dmic/init.conf
/usr/share/alsa/ucm2/codecs/wcd937x/HeadphoneMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd937x/HeadphoneMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd937x/HeadphoneDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd937x/HeadphoneEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd937x/init.conf
/usr/share/alsa/ucm2/codecs/rt713-dmic/init.conf
/usr/share/alsa/ucm2/codecs/nau8824/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/nau8824/InternalMic.conf
/usr/share/alsa/ucm2/codecs/nau8824/DMIC1_2.conf
/usr/share/alsa/ucm2/codecs/nau8824/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/nau8824/MonoSpeaker.conf
/usr/share/alsa/ucm2/codecs/nau8824/Speaker.conf
/usr/share/alsa/ucm2/codecs/nau8824/HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/wm5102/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/wm5102/IN2-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/wm5102/IN1-InternalMic.conf
/usr/share/alsa/ucm2/codecs/wm5102/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/wm5102/IN3-InternalMic.conf
/usr/share/alsa/ucm2/codecs/wm5102/HPOut2-Speaker.conf
/usr/share/alsa/ucm2/codecs/wm5102/Speaker.conf
/usr/share/alsa/ucm2/codecs/wm5102/IN1-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/wcd939x/AnalogMic1EnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/AnalogMic5EnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/AnalogMic4EnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/HeadphoneMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/HeadphoneMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/HeadphoneDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/HeadphoneEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/init.conf
/usr/share/alsa/ucm2/codecs/wcd939x/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/AnalogMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd939x/AnalogMic3EnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd938x/HeadphoneMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd938x/HeadphoneMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd938x/HeadphoneDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd938x/HeadphoneEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd938x/init.conf
/usr/share/alsa/ucm2/codecs/rt700/init.conf
/usr/share/alsa/ucm2/codecs/rt712-dmic/init.conf
/usr/share/alsa/ucm2/codecs/rt721/init.conf
/usr/share/alsa/ucm2/codecs/rt5640/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5640/IN1-InternalMic.conf
/usr/share/alsa/ucm2/codecs/rt5640/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/rt5640/HeadsetMic2-IN1.conf
/usr/share/alsa/ucm2/codecs/rt5640/MonoSpeaker.conf
/usr/share/alsa/ucm2/codecs/rt5640/IN3-InternalMic.conf
/usr/share/alsa/ucm2/codecs/rt5640/DigitalMics.conf
/usr/share/alsa/ucm2/codecs/rt5640/init.conf
/usr/share/alsa/ucm2/codecs/rt5640/HeadPhones2.conf
/usr/share/alsa/ucm2/codecs/rt5640/Speaker.conf
/usr/share/alsa/ucm2/codecs/rt5640/HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/cx2072x/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/cx2072x/InternalMic.conf
/usr/share/alsa/ucm2/codecs/cx2072x/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/cx2072x/DisableSeq.conf
/usr/share/alsa/ucm2/codecs/cx2072x/Speaker.conf
/usr/share/alsa/ucm2/codecs/cx2072x/HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/rt713/init.conf
/usr/share/alsa/ucm2/codecs/wcd934x/SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/HeadphoneMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/HeadphoneMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/DefaultDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/HeadphoneDisableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/HeadphoneEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/init.conf
/usr/share/alsa/ucm2/codecs/wcd934x/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wcd934x/SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/cs35l56-bridge/init.conf
/usr/share/alsa/ucm2/codecs/es8316/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/es8316/IN2-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/es8316/IN1-InternalMic.conf
/usr/share/alsa/ucm2/codecs/es8316/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/es8316/IN2-InternalMic.conf
/usr/share/alsa/ucm2/codecs/es8316/MonoSpeaker.conf
/usr/share/alsa/ucm2/codecs/es8316/Speaker.conf
/usr/share/alsa/ucm2/codecs/es8316/IN1-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/cs42l43/init.conf
/usr/share/alsa/ucm2/codecs/wsa881x/SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa881x/DefaultEnableSeq.conf
/usr/share/alsa/ucm2/codecs/wsa881x/SpeakerDisableSeq.conf
/usr/share/alsa/ucm2/codecs/rt1318/init.conf
/usr/share/alsa/ucm2/codecs/rt722/init.conf
/usr/share/alsa/ucm2/codecs/rt5682/init.conf
/usr/share/alsa/ucm2/codecs/rt5651/DigitalMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5651/IN3-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/IN2-HeadsetMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/IN1-InternalMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/HeadPhones-swapped.conf
/usr/share/alsa/ucm2/codecs/rt5651/HeadPhones.conf
/usr/share/alsa/ucm2/codecs/rt5651/IN2-InternalMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/MonoSpeaker.conf
/usr/share/alsa/ucm2/codecs/rt5651/IN12-InternalMic.conf
/usr/share/alsa/ucm2/codecs/rt5651/init.conf
/usr/share/alsa/ucm2/codecs/rt5651/Speaker.conf
/usr/share/alsa/ucm2/codecs/rt711/init.conf
/usr/share/alsa/ucm2/codecs/rt715/init.conf
/usr/share/alsa/ucm2/codecs/da7219/init.conf
/usr/share/alsa/ucm2/codecs/rt712/init.conf
/usr/share/alsa/ucm2/codecs/rt711-sdca/init.conf
/usr/share/alsa/ucm2/codecs/rt5645/EnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/DigitalMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/SpeakerEnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/HSMicEnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/DisableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/init.conf
/usr/share/alsa/ucm2/codecs/rt5645/DigitalMicDisableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/AnalogMic.conf
/usr/share/alsa/ucm2/codecs/rt5645/HeadphonesEnableSeq.conf
/usr/share/alsa/ucm2/codecs/rt5645/HSMicDisableSeq.conf
/usr/share/alsa/ucm2/sof-soundwire/rt713.conf
/usr/share/alsa/ucm2/sof-soundwire/rt713-dmic.conf
/usr/share/alsa/ucm2/sof-soundwire/rt1320.conf
/usr/share/alsa/ucm2/sof-soundwire/cs35l56.conf
/usr/share/alsa/ucm2/sof-soundwire/rt712-dmic.conf
/usr/share/alsa/ucm2/sof-soundwire/cs42l43-dmic.conf
/usr/share/alsa/ucm2/sof-soundwire/rt715.conf
/usr/share/alsa/ucm2/sof-soundwire/rt711-sdca.conf
/usr/share/alsa/ucm2/sof-soundwire/rt700.conf
/usr/share/alsa/ucm2/sof-soundwire/sof-soundwire.conf
/usr/share/alsa/ucm2/sof-soundwire/HiFi.conf
/usr/share/alsa/ucm2/sof-soundwire/rt1308.conf
/usr/share/alsa/ucm2/sof-soundwire/rt1316.conf
/usr/share/alsa/ucm2/sof-soundwire/cs35l56-bridge.conf
/usr/share/alsa/ucm2/sof-soundwire/rt722.conf
/usr/share/alsa/ucm2/sof-soundwire/rt715-sdca.conf
/usr/share/alsa/ucm2/sof-soundwire/cs42l43.conf
/usr/share/alsa/ucm2/sof-soundwire/cs42l43-spk.conf
/usr/share/alsa/ucm2/sof-soundwire/Hdmi.conf
/usr/share/alsa/ucm2/sof-soundwire/rt712.conf
/usr/share/alsa/ucm2/sof-soundwire/dmic.conf
/usr/share/alsa/ucm2/sof-soundwire/rt5682.conf
/usr/share/alsa/ucm2/sof-soundwire/rt1318.conf
/usr/share/alsa/ucm2/sof-soundwire/rt721.conf
/usr/share/alsa/ucm2/sof-soundwire/rt711.conf
/usr/share/alsa/ucm2/common/pcm/split.conf
/usr/share/alsa/ucm2/common/pcm/hdmi.conf
/usr/share/alsa/ucm2/common/linked-card.conf
/usr/share/alsa/ucm2/common/ctl/led.conf
/usr/share/alsa/ucm2/common/ctl/remap.conf
/usr/share/alsa/ucm2/common/direct.conf
/usr/share/alsa/ucm2/common/direct-verb.conf
/usr/share/alsa/ucm2/common/linked.conf
/usr/share/alsa/ucm2/Intel/SOF/SOF.conf
/usr/share/alsa/ucm2/Intel/SOF/HiFi.conf
/usr/share/alsa/ucm2/Intel/chtmax98090/chtmax98090.conf
/usr/share/alsa/ucm2/Intel/chtmax98090/HiFi.conf
/usr/share/alsa/ucm2/Intel/broxton-rt298/HiFi.conf
/usr/share/alsa/ucm2/Intel/broxton-rt298/broxton-rt298.conf
/usr/share/alsa/ucm2/Intel/broxton-rt298/Hdmi.conf
/usr/share/alsa/ucm2/Intel/sof-essx8336/sof-essx8336.conf
/usr/share/alsa/ucm2/Intel/sof-essx8336/HiFi.conf
/usr/share/alsa/ucm2/Intel/sof-essx8336/Hdmi.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5651/bytcr-rt5651.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5651/HiFi-LongName.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5651/HiFi.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5651/HiFi-Components.conf
/usr/share/alsa/ucm2/Intel/sof-ehl-rt5660/sof-ehl-rt5660.conf
/usr/share/alsa/ucm2/Intel/sof-ehl-rt5660/HiFi.conf
/usr/share/alsa/ucm2/Intel/sof-ehl-rt5660/Hdmi.conf
/usr/share/alsa/ucm2/Intel/bytcr-wm5102/bytcr-wm5102.conf
/usr/share/alsa/ucm2/Intel/bytcr-wm5102/HiFi.conf
/usr/share/alsa/ucm2/Intel/sof-hda-dsp/sof-hda-dsp.conf
/usr/share/alsa/ucm2/Intel/sof-hda-dsp/HiFi-sof.conf
/usr/share/alsa/ucm2/Intel/sof-hda-dsp/HiFi.conf
/usr/share/alsa/ucm2/Intel/sof-hda-dsp/Hdmi.conf
/usr/share/alsa/ucm2/Intel/hda-dsp/Hdmi1.conf
/usr/share/alsa/ucm2/Intel/hda-dsp/HiFi.conf
/usr/share/alsa/ucm2/Intel/hda-dsp/Hdmi2.conf
/usr/share/alsa/ucm2/Intel/hda-dsp/hda-dsp.conf
/usr/share/alsa/ucm2/Intel/sof-glkda7219max/sof-glkda7219max.conf
/usr/share/alsa/ucm2/Intel/sof-glkda7219max/HiFi.conf
/usr/share/alsa/ucm2/Intel/sof-glkda7219max/Hdmi.conf
/usr/share/alsa/ucm2/Intel/bdw-rt5677/HiFi.conf
/usr/share/alsa/ucm2/Intel/bdw-rt5677/bdw-rt5677.conf
/usr/share/alsa/ucm2/Intel/broadwell-rt286/broadwell-rt286.conf
/usr/share/alsa/ucm2/Intel/broadwell-rt286/HiFi.conf
/usr/share/alsa/ucm2/Intel/cht-bsw-rt5672/HiFi.conf
/usr/share/alsa/ucm2/Intel/cht-bsw-rt5672/cht-bsw-rt5672.conf
/usr/share/alsa/ucm2/Intel/chtrt5650/chtrt5650.conf
/usr/share/alsa/ucm2/Intel/chtrt5650/HiFi.conf
/usr/share/alsa/ucm2/Intel/chtnau8824/chtnau8824.conf
/usr/share/alsa/ucm2/Intel/chtnau8824/HiFi.conf
/usr/share/alsa/ucm2/Intel/kblrt5660/kblrt5660.conf
/usr/share/alsa/ucm2/Intel/kblrt5660/Hdmi1.conf
/usr/share/alsa/ucm2/Intel/kblrt5660/HiFi.conf
/usr/share/alsa/ucm2/Intel/kblrt5660/Hdmi2.conf
/usr/share/alsa/ucm2/Intel/bytcht-cx2072x/HiFi.conf
/usr/share/alsa/ucm2/Intel/bytcht-cx2072x/bytcht-cx2072x.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5640/HiFi-LongName.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5640/HiFi.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5640/bytcr-rt5640.conf
/usr/share/alsa/ucm2/Intel/bytcr-rt5640/HiFi-Components.conf
/usr/share/alsa/ucm2/Intel/skylake-rt286/skylake-rt286.conf
/usr/share/alsa/ucm2/Intel/skylake-rt286/Hdmi1.conf
/usr/share/alsa/ucm2/Intel/skylake-rt286/HiFi.conf
/usr/share/alsa/ucm2/Intel/skylake-rt286/Hdmi2.conf
/usr/share/alsa/ucm2/Intel/bytcht-es8316/bytcht-es8316.conf
/usr/share/alsa/ucm2/Intel/bytcht-es8316/HiFi-LongName.conf
/usr/share/alsa/ucm2/Intel/bytcht-es8316/HiFi.conf
/usr/share/alsa/ucm2/Intel/bytcht-es8316/HiFi-Components.conf
/usr/share/alsa/ucm2/Intel/chtrt5645/HiFi.conf
/usr/share/alsa/ucm2/Intel/chtrt5645/chtrt5645.conf
/usr/share/alsa/ucm2/PinePhone/PinePhone.conf
/usr/share/alsa/ucm2/PinePhone/VoiceCall.conf
/usr/share/alsa/ucm2/PinePhone/HiFi.conf
/usr/share/alsa/ucm2/Tegra/rt5631/Asus-Transformer-HiFi.conf
/usr/share/alsa/ucm2/Tegra/rt5631/Asus-Transformer.conf
/usr/share/alsa/ucm2/Tegra/tegra-hda/tegra-hda.conf
/usr/share/alsa/ucm2/Tegra/tegra-hda/tegra-hda-HiFi.conf
/usr/share/alsa/ucm2/Tegra/max98090/HiFi.conf
/usr/share/alsa/ucm2/Tegra/max98090/max98090.conf
/usr/share/alsa/ucm2/Tegra/wm8903/Asus-Transformer-HiFi.conf
/usr/share/alsa/ucm2/Tegra/wm8903/Asus-Transformer.conf
/usr/share/alsa/ucm2/Tegra/wm8903/Acer-A500-HiFi.conf
/usr/share/alsa/ucm2/Tegra/wm8903/Acer-A500.conf
/usr/share/alsa/ucm2/Tegra/rt5640/Google-Nexus-7.conf
/usr/share/alsa/ucm2/Tegra/rt5640/Google-Nexus-7-HiFi.conf
/usr/share/alsa/ucm2/Tegra/max98089/lge-x3-VoiceCall.conf
/usr/share/alsa/ucm2/Tegra/max98089/lge-x3-HiFi.conf
/usr/share/alsa/ucm2/Tegra/max98089/lge-x3.conf
/usr/share/alsa/ucm2/Tegra/alc5632/alc5632.conf
/usr/share/alsa/ucm2/Tegra/alc5632/HiFi.conf
/usr/share/alsa/ucm2/Tegra/alc5632/Record.conf
/usr/lib/sysctl.d/55-map-count.conf
/usr/lib/sysctl.d/50-default.conf
/usr/lib/sysctl.d/50-pid-max.conf
/usr/lib/sysctl.d/55-console-messages.conf
/usr/lib/sysctl.d/55-ptrace.conf
/usr/lib/sysctl.d/10-apparmor.conf
/usr/lib/sysctl.d/30-localsearch.conf
/usr/lib/sysctl.d/55-zeropage.conf
/usr/lib/sysctl.d/50-bubblewrap.conf
/usr/lib/sysctl.d/55-bufferbloat.conf
/usr/lib/sysctl.d/55-ipv6-privacy.conf
/usr/lib/sysctl.d/55-network-security.conf
/usr/lib/sysctl.d/10-coredump-debian.conf
/usr/lib/sysctl.d/55-magic-sysrq.conf
/usr/lib/sysctl.d/55-kernel-hardening.conf
/usr/lib/environment.d/990-snapd.conf
/usr/lib/environment.d/99-environment.conf
/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf
/usr/lib/NetworkManager/conf.d/10-default-firewall-use-iptables.conf
/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf
/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf
/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf
/usr/lib/tmpfiles.d/systemd-pstore.conf
/usr/lib/tmpfiles.d/passwd.conf
/usr/lib/tmpfiles.d/polkit-tmpfiles.conf
/usr/lib/tmpfiles.d/spice-vdagentd.conf
/usr/lib/tmpfiles.d/gvfsd-fuse-tmpfiles.conf
/usr/lib/tmpfiles.d/apport.conf
/usr/lib/tmpfiles.d/colord.conf
/usr/lib/tmpfiles.d/gnome-remote-desktop-tmpfiles.conf
/usr/lib/tmpfiles.d/screen-cleanup.conf
/usr/lib/tmpfiles.d/systemd-resolve.conf
/usr/lib/tmpfiles.d/tmp.conf
/usr/lib/tmpfiles.d/tpm-udev.conf
/usr/lib/tmpfiles.d/cron-daemon-common.conf
/usr/lib/tmpfiles.d/journal-nocow.conf
/usr/lib/tmpfiles.d/20-systemd-shell-extra.conf
/usr/lib/tmpfiles.d/20-systemd-ssh-generator.conf
/usr/lib/tmpfiles.d/00rsyslog.conf
/usr/lib/tmpfiles.d/speech-dispatcher.conf
/usr/lib/tmpfiles.d/man-db.conf
/usr/lib/tmpfiles.d/x11.conf
/usr/lib/tmpfiles.d/systemd-network.conf
/usr/lib/tmpfiles.d/home.conf
/usr/lib/tmpfiles.d/20-systemd-stub.conf
/usr/lib/tmpfiles.d/dbus.conf
/usr/lib/tmpfiles.d/systemd-nologin.conf
/usr/lib/tmpfiles.d/provision.conf
/usr/lib/tmpfiles.d/snapd.conf
/usr/lib/tmpfiles.d/var.conf
/usr/lib/tmpfiles.d/static-nodes-permissions.conf
/usr/lib/tmpfiles.d/legacy.conf
/usr/lib/tmpfiles.d/libselinux1.conf
/usr/lib/tmpfiles.d/openssh-client.conf
/usr/lib/tmpfiles.d/openvpn.conf
/usr/lib/tmpfiles.d/systemd.conf
/usr/lib/tmpfiles.d/credstore.conf
/usr/lib/tmpfiles.d/uuidd-tmpfiles.conf
/usr/lib/tmpfiles.d/debian.conf
/usr/lib/tmpfiles.d/systemd-tmp.conf
/usr/lib/tmpfiles.d/sudo.conf
/usr/lib/linux-sound-base/noOSS.modprobe.conf
/usr/lib/linux-sound-base/noALSA.modprobe.conf
/usr/lib/modprobe.d/fbdev-blacklist.conf
/usr/lib/modprobe.d/aliases.conf
/usr/lib/modprobe.d/blacklist_linux_6.17.0-14-generic.conf
/usr/lib/modprobe.d/systemd.conf
/usr/lib/aarch64-linux-gnu/sssd/conf/sssd.conf
/usr/lib/aarch64-linux-gnu/libpinyin/data/table.conf
/usr/lib/aarch64-linux-gnu/gconv/gconv-modules.d/gconv-modules-extra.conf
/usr/lib/systemd/journald.conf.d/syslog.conf
/usr/lib/systemd/system.conf.d/10-coredump-debian.conf
/usr/lib/systemd/system/rc-local.service.d/debian.conf
/usr/lib/systemd/system/user@.service.d/10-login-barrier.conf
/usr/lib/systemd/system/user@.service.d/10-oomd-user-service-defaults.conf
/usr/lib/systemd/system/user@.service.d/timeout.conf
/usr/lib/systemd/system/systemd-logind.service.d/dbus.conf
/usr/lib/systemd/system/systemd-fsck-root.service.d/10-skip-fsck-initramfs.conf
/usr/lib/systemd/system/systemd-udevd.service.d/syscall-architecture.conf
/usr/lib/systemd/system/systemd-journald.service.d/nice.conf
/usr/lib/systemd/system/user-.slice.d/10-defaults.conf
/usr/lib/systemd/system/systemd-coredump@.service.d/apport-coredump-hook.conf
/usr/lib/systemd/system/systemd-localed.service.d/x11-keyboard.conf
/usr/lib/systemd/system/user@0.service.d/10-login-barrier.conf
/usr/lib/systemd/system/-.slice.d/10-oomd-root-slice-defaults.conf
/usr/lib/systemd/user/gnome-session@ubuntu.target.d/gnome.session.conf
/usr/lib/systemd/user/gnome-session@gnome-initial-setup.target.d/gnome-initial-setup.conf
/usr/lib/systemd/user/app-flatpak-.scope.d/override.conf
/usr/lib/systemd/user/app-gnome-.scope.d/override.conf
/usr/lib/systemd/user/vte-spawn-.scope.d/defaults.conf
/usr/lib/systemd/user/snapd.session-agent.socket.d/70-gdm-skip.conf
/usr/lib/systemd/user/gnome-session@gnome-login.target.d/gnome-login.session.conf
/usr/lib/systemd/oomd.conf.d/10-oomd-defaults.conf
/usr/lib/systemd/user.conf.d/10-coredump-debian.conf
/usr/lib/systemd/resolv.conf
/usr/lib/systemd/logind.conf.d/unattended-upgrades-logind-maxdelay.conf
/usr/lib/systemd/ssh_config.d/20-systemd-ssh-proxy.conf
/usr/lib/systemd/resolved.conf.d/cache-no-negative.conf
/usr/lib/systemd/resolved.conf.d/00-disable-mdns.conf
/usr/lib/binfmt.d/python3.13.conf
/usr/lib/modules-load.d/fwupd-i2c.conf
/usr/lib/kernel/install.conf
/usr/lib/dhcpcd/dhcpcd-hooks/50-timesyncd.conf
/usr/lib/dhcpcd/dhcpcd-hooks/20-resolv.conf
/usr/lib/sysusers.d/polkit.conf
/usr/lib/sysusers.d/systemd-journal.conf
/usr/lib/sysusers.d/pipewire.conf
/usr/lib/sysusers.d/basic.conf
/usr/lib/sysusers.d/gamemode.conf
/usr/lib/sysusers.d/systemd-resolve.conf
/usr/lib/sysusers.d/cron-daemon-common.conf
/usr/lib/sysusers.d/gdm3.conf
/usr/lib/sysusers.d/fwupd.conf
/usr/lib/sysusers.d/systemd-oom.conf
/usr/lib/sysusers.d/systemd-network.conf
/usr/lib/sysusers.d/uuidd-sysusers.conf
/usr/lib/sysusers.d/debian-udev.conf
/usr/lib/sysusers.d/dbus.conf
/usr/lib/sysusers.d/gnome-initial-setup.conf
/usr/lib/sysusers.d/gnome-remote-desktop-sysusers.conf
/usr/lib/dracut/modules.d/11systemd-resolved/resolved-tmpfile-dracut.conf
/usr/lib/dracut/modules.d/11systemd-journald/initrd.conf
/usr/lib/dracut/modules.d/11systemd-timesyncd/timesyncd-tmpfile-dracut.conf
/usr/lib/dracut/modules.d/11systemd-hostnamed/org.freedesktop.hostname1_dracut.conf
/usr/lib/dracut/modules.d/11systemd-hostnamed/systemd-hostname-dracut.conf
/usr/lib/dracut/modules.d/11systemd-hostnamed/99-systemd-networkd-dracut.conf
/usr/lib/dracut/modules.d/77dracut-systemd/dracut-tmpfiles.conf
/usr/lib/dracut/modules.d/70multipath/multipathd-dracut.conf
/usr/lib/dracut/modules.d/77syslog/rsyslog.conf
/usr/lib/dracut/dracut.conf.d/fips/10-fips.conf
/usr/lib/dracut/dracut.conf.d/no-network/10-no-network.conf
/usr/lib/dracut/dracut.conf.d/uki-virt/10-uki-virt.conf
/usr/lib/dracut/dracut.conf.d/rescue/10-rescue.conf
/usr/lib/dracut/dracut.conf.d/no-xattr/10-no-xattr.conf
/usr/lib/dracut/dracut.conf.d/generic/11-generic.conf
/usr/lib/dracut/dracut.conf.d/ima/10-ima.conf
/usr/lib/dracut/dracut.conf.d/hostonly/10-hostonly.conf
/usr/lib/dracut/dracut.conf.d/10-debian.conf
/usr/src/linux-headers-6.17.0-14-generic/include/config/auto.conf
/run/NetworkManager/resolv.conf
/run/NetworkManager/no-stub-resolv.conf
/run/NetworkManager/conf.d/10-globally-managed-devices.conf
/run/tmpfiles.d/static-nodes.conf
/run/systemd/resolve/resolv.conf
/run/systemd/resolve/stub-resolv.conf
/etc/PackageKit/PackageKit.conf
/etc/PackageKit/Vendor.conf
/etc/udisks2/udisks2.conf
/etc/libao.conf
/etc/cups/snmp.conf
/etc/cups/cupsd.conf
/etc/cups/cups-files.conf
/etc/cups/subscriptions.conf
/etc/cups/cups-browsed.conf
/etc/gtk-3.0/im-multipress.conf
/etc/gtk-2.0/im-multipress.conf
/etc/ubuntu-advantage/uaclient.conf
/etc/usb_modeswitch.conf
/etc/environment.d/90qt-a11y.conf
/etc/environment.d/90atk-adaptor.conf
/etc/ssh/ssh_config.d/20-systemd-ssh-proxy.conf
/etc/xattr.conf
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
/etc/NetworkManager/NetworkManager.conf
/etc/dbus-1/system.d/com.ubuntu.WhoopsiePreferences.conf
/etc/dbus-1/system.d/com.redhat.NewPrinterNotification.conf
/etc/dbus-1/system.d/com.hp.hplip.conf
/etc/dbus-1/system.d/org.opensuse.CupsPkHelper.Mechanism.conf
/etc/dbus-1/system.d/com.ubuntu.LanguageSelector.conf
/etc/dbus-1/system.d/com.redhat.PrinterDriversInstaller.conf
/etc/dbus-1/system.d/org.debian.apt.conf
/etc/dbus-1/system.d/com.ubuntu.SoftwareProperties.conf
/etc/ca-certificates.conf
/etc/mke2fs.conf
/etc/UPower/UPower.conf
/etc/chrony/conf.d/ubuntu-nts.conf
/etc/chrony/chrony.conf
/etc/cracklib/cracklib.conf
/etc/libaudit.conf
/etc/debconf.conf
/etc/nftables.conf
/etc/vconsole.conf
/etc/rsyslog.d/50-default.conf
/etc/rsyslog.d/21-cloudinit.conf
/etc/rsyslog.d/20-ufw.conf
/etc/tmpfiles.d/screen-cleanup.conf
/etc/dhcpcd.conf
/etc/init/whoopsie.conf
/etc/sudo_logsrvd.conf
/etc/avahi/avahi-daemon.conf
/etc/ufw/ufw.conf
/etc/ufw/sysctl.conf
/etc/resolv.conf
/etc/ipp-usb/ipp-usb.conf
/etc/pnm2ppa.conf
/etc/adduser.conf
/etc/rygel.conf
/etc/snmp/snmp.conf
/etc/selinux/semanage.conf
/etc/sensors3.conf
/etc/ldap/ldap.conf
/etc/udev/udev.conf
/etc/udev/iocost.conf
/etc/speech-dispatcher/modules/espeak-ng.conf
/etc/speech-dispatcher/modules/cicero.conf
/etc/speech-dispatcher/modules/llia_phon-generic.conf
/etc/speech-dispatcher/modules/dtk-generic.conf
/etc/speech-dispatcher/modules/espeak.conf
/etc/speech-dispatcher/modules/festival.conf
/etc/speech-dispatcher/modules/flite.conf
/etc/speech-dispatcher/modules/espeak-ng-mbrola-generic.conf
/etc/speech-dispatcher/modules/mary-generic.conf
/etc/speech-dispatcher/modules/openjtalk.conf
/etc/speech-dispatcher/modules/espeak-ng-mbrola.conf
/etc/speech-dispatcher/modules/epos-generic.conf
/etc/speech-dispatcher/modules/mimic3-generic.conf
/etc/speech-dispatcher/modules/espeak-mbrola-generic.conf
/etc/speech-dispatcher/modules/swift-generic.conf
/etc/speech-dispatcher/speechd.conf
/etc/speech-dispatcher/clients/emacs.conf
/etc/ld.so.conf
/etc/plymouth/plymouthd.conf
/etc/initramfs-tools/initramfs.conf
/etc/ghostscript/fontmap.d/10fonts-urw-base35.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan2.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-korea1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-cns1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-gb1.conf
/etc/ld.so.conf.d/libc.conf
/etc/ld.so.conf.d/aarch64-linux-gnu.conf
/etc/xdg/user-dirs.conf
/etc/host.conf
/etc/locale.conf
/etc/pulse/client.conf
/etc/rsyslog.conf
/etc/apt/apt.conf.d/20apt-esm-hook.conf
/etc/apt/apt.conf.d/20snapd.conf
/etc/logrotate.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/fprintd.conf
/etc/bluetooth/input.conf
/etc/bluetooth/network.conf
/etc/bluetooth/main.conf
/etc/systemd/logind.conf
/etc/systemd/system.conf
/etc/systemd/resolved.conf
/etc/systemd/journald.conf
/etc/systemd/oomd.conf
/etc/systemd/sleep.conf
/etc/systemd/networkd.conf
/etc/systemd/user.conf
/etc/systemd/pstore.conf
/etc/deluser.conf
/etc/ucf.conf
/etc/e2scrub.conf
/etc/apparmor/parser.conf
/etc/gdm3/custom.conf
/etc/kdump/sysctl.conf
/etc/apport/crashdb.conf
/etc/modules-load.d/modules.conf
/etc/pam.conf
/etc/fonts/fonts.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-serif.conf
/etc/fonts/conf.avail/30-droid-noto.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-serif.conf
/etc/fonts/conf.avail/65-droid-sans-fallback.conf
/etc/fonts/conf.avail/57-dejavu-serif.conf
/etc/fonts/conf.avail/58-dejavu-lgc-serif.conf
/etc/fonts/conf.avail/57-dejavu-sans-mono.conf
/etc/fonts/conf.avail/57-dejavu-sans.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/30-droid-noto-mono.conf
/etc/fonts/conf.d/10-scale-bitmap-fonts.conf
/etc/fonts/conf.d/61-urw-standard-symbols-ps.conf
/etc/fonts/conf.d/69-language-selector-zh-tw.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-serif.conf
/etc/fonts/conf.d/49-sansserif.conf
/etc/fonts/conf.d/60-generic.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-sans.conf
/etc/fonts/conf.d/58-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.d/61-urw-nimbus-roman.conf
/etc/fonts/conf.d/10-hinting-slight.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.d/61-urw-gothic.conf
/etc/fonts/conf.d/48-spacing.conf
/etc/fonts/conf.d/61-urw-fallback-backwards.conf
/etc/fonts/conf.d/40-nonlatin.conf
/etc/fonts/conf.d/10-sub-pixel-rgb.conf
/etc/fonts/conf.d/61-urw-d050000l.conf
/etc/fonts/conf.d/69-language-selector-zh-cn.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-sans-mono.conf
/etc/fonts/conf.d/60-latin.conf
/etc/fonts/conf.d/69-unifont.conf
/etc/fonts/conf.d/45-generic.conf
/etc/fonts/conf.d/65-fonts-persian.conf
/etc/fonts/conf.d/90-synthetic.conf
/etc/fonts/conf.d/64-language-selector-cjk-prefer.conf
/etc/fonts/conf.d/61-urw-p052.conf
/etc/fonts/conf.d/99-language-selector-zh.conf
/etc/fonts/conf.d/61-urw-bookman.conf
/etc/fonts/conf.d/80-delicious.conf
/etc/fonts/conf.d/70-no-bitmaps-except-emoji.conf
/etc/fonts/conf.d/61-urw-nimbus-sans.conf
/etc/fonts/conf.d/70-fonts-noto-cjk.conf
/etc/fonts/conf.d/51-local.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-serif.conf
/etc/fonts/conf.d/45-latin.conf
/etc/fonts/conf.d/65-droid-sans-fallback.conf
/etc/fonts/conf.d/61-urw-nimbus-mono-ps.conf
/etc/fonts/conf.d/57-dejavu-serif.conf
/etc/fonts/conf.d/58-dejavu-lgc-serif.conf
/etc/fonts/conf.d/71-ubuntulegacy.conf
/etc/fonts/conf.d/65-nonlatin.conf
/etc/fonts/conf.d/69-language-selector-zh-sg.conf
/etc/fonts/conf.d/30-metric-aliases.conf
/etc/fonts/conf.d/57-dejavu-sans-mono.conf
/etc/fonts/conf.d/69-language-selector-zh-mo.conf
/etc/fonts/conf.d/30-cjk-aliases.conf
/etc/fonts/conf.d/10-yes-antialias.conf
/etc/fonts/conf.d/57-dejavu-sans.conf
/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans.conf
/etc/fonts/conf.d/20-unhint-small-vera.conf
/etc/fonts/conf.d/11-lcdfilter-default.conf
/etc/fonts/conf.d/69-language-selector-zh-hk.conf
/etc/fonts/conf.d/61-urw-z003.conf
/etc/fonts/conf.d/61-urw-fallback-generics.conf
/etc/fonts/conf.d/69-language-selector-ja.conf
/etc/fonts/conf.d/56-language-selector-prefer.conf
/etc/fonts/conf.d/58-dejavu-lgc-sans.conf
/etc/fonts/conf.d/61-urw-c059.conf
/etc/fonts/conf.d/50-user.conf
/etc/fonts/snap-override/10-prefer-noto.conf
/etc/brltty.conf
/etc/geoclue/geoclue.conf
/etc/nsswitch.conf
/etc/gai.conf
/etc/hp/hplip.conf
/etc/depmod.d/ubuntu.conf
/etc/dracut.conf
/etc/fwupd/fwupd.conf
/etc/fwupd/remotes.d/lvfs-testing.conf
/etc/fwupd/remotes.d/vendor-directory.conf
/etc/fwupd/remotes.d/lvfs.conf
/etc/fuse.conf
/etc/security/access.conf
/etc/security/capability.conf
/etc/security/namespace.conf
/etc/security/pwquality.conf
/etc/security/time.conf
/etc/security/sepermit.conf
/etc/security/limits.conf
/etc/security/faillock.conf
/etc/security/pam_env.conf
/etc/security/pwhistory.conf
/etc/security/group.conf
/etc/security/limits.d/10-gamemode.conf
/etc/security/limits.d/25-pw-rlimits.conf
/etc/security/limits.d/10-coredump-debian.conf
/etc/hdparm.conf
/etc/sane.d/leo.conf
/etc/sane.d/coolscan.conf
/etc/sane.d/epjitsu.conf
/etc/sane.d/u12.conf
/etc/sane.d/s9036.conf
/etc/sane.d/qcam.conf
/etc/sane.d/dll.conf
/etc/sane.d/umax.conf
/etc/sane.d/test.conf
/etc/sane.d/pie.conf
/etc/sane.d/umax_pp.conf
/etc/sane.d/net.conf
/etc/sane.d/cardscan.conf
/etc/sane.d/gphoto2.conf
/etc/sane.d/hp5400.conf
/etc/sane.d/matsushita.conf
/etc/sane.d/mustek_usb.conf
/etc/sane.d/artec_eplus48u.conf
/etc/sane.d/dc240.conf
/etc/sane.d/stv680.conf
/etc/sane.d/ma1509.conf
/etc/sane.d/artec.conf
/etc/sane.d/canon.conf
/etc/sane.d/sm3840.conf
/etc/sane.d/saned.conf
/etc/sane.d/snapscan.conf
/etc/sane.d/sharp.conf
/etc/sane.d/abaton.conf
/etc/sane.d/kodakaio.conf
/etc/sane.d/teco3.conf
/etc/sane.d/p5.conf
/etc/sane.d/st400.conf
/etc/sane.d/canon_dr.conf
/etc/sane.d/gt68xx.conf
/etc/sane.d/v4l.conf
/etc/sane.d/teco1.conf
/etc/sane.d/dell1600n_net.conf
/etc/sane.d/dmc.conf
/etc/sane.d/mustek_pp.conf
/etc/sane.d/nec.conf
/etc/sane.d/coolscan3.conf
/etc/sane.d/avision.conf
/etc/sane.d/canon_lide70.conf
/etc/sane.d/microtek2.conf
/etc/sane.d/kvs1025.conf
/etc/sane.d/magicolor.conf
/etc/sane.d/airscan.conf
/etc/sane.d/canon630u.conf
/etc/sane.d/canon_pp.conf
/etc/sane.d/microtek.conf
/etc/sane.d/genesys.conf
/etc/sane.d/hp3900.conf
/etc/sane.d/xerox_mfp.conf
/etc/sane.d/tamarack.conf
/etc/sane.d/fujitsu.conf
/etc/sane.d/lexmark_x2600.conf
/etc/sane.d/agfafocus.conf
/etc/sane.d/rts8891.conf
/etc/sane.d/pixma.conf
/etc/sane.d/sceptre.conf
/etc/sane.d/sp15c.conf
/etc/sane.d/hp.conf
/etc/sane.d/apple.conf
/etc/sane.d/epson.conf
/etc/sane.d/plustek.conf
/etc/sane.d/lexmark.conf
/etc/sane.d/teco2.conf
/etc/sane.d/pieusb.conf
/etc/sane.d/hp4200.conf
/etc/sane.d/escl.conf
/etc/sane.d/mustek.conf
/etc/sane.d/epson2.conf
/etc/sane.d/bh.conf
/etc/sane.d/coolscan2.conf
/etc/sane.d/kodak.conf
/etc/sane.d/hpsj5s.conf
/etc/sane.d/plustek_pp.conf
/etc/sane.d/ibm.conf
/etc/sane.d/umax1220u.conf
/etc/sane.d/dc210.conf
/etc/sane.d/hs2p.conf
/etc/sane.d/dc25.conf
/etc/sane.d/ricoh.conf
/etc/sane.d/epsonds.conf
/etc/alsa/conf.d/50-pipewire.conf
/etc/alsa/conf.d/99-pipewire-default.conf
/etc/sudo.conf
/snap/gnome-42-2204/245/etc/debconf.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-antialias.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-autohint.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-hinting-full.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-hinting-medium.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-hinting-none.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-hinting-slight.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-no-sub-pixel.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-scale-bitmap-fonts.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-sub-pixel-bgr.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-sub-pixel-rgb.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-sub-pixel-vbgr.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-sub-pixel-vrgb.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/10-unhinted.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/11-lcdfilter-default.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/11-lcdfilter-legacy.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/11-lcdfilter-light.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-dejavu-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/20-unhint-small-vera.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/25-arphic-ukai-render.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/25-arphic-uming-bitmaps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/25-arphic-uming-render.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/25-ttf-arphic-ukai-render.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/25-unhint-nonlatin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/30-cjk-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/30-droid-noto-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/30-metric-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/35-arphic-ukai-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/35-arphic-uming-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/35-ttf-arphic-ukai-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/40-nonlatin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/41-arphic-ukai.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/41-arphic-uming.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/41-ttf-arphic-ukai.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/45-generic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/45-latin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/49-sansserif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/50-user.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/51-local.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/53-monospace-lcd-filter.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/56-language-selector-ar.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/57-dejavu-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/57-dejavu-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/57-dejavu-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/58-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/58-dejavu-lgc-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/58-dejavu-lgc-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/59-lohit-devanagari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/60-generic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/60-latin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/64-arphic-uming.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/64-language-selector-prefer.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-beng-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-deva-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-gubbi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-gujr-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-guru-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-orya-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-pagul.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-fonts-telu-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-smc-meera.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-0-smc-rachana.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-droid-sans-fallback.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-fonts-arphic-ukai.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-fonts-arphic-uming.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-fonts-persian.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-khmer.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/65-nonlatin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-assamese.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-bengali.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-devanagari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-gujarati.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-gurmukhi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-kannada.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-odia.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-tamil-classical.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-tamil.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/66-lohit-telugu.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-fonts-smc-manjari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-lohit-malayalam.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-anjalioldlipi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-chilanka.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-dyuthi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-karumbi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-keraleeyam.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-raghumalayalamsans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-suruma.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/67-smc-uroob.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-ja.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-zh-cn.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-zh-hk.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-zh-mo.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-zh-sg.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-language-selector-zh-tw.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/69-unifont.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/70-force-bitmaps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/70-no-bitmaps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/70-yes-bitmaps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/75-arphic-ukai-select.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/75-ttf-arphic-ukai-select.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/80-delicious.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/90-arphic-ukai-embolden.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/90-arphic-uming-embolden.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/90-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/90-ttf-arphic-ukai-embolden.conf
/snap/gnome-42-2204/245/etc/fonts/conf.avail/99-language-selector-zh.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/10-antialias.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/10-hinting-slight.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/10-scale-bitmap-fonts.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/11-lcdfilter-default.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-dejavu-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/20-unhint-small-vera.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/25-arphic-ukai-render.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/25-arphic-uming-render.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/30-cjk-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/30-metric-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/35-arphic-ukai-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/35-arphic-uming-aliases.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/40-nonlatin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/41-arphic-ukai.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/41-arphic-uming.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/45-generic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/45-latin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/49-sansserif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/50-user.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/51-local.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/56-language-selector-ar.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/57-dejavu-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/57-dejavu-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/57-dejavu-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/58-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/58-dejavu-lgc-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/58-dejavu-lgc-serif.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/59-lohit-devanagari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/60-generic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/60-latin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-bookman.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-c059.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-d050000l.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-fallback-backwards.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-fallback-generics.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-gothic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-nimbus-mono-ps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-nimbus-roman.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-nimbus-sans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-p052.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-standard-symbols-ps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/61-urw-z003.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-01-tlwg-kinnari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-02-tlwg-norasi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-10-tlwg-loma.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-11-tlwg-waree.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-13-tlwg-garuda.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-14-tlwg-umpush.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-15-laksaman.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-21-tlwg-typo.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-22-tlwg-typist.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-23-tlwg-mono.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/64-language-selector-prefer.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-beng-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-deva-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-gubbi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-gujr-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-guru-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-orya-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-pagul.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-fonts-telu-extra.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-smc-meera.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-0-smc-rachana.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-droid-sans-fallback.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-fonts-arphic-ukai.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-fonts-arphic-uming.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-fonts-persian.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/65-nonlatin.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-assamese.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-bengali.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-devanagari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-gujarati.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-gurmukhi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-kannada.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-odia.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-tamil-classical.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-tamil.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/66-lohit-telugu.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-fonts-smc-manjari.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-anjalioldlipi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-chilanka.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-dyuthi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-karumbi.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-keraleeyam.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-raghumalayalamsans.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-suruma.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/67-smc-uroob.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-ja.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-zh-cn.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-zh-hk.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-zh-mo.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-zh-sg.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-language-selector-zh-tw.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/69-unifont.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/70-fonts-noto-cjk.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/70-no-bitmaps.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/75-arphic-ukai-select.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/80-delicious.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/89-tlwg-laksaman-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/90-arphic-ukai-embolden.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/90-arphic-uming-embolden.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/90-synthetic.conf
/snap/gnome-42-2204/245/etc/fonts/conf.d/99-language-selector-zh.conf
/snap/gnome-42-2204/245/etc/fonts/fonts.conf
/snap/gnome-42-2204/245/etc/gai.conf
/snap/gnome-42-2204/245/etc/gtk-3.0/im-multipress.conf
/snap/gnome-42-2204/245/etc/ld.so.conf
/snap/gnome-42-2204/245/etc/ld.so.conf.d/libc.conf
/snap/gnome-42-2204/245/etc/pulse/client.conf
/snap/gnome-42-2204/245/etc/sensors3.conf
/snap/gnome-42-2204/245/etc/xdg/user-dirs.conf
/snap/gnome-42-2204/245/usr/lib/binfmt.d/python3.10.conf
/snap/gnome-42-2204/245/usr/lib/sysctl.d/50-bubblewrap.conf
/snap/gnome-42-2204/245/usr/lib/systemd/user/vte-spawn-.scope.d/defaults.conf
/snap/gnome-42-2204/245/usr/share/alsa/alsa.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/AACI.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ATIIXP-MODEM.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ATIIXP.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/AU8810.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/AU8820.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/AU8830.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Audigy.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Audigy2.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Aureon51.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Aureon71.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CA0106.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CMI8338-SWIEC.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CMI8338.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CMI8738-MC6.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CMI8738-MC8.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CMI8788.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/CS46xx.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/EMU10K1.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/EMU10K1X.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ENS1370.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ENS1371.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ES1968.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Echo_Echo3G.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/FM801.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/FWSpeakers.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/FireWave.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/GUS.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/HDA-Intel.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/HdmiLpeAudio.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ICE1712.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ICE1724.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ICH-MODEM.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ICH.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/ICH4.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Loopback.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/Maestro3.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/NFORCE.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/PC-Speaker.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/PMac.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/PMacToonie.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/PS3.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/RME9636.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/RME9652.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/SB-XFi.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/SI7018.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/TRID4DWAVENX.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/USB-Audio.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VIA686A.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VIA8233.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VIA8233A.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VIA8237.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VX222.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VXPocket.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/VXPocket440.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/YMF744.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/aliases.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/pistachio-card.conf
/snap/gnome-42-2204/245/usr/share/alsa/cards/vc4-hdmi.conf
/snap/gnome-42-2204/245/usr/share/alsa/ctl/default.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/center_lfe.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/default.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/dmix.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/dpl.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/dsnoop.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/front.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/hdmi.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/iec958.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/modem.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/rear.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/side.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround21.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround40.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround41.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround50.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround51.conf
/snap/gnome-42-2204/245/usr/share/alsa/pcm/surround71.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-aux.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-dock-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-fm.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-front-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-headphone-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-headset-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic-always.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-linein.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-mic-line.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-rear-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-tvtuner.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input-video.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-input.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-chat.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones-2.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-lineout.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-mono.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker-always.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/analog-output.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-0.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-1.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-10.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-2.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-3.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-4.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-5.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-6.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-7.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-8.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/hdmi-output-9.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-input.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-output.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-chat-common.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-game-common.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-input.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-mono.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-stereo.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/paths/virtual-surround-7.1.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/audigy.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/cmedia-high-speed-true-hdaudio.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/default.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/dell-dock-tb16-usb-audio.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker-and-int-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-120w-g2.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-audio-module.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/kinect-audio.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/maudio-fasttrack-pro.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio4dj.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio8dj.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-komplete-audio6.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-korecontroller.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio10.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio2.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio6.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktorkontrol-s4.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/sb-omni-surround-5.1.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/sennheiser-gsx.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/simple-headphones-mic.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/steelseries-arctis-common-usb-audio.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/texas-instruments-pcm2902.conf
/snap/gnome-42-2204/245/usr/share/alsa-card-profile/mixer/profile-sets/usb-gaming-headset.conf
/snap/gnome-42-2204/245/usr/share/debconf/debconf.conf
/snap/gnome-42-2204/245/usr/share/defaults/at-spi2/accessibility.conf
/snap/gnome-42-2204/245/usr/share/drirc.d/00-mesa-defaults.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-autoeng.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-chttrans.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-clipboard.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-dbus.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-freedesktop-notify.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-fullwidth-char.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-imselector.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-ipc.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-ipcportal.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-keyboard.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-punc.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-quickphrase.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-remote-module.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-spell.conf
/snap/gnome-42-2204/245/usr/share/fcitx/addon/fcitx-unicode.conf
/snap/gnome-42-2204/245/usr/share/fcitx/dbus/daemon.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-01-tlwg-kinnari.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-02-tlwg-norasi.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-10-tlwg-loma.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-11-tlwg-waree.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-13-tlwg-garuda.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-14-tlwg-umpush.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-15-laksaman.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-21-tlwg-typo.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-22-tlwg-typist.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/64-23-tlwg-mono.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/70-fonts-noto-cjk.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/89-tlwg-garuda-synthetic.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/89-tlwg-kinnari-synthetic.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/89-tlwg-laksaman-synthetic.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/89-tlwg-umpush-synthetic.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-bookman.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-c059.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-d050000l.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-fallback-backwards.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-fallback-generics.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-fallback-specifics.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-gothic.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-nimbus-mono-ps.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-nimbus-roman.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-nimbus-sans.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-p052.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-standard-symbols-ps.conf
/snap/gnome-42-2204/245/usr/share/fontconfig/conf.avail/urw-z003.conf
/snap/gnome-42-2204/245/usr/share/libc-bin/nsswitch.conf
/snap/gnome-42-2204/245/usr/share/pipewire/client-rt.conf
/snap/gnome-42-2204/245/usr/share/pipewire/client.conf
/snap/gnome-42-2204/245/usr/share/pipewire/jack.conf
/snap/gnome-42-2204/245/usr/share/pipewire/minimal.conf
/snap/gnome-42-2204/245/usr/share/pipewire/pipewire.conf
/snap/gnome-42-2204/245/usr/share/upstart/sessions/session-migration.conf
/snap/gnome-42-2204/245/usr/share/upstart/sessions/unity-gtk-module.conf
/snap/gnome-42-2204/228/etc/debconf.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-antialias.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-autohint.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-hinting-full.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-hinting-medium.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-hinting-none.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-hinting-slight.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-no-sub-pixel.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-scale-bitmap-fonts.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-sub-pixel-bgr.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-sub-pixel-rgb.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-sub-pixel-vbgr.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-sub-pixel-vrgb.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/10-unhinted.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/11-lcdfilter-default.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/11-lcdfilter-legacy.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/11-lcdfilter-light.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-dejavu-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/20-unhint-small-vera.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/25-arphic-ukai-render.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/25-arphic-uming-bitmaps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/25-arphic-uming-render.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/25-ttf-arphic-ukai-render.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/25-unhint-nonlatin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/30-cjk-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/30-droid-noto-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/30-metric-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/35-arphic-ukai-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/35-arphic-uming-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/35-ttf-arphic-ukai-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/40-nonlatin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/41-arphic-ukai.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/41-arphic-uming.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/41-ttf-arphic-ukai.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/45-generic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/45-latin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/49-sansserif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/50-user.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/51-local.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/53-monospace-lcd-filter.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/56-language-selector-ar.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/57-dejavu-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/57-dejavu-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/57-dejavu-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/58-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/58-dejavu-lgc-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/58-dejavu-lgc-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/59-lohit-devanagari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/60-generic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/60-latin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/64-arphic-uming.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/64-language-selector-prefer.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-beng-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-deva-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-gubbi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-gujr-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-guru-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-orya-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-pagul.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-fonts-telu-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-smc-meera.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-0-smc-rachana.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-droid-sans-fallback.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-fonts-arphic-ukai.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-fonts-arphic-uming.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-fonts-persian.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-khmer.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/65-nonlatin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-assamese.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-bengali.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-devanagari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-gujarati.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-gurmukhi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-kannada.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-odia.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-tamil-classical.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-tamil.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/66-lohit-telugu.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-fonts-smc-manjari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-lohit-malayalam.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-anjalioldlipi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-chilanka.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-dyuthi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-karumbi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-keraleeyam.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-raghumalayalamsans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-suruma.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/67-smc-uroob.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-ja.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-zh-cn.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-zh-hk.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-zh-mo.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-zh-sg.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-language-selector-zh-tw.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/69-unifont.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/70-force-bitmaps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/70-no-bitmaps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/70-yes-bitmaps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/75-arphic-ukai-select.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/75-ttf-arphic-ukai-select.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/80-delicious.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/90-arphic-ukai-embolden.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/90-arphic-uming-embolden.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/90-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/90-ttf-arphic-ukai-embolden.conf
/snap/gnome-42-2204/228/etc/fonts/conf.avail/99-language-selector-zh.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/10-antialias.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/10-hinting-slight.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/10-scale-bitmap-fonts.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/11-lcdfilter-default.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-lgc-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-dejavu-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/20-unhint-small-vera.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/25-arphic-ukai-render.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/25-arphic-uming-render.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/30-cjk-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/30-metric-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/35-arphic-ukai-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/35-arphic-uming-aliases.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/40-nonlatin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/41-arphic-ukai.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/41-arphic-uming.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/45-generic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/45-latin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/49-sansserif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/50-user.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/51-local.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/56-language-selector-ar.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/57-dejavu-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/57-dejavu-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/57-dejavu-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/58-dejavu-lgc-sans-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/58-dejavu-lgc-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/58-dejavu-lgc-serif.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/59-lohit-devanagari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/60-generic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/60-latin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-bookman.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-c059.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-d050000l.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-fallback-backwards.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-fallback-generics.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-gothic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-nimbus-mono-ps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-nimbus-roman.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-nimbus-sans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-p052.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-standard-symbols-ps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/61-urw-z003.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-01-tlwg-kinnari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-02-tlwg-norasi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-10-tlwg-loma.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-11-tlwg-waree.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-13-tlwg-garuda.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-14-tlwg-umpush.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-15-laksaman.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-21-tlwg-typo.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-22-tlwg-typist.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-23-tlwg-mono.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/64-language-selector-prefer.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-beng-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-deva-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-gubbi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-gujr-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-guru-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-orya-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-pagul.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-fonts-telu-extra.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-smc-meera.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-0-smc-rachana.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-droid-sans-fallback.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-fonts-arphic-ukai.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-fonts-arphic-uming.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-fonts-persian.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/65-nonlatin.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-assamese.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-bengali.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-devanagari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-gujarati.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-gurmukhi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-kannada.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-odia.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-tamil-classical.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-tamil.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/66-lohit-telugu.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-fonts-smc-manjari.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-anjalioldlipi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-chilanka.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-dyuthi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-karumbi.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-keraleeyam.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-raghumalayalamsans.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-suruma.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/67-smc-uroob.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-ja.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-zh-cn.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-zh-hk.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-zh-mo.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-zh-sg.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-language-selector-zh-tw.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/69-unifont.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/70-fonts-noto-cjk.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/70-no-bitmaps.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/75-arphic-ukai-select.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/80-delicious.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/89-tlwg-garuda-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/89-tlwg-kinnari-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/89-tlwg-laksaman-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/89-tlwg-umpush-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/90-arphic-ukai-embolden.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/90-arphic-uming-embolden.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/90-synthetic.conf
/snap/gnome-42-2204/228/etc/fonts/conf.d/99-language-selector-zh.conf
/snap/gnome-42-2204/228/etc/fonts/fonts.conf
/snap/gnome-42-2204/228/etc/gai.conf
/snap/gnome-42-2204/228/etc/gtk-3.0/im-multipress.conf
/snap/gnome-42-2204/228/etc/ld.so.conf
/snap/gnome-42-2204/228/etc/ld.so.conf.d/libc.conf
/snap/gnome-42-2204/228/etc/pulse/client.conf
/snap/gnome-42-2204/228/etc/sensors3.conf
/snap/gnome-42-2204/228/etc/xdg/user-dirs.conf
/snap/gnome-42-2204/228/usr/lib/binfmt.d/python3.10.conf
/snap/gnome-42-2204/228/usr/lib/sysctl.d/50-bubblewrap.conf
/snap/gnome-42-2204/228/usr/lib/systemd/user/vte-spawn-.scope.d/defaults.conf
/snap/gnome-42-2204/228/usr/share/alsa/alsa.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/AACI.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ATIIXP-MODEM.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ATIIXP.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/AU8810.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/AU8820.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/AU8830.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Audigy.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Audigy2.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Aureon51.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Aureon71.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CA0106.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CMI8338-SWIEC.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CMI8338.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CMI8738-MC6.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CMI8738-MC8.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CMI8788.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/CS46xx.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/EMU10K1.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/EMU10K1X.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ENS1370.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ENS1371.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ES1968.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Echo_Echo3G.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/FM801.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/FWSpeakers.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/FireWave.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/GUS.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/HDA-Intel.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/HdmiLpeAudio.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ICE1712.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ICE1724.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ICH-MODEM.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ICH.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/ICH4.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Loopback.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/Maestro3.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/NFORCE.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/PC-Speaker.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/PMac.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/PMacToonie.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/PS3.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/RME9636.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/RME9652.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/SB-XFi.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/SI7018.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/TRID4DWAVENX.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/USB-Audio.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VIA686A.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VIA8233.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VIA8233A.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VIA8237.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VX222.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VXPocket.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/VXPocket440.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/YMF744.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/aliases.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/pistachio-card.conf
/snap/gnome-42-2204/228/usr/share/alsa/cards/vc4-hdmi.conf
/snap/gnome-42-2204/228/usr/share/alsa/ctl/default.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/center_lfe.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/default.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/dmix.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/dpl.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/dsnoop.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/front.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/hdmi.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/iec958.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/modem.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/rear.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/side.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround21.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround40.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround41.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround50.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround51.conf
/snap/gnome-42-2204/228/usr/share/alsa/pcm/surround71.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-aux.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-dock-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-fm.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-front-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-headphone-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-headset-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic-always.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-linein.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-mic-line.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-rear-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-tvtuner.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input-video.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-input.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-chat.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones-2.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-headphones.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-lineout.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-mono.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker-always.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output-speaker.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/analog-output.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-0.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-1.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-10.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-2.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-3.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-4.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-5.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-6.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-7.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-8.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/hdmi-output-9.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-input.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/iec958-stereo-output.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-chat-common.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/steelseries-arctis-output-game-common.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-input.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-mono.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/usb-gaming-headset-output-stereo.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/paths/virtual-surround-7.1.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/audigy.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/cmedia-high-speed-true-hdaudio.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/default.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/dell-dock-tb16-usb-audio.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker-and-int-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/force-speaker.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-120w-g2.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/hp-tbt-dock-audio-module.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/kinect-audio.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/maudio-fasttrack-pro.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio4dj.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-audio8dj.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-komplete-audio6.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-korecontroller.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio10.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio2.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktor-audio6.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/native-instruments-traktorkontrol-s4.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/sb-omni-surround-5.1.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/sennheiser-gsx.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/simple-headphones-mic.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/steelseries-arctis-common-usb-audio.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/texas-instruments-pcm2902.conf
/snap/gnome-42-2204/228/usr/share/alsa-card-profile/mixer/profile-sets/usb-gaming-headset.conf
/snap/gnome-42-2204/228/usr/share/debconf/debconf.conf
/snap/gnome-42-2204/228/usr/share/defaults/at-spi2/accessibility.conf
/snap/gnome-42-2204/228/usr/share/drirc.d/00-mesa-defaults.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-autoeng.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-chttrans.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-clipboard.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-dbus.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-freedesktop-notify.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-fullwidth-char.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-imselector.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-ipc.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-ipcportal.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-keyboard.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-punc.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-quickphrase.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-remote-module.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-spell.conf
/snap/gnome-42-2204/228/usr/share/fcitx/addon/fcitx-unicode.conf
/snap/gnome-42-2204/228/usr/share/fcitx/dbus/daemon.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-01-tlwg-kinnari.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-02-tlwg-norasi.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-10-tlwg-loma.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-11-tlwg-waree.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-13-tlwg-garuda.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-14-tlwg-umpush.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-15-laksaman.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-21-tlwg-typo.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-22-tlwg-typist.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/64-23-tlwg-mono.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/70-fonts-noto-cjk.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/89-tlwg-garuda-synthetic.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/89-tlwg-kinnari-synthetic.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/89-tlwg-laksaman-synthetic.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/89-tlwg-umpush-synthetic.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-bookman.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-c059.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-d050000l.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-fallback-backwards.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-fallback-generics.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-fallback-specifics.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-gothic.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-nimbus-mono-ps.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-nimbus-roman.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-nimbus-sans.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-p052.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-standard-symbols-ps.conf
/snap/gnome-42-2204/228/usr/share/fontconfig/conf.avail/urw-z003.conf
/snap/gnome-42-2204/228/usr/share/libc-bin/nsswitch.conf
/snap/gnome-42-2204/228/usr/share/pipewire/client-rt.conf
/snap/gnome-42-2204/228/usr/share/pipewire/client.conf
/snap/gnome-42-2204/228/usr/share/pipewire/jack.conf
/snap/gnome-42-2204/228/usr/share/pipewire/minimal.conf
/snap/gnome-42-2204/228/usr/share/pipewire/pipewire.conf
/snap/gnome-42-2204/228/usr/share/upstart/sessions/session-migration.conf
/snap/gnome-42-2204/228/usr/share/upstart/sessions/unity-gtk-module.conf
/snap/snapd/25205/usr/lib/aarch64-linux-gnu/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/snapd/25205/usr/lib/environment.d/990-snapd.conf
/snap/snapd/25205/usr/lib/snapd/apparmor/parser.conf
/snap/snapd/25205/usr/lib/tmpfiles.d/snapd.conf
/snap/snapd/25205/usr/share/dbus-1/session.d/snapd.session-services.conf
/snap/snapd/25205/usr/share/dbus-1/system.d/snapd.system-services.conf
/snap/snapd/25939/usr/lib/aarch64-linux-gnu/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/snapd/25939/usr/lib/environment.d/990-snapd.conf
/snap/snapd/25939/usr/lib/snapd/apparmor/parser.conf
/snap/snapd/25939/usr/lib/tmpfiles.d/snapd.conf
/snap/snapd/25939/usr/share/dbus-1/session.d/snapd.session-services.conf
/snap/snapd/25939/usr/share/dbus-1/system.d/snapd.system-services.conf
/snap/core22/2293/etc/adduser.conf
/snap/core22/2293/etc/apparmor/parser.conf
/snap/core22/2293/etc/ca-certificates.conf
/snap/core22/2293/etc/dbus-1/system.d/wpa_supplicant.conf
/snap/core22/2293/etc/deluser.conf
/snap/core22/2293/etc/depmod.d/ubuntu.conf
/snap/core22/2293/etc/dhcp/dhclient.conf
/snap/core22/2293/etc/e2scrub.conf
/snap/core22/2293/etc/host.conf
/snap/core22/2293/etc/ld.so.conf
/snap/core22/2293/etc/ld.so.conf.d/aarch64-linux-gnu.conf
/snap/core22/2293/etc/ld.so.conf.d/arm-linux-gnueabihf.conf
/snap/core22/2293/etc/ld.so.conf.d/libc.conf
/snap/core22/2293/etc/libaudit.conf
/snap/core22/2293/etc/modprobe.d/blacklist-ath_pci.conf
/snap/core22/2293/etc/modprobe.d/blacklist-firewire.conf
/snap/core22/2293/etc/modprobe.d/blacklist-framebuffer.conf
/snap/core22/2293/etc/modprobe.d/blacklist-rare-network.conf
/snap/core22/2293/etc/modprobe.d/blacklist.conf
/snap/core22/2293/etc/modprobe.d/iwlwifi.conf
/snap/core22/2293/etc/modules-load.d/modules.conf
/snap/core22/2293/etc/nsswitch.conf
/snap/core22/2293/etc/plymouth/plymouthd.conf
/snap/core22/2293/etc/polkit-1/localauthority.conf.d/50-localauthority.conf
/snap/core22/2293/etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf
/snap/core22/2293/etc/resolv.conf
/snap/core22/2293/etc/rsyslog.d/21-cloudinit.conf
/snap/core22/2293/etc/security/access.conf
/snap/core22/2293/etc/security/faillock.conf
/snap/core22/2293/etc/security/group.conf
/snap/core22/2293/etc/security/limits.conf
/snap/core22/2293/etc/security/namespace.conf
/snap/core22/2293/etc/security/pam_env.conf
/snap/core22/2293/etc/security/sepermit.conf
/snap/core22/2293/etc/security/time.conf
/snap/core22/2293/etc/sudo.conf
/snap/core22/2293/etc/sudo_logsrvd.conf
/snap/core22/2293/etc/sysctl.d/10-console-messages.conf
/snap/core22/2293/etc/sysctl.d/10-ipv6-privacy.conf
/snap/core22/2293/etc/sysctl.d/10-kernel-hardening.conf
/snap/core22/2293/etc/sysctl.d/10-magic-sysrq.conf
/snap/core22/2293/etc/sysctl.d/10-network-security.conf
/snap/core22/2293/etc/sysctl.d/10-ptrace.conf
/snap/core22/2293/etc/sysctl.d/10-zeropage.conf
/snap/core22/2293/etc/systemd/bootchart.conf
/snap/core22/2293/etc/systemd/journald.conf
/snap/core22/2293/etc/systemd/logind.conf
/snap/core22/2293/etc/systemd/networkd.conf
/snap/core22/2293/etc/systemd/pstore.conf
/snap/core22/2293/etc/systemd/resolved.conf
/snap/core22/2293/etc/systemd/sleep.conf
/snap/core22/2293/etc/systemd/system.conf
/snap/core22/2293/etc/systemd/system.conf.d/11-snapd-ctrl-alt-del-burst.conf
/snap/core22/2293/etc/systemd/timesyncd.conf
/snap/core22/2293/etc/systemd/user.conf
/snap/core22/2293/etc/ucf.conf
/snap/core22/2293/etc/udev/udev.conf
/snap/core22/2293/etc/xattr.conf
/snap/core22/2293/run/systemd/resolve/stub-resolv.conf
/snap/core22/2293/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf
/snap/core22/2293/usr/lib/aarch64-linux-gnu/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/core22/2293/usr/lib/arm-linux-gnueabihf/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/core22/2293/usr/lib/binfmt.d/python3.10.conf
/snap/core22/2293/usr/lib/environment.d/99-environment.conf
/snap/core22/2293/usr/lib/environment.d/990-snapd.conf
/snap/core22/2293/usr/lib/finalrd/finalrd-static.conf
/snap/core22/2293/usr/lib/initramfs-tools/etc/dhcp/dhclient.conf
/snap/core22/2293/usr/lib/modprobe.d/aliases.conf
/snap/core22/2293/usr/lib/modprobe.d/fbdev-blacklist.conf
/snap/core22/2293/usr/lib/modprobe.d/systemd.conf
/snap/core22/2293/usr/lib/sysctl.d/50-default.conf
/snap/core22/2293/usr/lib/sysctl.d/50-pid-max.conf
/snap/core22/2293/usr/lib/sysctl.d/99-protect-links.conf
/snap/core22/2293/usr/lib/systemd/bootchart.conf.d/ubuntu-core.conf
/snap/core22/2293/usr/lib/systemd/resolv.conf
/snap/core22/2293/usr/lib/systemd/system/debug-shell.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/emergency.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/emergency.target.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-halt.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-kexec.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-poweroff.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-quit.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-reboot.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/plymouth-start.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/rc-local.service.d/debian.conf
/snap/core22/2293/usr/lib/systemd/system/run-mnt-data.mount.d/late-umount.conf
/snap/core22/2293/usr/lib/systemd/system/run-mnt-kernel.mount.d/late-umount.conf
/snap/core22/2293/usr/lib/systemd/system/run-mnt-ubuntu\x2dseed.mount.d/late-umount.conf
/snap/core22/2293/usr/lib/systemd/system/secureboot-db.service.d/core-override.conf
/snap/core22/2293/usr/lib/systemd/system/sshd-keygen@.service.d/disable-sshd-keygen-if-cloud-init-active.conf
/snap/core22/2293/usr/lib/systemd/system/systemd-bootchart.service.d/ubuntu-core.conf
/snap/core22/2293/usr/lib/systemd/system/systemd-localed.service.d/locale-gen.conf
/snap/core22/2293/usr/lib/systemd/system/user-.slice.d/10-defaults.conf
/snap/core22/2293/usr/lib/systemd/system/user@.service.d/timeout.conf
/snap/core22/2293/usr/lib/systemd/system/usr-lib-modules.mount.d/late-umount.conf
/snap/core22/2293/usr/lib/sysusers.d/basic.conf
/snap/core22/2293/usr/lib/sysusers.d/dbus.conf
/snap/core22/2293/usr/lib/sysusers.d/systemd-journal.conf
/snap/core22/2293/usr/lib/sysusers.d/systemd-network.conf
/snap/core22/2293/usr/lib/sysusers.d/systemd-resolve.conf
/snap/core22/2293/usr/lib/sysusers.d/systemd-timesync.conf
/snap/core22/2293/usr/lib/tmpfiles.d/cryptsetup.conf
/snap/core22/2293/usr/lib/tmpfiles.d/dbus.conf
/snap/core22/2293/usr/lib/tmpfiles.d/debian.conf
/snap/core22/2293/usr/lib/tmpfiles.d/home.conf
/snap/core22/2293/usr/lib/tmpfiles.d/journal-nocow.conf
/snap/core22/2293/usr/lib/tmpfiles.d/journald-conf-d.conf
/snap/core22/2293/usr/lib/tmpfiles.d/legacy.conf
/snap/core22/2293/usr/lib/tmpfiles.d/passwd.conf
/snap/core22/2293/usr/lib/tmpfiles.d/snapd.conf
/snap/core22/2293/usr/lib/tmpfiles.d/static-nodes-permissions.conf
/snap/core22/2293/usr/lib/tmpfiles.d/sudo.conf
/snap/core22/2293/usr/lib/tmpfiles.d/systemd-nologin.conf
/snap/core22/2293/usr/lib/tmpfiles.d/systemd-pstore.conf
/snap/core22/2293/usr/lib/tmpfiles.d/systemd-tmp.conf
/snap/core22/2293/usr/lib/tmpfiles.d/systemd.conf
/snap/core22/2293/usr/lib/tmpfiles.d/tmp.conf
/snap/core22/2293/usr/lib/tmpfiles.d/var.conf
/snap/core22/2293/usr/lib/tmpfiles.d/x11.conf
/snap/core22/2293/usr/share/adduser/adduser.conf
/snap/core22/2293/usr/share/dbus-1/session.conf
/snap/core22/2293/usr/share/dbus-1/system.conf
/snap/core22/2293/usr/share/dbus-1/system.d/io.netplan.Netplan.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.PolicyKit1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.hostname1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.locale1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.login1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.network1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.systemd1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.timedate1.conf
/snap/core22/2293/usr/share/dbus-1/system.d/org.freedesktop.timesync1.conf
/snap/core22/2293/usr/share/libc-bin/nsswitch.conf
/snap/core22/2134/etc/adduser.conf
/snap/core22/2134/etc/apparmor/parser.conf
/snap/core22/2134/etc/ca-certificates.conf
/snap/core22/2134/etc/dbus-1/system.d/wpa_supplicant.conf
/snap/core22/2134/etc/deluser.conf
/snap/core22/2134/etc/depmod.d/ubuntu.conf
/snap/core22/2134/etc/dhcp/dhclient.conf
/snap/core22/2134/etc/e2scrub.conf
/snap/core22/2134/etc/host.conf
/snap/core22/2134/etc/ld.so.conf
/snap/core22/2134/etc/ld.so.conf.d/aarch64-linux-gnu.conf
/snap/core22/2134/etc/ld.so.conf.d/arm-linux-gnueabihf.conf
/snap/core22/2134/etc/ld.so.conf.d/libc.conf
/snap/core22/2134/etc/libaudit.conf
/snap/core22/2134/etc/modprobe.d/blacklist-ath_pci.conf
/snap/core22/2134/etc/modprobe.d/blacklist-firewire.conf
/snap/core22/2134/etc/modprobe.d/blacklist-framebuffer.conf
/snap/core22/2134/etc/modprobe.d/blacklist-rare-network.conf
/snap/core22/2134/etc/modprobe.d/blacklist.conf
/snap/core22/2134/etc/modprobe.d/iwlwifi.conf
/snap/core22/2134/etc/modules-load.d/modules.conf
/snap/core22/2134/etc/nsswitch.conf
/snap/core22/2134/etc/plymouth/plymouthd.conf
/snap/core22/2134/etc/polkit-1/localauthority.conf.d/50-localauthority.conf
/snap/core22/2134/etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf
/snap/core22/2134/etc/resolv.conf
/snap/core22/2134/etc/rsyslog.d/21-cloudinit.conf
/snap/core22/2134/etc/security/access.conf
/snap/core22/2134/etc/security/faillock.conf
/snap/core22/2134/etc/security/group.conf
/snap/core22/2134/etc/security/limits.conf
/snap/core22/2134/etc/security/namespace.conf
/snap/core22/2134/etc/security/pam_env.conf
/snap/core22/2134/etc/security/sepermit.conf
/snap/core22/2134/etc/security/time.conf
/snap/core22/2134/etc/sudo.conf
/snap/core22/2134/etc/sudo_logsrvd.conf
/snap/core22/2134/etc/sysctl.d/10-console-messages.conf
/snap/core22/2134/etc/sysctl.d/10-ipv6-privacy.conf
/snap/core22/2134/etc/sysctl.d/10-kernel-hardening.conf
/snap/core22/2134/etc/sysctl.d/10-magic-sysrq.conf
/snap/core22/2134/etc/sysctl.d/10-network-security.conf
/snap/core22/2134/etc/sysctl.d/10-ptrace.conf
/snap/core22/2134/etc/sysctl.d/10-zeropage.conf
/snap/core22/2134/etc/systemd/bootchart.conf
/snap/core22/2134/etc/systemd/journald.conf
/snap/core22/2134/etc/systemd/logind.conf
/snap/core22/2134/etc/systemd/networkd.conf
/snap/core22/2134/etc/systemd/pstore.conf
/snap/core22/2134/etc/systemd/resolved.conf
/snap/core22/2134/etc/systemd/sleep.conf
/snap/core22/2134/etc/systemd/system.conf
/snap/core22/2134/etc/systemd/system.conf.d/11-snapd-ctrl-alt-del-burst.conf
/snap/core22/2134/etc/systemd/timesyncd.conf
/snap/core22/2134/etc/systemd/user.conf
/snap/core22/2134/etc/ucf.conf
/snap/core22/2134/etc/udev/udev.conf
/snap/core22/2134/etc/xattr.conf
/snap/core22/2134/run/systemd/resolve/stub-resolv.conf
/snap/core22/2134/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf
/snap/core22/2134/usr/lib/aarch64-linux-gnu/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/core22/2134/usr/lib/arm-linux-gnueabihf/gconv/gconv-modules.d/gconv-modules-extra.conf
/snap/core22/2134/usr/lib/binfmt.d/python3.10.conf
/snap/core22/2134/usr/lib/environment.d/99-environment.conf
/snap/core22/2134/usr/lib/environment.d/990-snapd.conf
/snap/core22/2134/usr/lib/finalrd/finalrd-static.conf
/snap/core22/2134/usr/lib/initramfs-tools/etc/dhcp/dhclient.conf
/snap/core22/2134/usr/lib/modprobe.d/aliases.conf
/snap/core22/2134/usr/lib/modprobe.d/fbdev-blacklist.conf
/snap/core22/2134/usr/lib/modprobe.d/systemd.conf
/snap/core22/2134/usr/lib/sysctl.d/50-default.conf
/snap/core22/2134/usr/lib/sysctl.d/50-pid-max.conf
/snap/core22/2134/usr/lib/sysctl.d/99-protect-links.conf
/snap/core22/2134/usr/lib/systemd/bootchart.conf.d/ubuntu-core.conf
/snap/core22/2134/usr/lib/systemd/resolv.conf
/snap/core22/2134/usr/lib/systemd/system/debug-shell.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/emergency.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/emergency.target.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-halt.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-kexec.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-poweroff.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-quit.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-reboot.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/plymouth-start.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/rc-local.service.d/debian.conf
/snap/core22/2134/usr/lib/systemd/system/run-mnt-data.mount.d/late-umount.conf
/snap/core22/2134/usr/lib/systemd/system/run-mnt-kernel.mount.d/late-umount.conf
/snap/core22/2134/usr/lib/systemd/system/run-mnt-ubuntu\x2dseed.mount.d/late-umount.conf
/snap/core22/2134/usr/lib/systemd/system/secureboot-db.service.d/core-override.conf
/snap/core22/2134/usr/lib/systemd/system/sshd-keygen@.service.d/disable-sshd-keygen-if-cloud-init-active.conf
/snap/core22/2134/usr/lib/systemd/system/systemd-bootchart.service.d/ubuntu-core.conf
/snap/core22/2134/usr/lib/systemd/system/systemd-localed.service.d/locale-gen.conf
/snap/core22/2134/usr/lib/systemd/system/user-.slice.d/10-defaults.conf
/snap/core22/2134/usr/lib/systemd/system/user@.service.d/timeout.conf
/snap/core22/2134/usr/lib/systemd/system/usr-lib-modules.mount.d/late-umount.conf
/snap/core22/2134/usr/lib/sysusers.d/basic.conf
/snap/core22/2134/usr/lib/sysusers.d/dbus.conf
/snap/core22/2134/usr/lib/sysusers.d/systemd-journal.conf
/snap/core22/2134/usr/lib/sysusers.d/systemd-network.conf
/snap/core22/2134/usr/lib/sysusers.d/systemd-resolve.conf
/snap/core22/2134/usr/lib/sysusers.d/systemd-timesync.conf
/snap/core22/2134/usr/lib/tmpfiles.d/cryptsetup.conf
/snap/core22/2134/usr/lib/tmpfiles.d/dbus.conf
/snap/core22/2134/usr/lib/tmpfiles.d/debian.conf
/snap/core22/2134/usr/lib/tmpfiles.d/home.conf
/snap/core22/2134/usr/lib/tmpfiles.d/journal-nocow.conf
/snap/core22/2134/usr/lib/tmpfiles.d/journald-conf-d.conf
/snap/core22/2134/usr/lib/tmpfiles.d/legacy.conf
/snap/core22/2134/usr/lib/tmpfiles.d/passwd.conf
/snap/core22/2134/usr/lib/tmpfiles.d/static-nodes-permissions.conf
/snap/core22/2134/usr/lib/tmpfiles.d/sudo.conf
/snap/core22/2134/usr/lib/tmpfiles.d/systemd-nologin.conf
/snap/core22/2134/usr/lib/tmpfiles.d/systemd-pstore.conf
/snap/core22/2134/usr/lib/tmpfiles.d/systemd-tmp.conf
/snap/core22/2134/usr/lib/tmpfiles.d/systemd.conf
/snap/core22/2134/usr/lib/tmpfiles.d/tmp.conf
/snap/core22/2134/usr/lib/tmpfiles.d/var.conf
/snap/core22/2134/usr/lib/tmpfiles.d/x11.conf
/snap/core22/2134/usr/share/adduser/adduser.conf
/snap/core22/2134/usr/share/dbus-1/session.conf
/snap/core22/2134/usr/share/dbus-1/system.conf
/snap/core22/2134/usr/share/dbus-1/system.d/io.netplan.Netplan.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.PolicyKit1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.hostname1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.locale1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.login1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.network1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.resolve1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.systemd1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.timedate1.conf
/snap/core22/2134/usr/share/dbus-1/system.d/org.freedesktop.timesync1.conf
/snap/core22/2134/usr/share/libc-bin/nsswitch.conf
/snap/firefox/7897/usr/share/alsa/alsa.conf
/snap/firefox/7897/usr/share/alsa/cards/AACI.conf
/snap/firefox/7897/usr/share/alsa/cards/ATIIXP-MODEM.conf
/snap/firefox/7897/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/snap/firefox/7897/usr/share/alsa/cards/ATIIXP.conf
/snap/firefox/7897/usr/share/alsa/cards/AU8810.conf
/snap/firefox/7897/usr/share/alsa/cards/AU8820.conf
/snap/firefox/7897/usr/share/alsa/cards/AU8830.conf
/snap/firefox/7897/usr/share/alsa/cards/Audigy.conf
/snap/firefox/7897/usr/share/alsa/cards/Audigy2.conf
/snap/firefox/7897/usr/share/alsa/cards/Aureon51.conf
/snap/firefox/7897/usr/share/alsa/cards/Aureon71.conf
/snap/firefox/7897/usr/share/alsa/cards/CA0106.conf
/snap/firefox/7897/usr/share/alsa/cards/CMI8338-SWIEC.conf
/snap/firefox/7897/usr/share/alsa/cards/CMI8338.conf
/snap/firefox/7897/usr/share/alsa/cards/CMI8738-MC6.conf
/snap/firefox/7897/usr/share/alsa/cards/CMI8738-MC8.conf
/snap/firefox/7897/usr/share/alsa/cards/CMI8788.conf
/snap/firefox/7897/usr/share/alsa/cards/CS46xx.conf
/snap/firefox/7897/usr/share/alsa/cards/EMU10K1.conf
/snap/firefox/7897/usr/share/alsa/cards/EMU10K1X.conf
/snap/firefox/7897/usr/share/alsa/cards/ENS1370.conf
/snap/firefox/7897/usr/share/alsa/cards/ENS1371.conf
/snap/firefox/7897/usr/share/alsa/cards/ES1968.conf
/snap/firefox/7897/usr/share/alsa/cards/Echo_Echo3G.conf
/snap/firefox/7897/usr/share/alsa/cards/FM801.conf
/snap/firefox/7897/usr/share/alsa/cards/FWSpeakers.conf
/snap/firefox/7897/usr/share/alsa/cards/FireWave.conf
/snap/firefox/7897/usr/share/alsa/cards/GUS.conf
/snap/firefox/7897/usr/share/alsa/cards/HDA-Intel.conf
/snap/firefox/7897/usr/share/alsa/cards/HdmiLpeAudio.conf
/snap/firefox/7897/usr/share/alsa/cards/ICE1712.conf
/snap/firefox/7897/usr/share/alsa/cards/ICE1724.conf
/snap/firefox/7897/usr/share/alsa/cards/ICH-MODEM.conf
/snap/firefox/7897/usr/share/alsa/cards/ICH.conf
/snap/firefox/7897/usr/share/alsa/cards/ICH4.conf
/snap/firefox/7897/usr/share/alsa/cards/Loopback.conf
/snap/firefox/7897/usr/share/alsa/cards/Maestro3.conf
/snap/firefox/7897/usr/share/alsa/cards/NFORCE.conf
/snap/firefox/7897/usr/share/alsa/cards/PC-Speaker.conf
/snap/firefox/7897/usr/share/alsa/cards/PMac.conf
/snap/firefox/7897/usr/share/alsa/cards/PMacToonie.conf
/snap/firefox/7897/usr/share/alsa/cards/PS3.conf
/snap/firefox/7897/usr/share/alsa/cards/RME9636.conf
/snap/firefox/7897/usr/share/alsa/cards/RME9652.conf
/snap/firefox/7897/usr/share/alsa/cards/SB-XFi.conf
/snap/firefox/7897/usr/share/alsa/cards/SI7018.conf
/snap/firefox/7897/usr/share/alsa/cards/TRID4DWAVENX.conf
/snap/firefox/7897/usr/share/alsa/cards/USB-Audio.conf
/snap/firefox/7897/usr/share/alsa/cards/VIA686A.conf
/snap/firefox/7897/usr/share/alsa/cards/VIA8233.conf
/snap/firefox/7897/usr/share/alsa/cards/VIA8233A.conf
/snap/firefox/7897/usr/share/alsa/cards/VIA8237.conf
/snap/firefox/7897/usr/share/alsa/cards/VX222.conf
/snap/firefox/7897/usr/share/alsa/cards/VXPocket.conf
/snap/firefox/7897/usr/share/alsa/cards/VXPocket440.conf
/snap/firefox/7897/usr/share/alsa/cards/YMF744.conf
/snap/firefox/7897/usr/share/alsa/cards/aliases.conf
/snap/firefox/7897/usr/share/alsa/cards/pistachio-card.conf
/snap/firefox/7897/usr/share/alsa/cards/vc4-hdmi.conf
/snap/firefox/7897/usr/share/alsa/ctl/default.conf
/snap/firefox/7897/usr/share/alsa/pcm/center_lfe.conf
/snap/firefox/7897/usr/share/alsa/pcm/default.conf
/snap/firefox/7897/usr/share/alsa/pcm/dmix.conf
/snap/firefox/7897/usr/share/alsa/pcm/dpl.conf
/snap/firefox/7897/usr/share/alsa/pcm/dsnoop.conf
/snap/firefox/7897/usr/share/alsa/pcm/front.conf
/snap/firefox/7897/usr/share/alsa/pcm/hdmi.conf
/snap/firefox/7897/usr/share/alsa/pcm/iec958.conf
/snap/firefox/7897/usr/share/alsa/pcm/modem.conf
/snap/firefox/7897/usr/share/alsa/pcm/rear.conf
/snap/firefox/7897/usr/share/alsa/pcm/side.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround21.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround40.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround41.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround50.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround51.conf
/snap/firefox/7897/usr/share/alsa/pcm/surround71.conf
/snap/firefox/7897/usr/share/pipewire/client-rt.conf
/snap/firefox/7897/usr/share/pipewire/client.conf
/snap/firefox/7897/usr/share/pipewire/jack.conf
/snap/firefox/7897/usr/share/pipewire/minimal.conf
/snap/firefox/7897/usr/share/pipewire/pipewire-pulse.conf
/snap/firefox/7897/usr/share/pipewire/pipewire.conf
/snap/firefox/7865/usr/share/alsa/alsa.conf
/snap/firefox/7865/usr/share/alsa/cards/AACI.conf
/snap/firefox/7865/usr/share/alsa/cards/ATIIXP-MODEM.conf
/snap/firefox/7865/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/snap/firefox/7865/usr/share/alsa/cards/ATIIXP.conf
/snap/firefox/7865/usr/share/alsa/cards/AU8810.conf
/snap/firefox/7865/usr/share/alsa/cards/AU8820.conf
/snap/firefox/7865/usr/share/alsa/cards/AU8830.conf
/snap/firefox/7865/usr/share/alsa/cards/Audigy.conf
/snap/firefox/7865/usr/share/alsa/cards/Audigy2.conf
/snap/firefox/7865/usr/share/alsa/cards/Aureon51.conf
/snap/firefox/7865/usr/share/alsa/cards/Aureon71.conf
/snap/firefox/7865/usr/share/alsa/cards/CA0106.conf
/snap/firefox/7865/usr/share/alsa/cards/CMI8338-SWIEC.conf
/snap/firefox/7865/usr/share/alsa/cards/CMI8338.conf
/snap/firefox/7865/usr/share/alsa/cards/CMI8738-MC6.conf
/snap/firefox/7865/usr/share/alsa/cards/CMI8738-MC8.conf
/snap/firefox/7865/usr/share/alsa/cards/CMI8788.conf
/snap/firefox/7865/usr/share/alsa/cards/CS46xx.conf
/snap/firefox/7865/usr/share/alsa/cards/EMU10K1.conf
/snap/firefox/7865/usr/share/alsa/cards/EMU10K1X.conf
/snap/firefox/7865/usr/share/alsa/cards/ENS1370.conf
/snap/firefox/7865/usr/share/alsa/cards/ENS1371.conf
/snap/firefox/7865/usr/share/alsa/cards/ES1968.conf
/snap/firefox/7865/usr/share/alsa/cards/Echo_Echo3G.conf
/snap/firefox/7865/usr/share/alsa/cards/FM801.conf
/snap/firefox/7865/usr/share/alsa/cards/FWSpeakers.conf
/snap/firefox/7865/usr/share/alsa/cards/FireWave.conf
/snap/firefox/7865/usr/share/alsa/cards/GUS.conf
/snap/firefox/7865/usr/share/alsa/cards/HDA-Intel.conf
/snap/firefox/7865/usr/share/alsa/cards/HdmiLpeAudio.conf
/snap/firefox/7865/usr/share/alsa/cards/ICE1712.conf
/snap/firefox/7865/usr/share/alsa/cards/ICE1724.conf
/snap/firefox/7865/usr/share/alsa/cards/ICH-MODEM.conf
/snap/firefox/7865/usr/share/alsa/cards/ICH.conf
/snap/firefox/7865/usr/share/alsa/cards/ICH4.conf
/snap/firefox/7865/usr/share/alsa/cards/Loopback.conf
/snap/firefox/7865/usr/share/alsa/cards/Maestro3.conf
/snap/firefox/7865/usr/share/alsa/cards/NFORCE.conf
/snap/firefox/7865/usr/share/alsa/cards/PC-Speaker.conf
/snap/firefox/7865/usr/share/alsa/cards/PMac.conf
/snap/firefox/7865/usr/share/alsa/cards/PMacToonie.conf
/snap/firefox/7865/usr/share/alsa/cards/PS3.conf
/snap/firefox/7865/usr/share/alsa/cards/RME9636.conf
/snap/firefox/7865/usr/share/alsa/cards/RME9652.conf
/snap/firefox/7865/usr/share/alsa/cards/SB-XFi.conf
/snap/firefox/7865/usr/share/alsa/cards/SI7018.conf
/snap/firefox/7865/usr/share/alsa/cards/TRID4DWAVENX.conf
/snap/firefox/7865/usr/share/alsa/cards/USB-Audio.conf
/snap/firefox/7865/usr/share/alsa/cards/VIA686A.conf
/snap/firefox/7865/usr/share/alsa/cards/VIA8233.conf
/snap/firefox/7865/usr/share/alsa/cards/VIA8233A.conf
/snap/firefox/7865/usr/share/alsa/cards/VIA8237.conf
/snap/firefox/7865/usr/share/alsa/cards/VX222.conf
/snap/firefox/7865/usr/share/alsa/cards/VXPocket.conf
/snap/firefox/7865/usr/share/alsa/cards/VXPocket440.conf
/snap/firefox/7865/usr/share/alsa/cards/YMF744.conf
/snap/firefox/7865/usr/share/alsa/cards/aliases.conf
/snap/firefox/7865/usr/share/alsa/cards/pistachio-card.conf
/snap/firefox/7865/usr/share/alsa/cards/vc4-hdmi.conf
/snap/firefox/7865/usr/share/alsa/ctl/default.conf
/snap/firefox/7865/usr/share/alsa/pcm/center_lfe.conf
/snap/firefox/7865/usr/share/alsa/pcm/default.conf
/snap/firefox/7865/usr/share/alsa/pcm/dmix.conf
/snap/firefox/7865/usr/share/alsa/pcm/dpl.conf
/snap/firefox/7865/usr/share/alsa/pcm/dsnoop.conf
/snap/firefox/7865/usr/share/alsa/pcm/front.conf
/snap/firefox/7865/usr/share/alsa/pcm/hdmi.conf
/snap/firefox/7865/usr/share/alsa/pcm/iec958.conf
/snap/firefox/7865/usr/share/alsa/pcm/modem.conf
/snap/firefox/7865/usr/share/alsa/pcm/rear.conf
/snap/firefox/7865/usr/share/alsa/pcm/side.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround21.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround40.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround41.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround50.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround51.conf
/snap/firefox/7865/usr/share/alsa/pcm/surround71.conf
/snap/firefox/7865/usr/share/pipewire/client-rt.conf
/snap/firefox/7865/usr/share/pipewire/client.conf
/snap/firefox/7865/usr/share/pipewire/jack.conf
/snap/firefox/7865/usr/share/pipewire/minimal.conf
/snap/firefox/7865/usr/share/pipewire/pipewire-pulse.conf
/snap/firefox/7865/usr/share/pipewire/pipewire.conf
```

---
## Latihan 3.5

**Code** : 

Buat file Script
```bash
nano backup_script.sh
```
Isi Script
```bash
SOURCE_DIR="$HOME/praktikum-os"
BACKUP_FILE="backup_$(date +%Y%m%d_%H%M%S).tar.gz"
echo "--- Backup started at $(date) ---" | tee -a backup-success.log
tar -vczf "$BACKUP_FILE" "$SOURCE_DIR" 2> >(while read line; do echo "$(date): $line"; done >> backup-error.log) | while read line; do echo "$(date): $line"; done | tee -a backup-success.log
echo "--- Backup finished at $(date) ---" | tee -a backup-success.log
```
Beri izin
```bash
chmod +x backup_script.sh
```
Run Script
```bash
./backup_script.sh
```

**Output** : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ nano backup_script.sh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ chmod +x backup_script.sh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week03$ ./backup_script.sh
--- Backup started at Tue Mar  3 19:24:59 WIB 2026 ---
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/data.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/latihan.txt
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/config.txt
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/notes.txt
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week02/server.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/error.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/backup_20260303_192459.tar.gz
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/monitor.sh
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/sorted-users.txt
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/backup-error.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/backup_script.sh
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/monitoring.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/backup-success.log
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/config-files.txt
Tue Mar  3 19:24:59 WIB 2026: /home/ibennn/praktikum-os/week03/large-logs.txt
--- Backup finished at Tue Mar  3 19:24:59 WIB 2026 ---

```
