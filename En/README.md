# How to use termux-x11 with nethunter root

1) Installation and setting up of termux and termux-x11:

  * Install termux from fdroid, run termux
  * Run commands:
  ```
$ pkg update && pkg upgrade
$ pkg intall x11-repo
$ pkg install root-repo
$ pkg install termux-x11-nightly tsu
  ```
  * Uncomment `allow-external-apps = true` in `termux_home/.termux/termux.properties`
  * Download termux-x11 apk from [Github](https://github.com/termux/termux-x11/releases/tag/nightly)
  * Test termux-x11: run
   ```
$ termux-x11 :1 &
$ pkg install firefox-esr     # or any GUI application
$ export DISPLAY=:1
$ firefox                     # or the application you installed
$ kill -                      # - is termux-x11 PID
   ```
2) Script to run termux-x11 from android shell

  * `# wget https://github.com/erophey7/termux-x11-with-nethunter-root/blob/main/x11_start -O path/to/script/x11_start` recomended path: `
/data/data/com.offsec.nhterm/files/home/.nhterm/script/x11_start`

 * `# nano path/to/script/x11_start`
  Edit `export USER=` with termux output without root `whoami`

  * Save the script and run from root `chmod +x path/to/script/x11_start`

3) Usage
  * Run script from root shell `path/to/script/x11_start :1` :1 is display number
  * Set display in kali shell `export DISPLAY=:1`
  * Run GUI app in kali shell

