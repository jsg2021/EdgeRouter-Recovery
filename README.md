# EdgeRouter-Recovery

Install a TFTP Server on a computer attached to the local network, or direct to eth0. 
<details>
<summary>macOS tftp</summary>
```bash
sudo launchctl load -F /System/Library/LaunchDaemons/tftp.plist
sudo launchctl start com.apple.tftpd
sudo chmod 777 /private/tftpboot

# to stop
sudo launchctl stop com.apple.tftpd
sudo launchctl unload -F /System/Library/LaunchDaemons/tftp.plist
```
</details>
Use the following commands to boot:

```shell
set ipaddr <free ip on local network>
dhcp
setenv serverip <ip of host pc>
setenv ethact octeth0
tftpboot 0 emrk-0.9c.bin
bootoctlinux 0
```

once tool is booted, run `emrk-reinstall`, answer yes... use latest firmware: (not https) http://dl.ui.com/firmwares/edgemax/v2.0.9-hotfix.4/ER-e100.v2.0.9-hotfix.4.5521907.tar


