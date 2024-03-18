# Как использовать Termux-x11 вместе с Kali Nethunter

1) Установка и настройка Termux и Termux-x11:

  * Установка Termux и Termux-x11 с Fdroid
  * Выполните в Termux:
  ```
$ pkg update && pkg upgrade
$ pkg intall x11-repo
$ pkg install root-repo
$ pkg install termux-x11-nightly tsu
  ```
  * раскомментируйте `allow-external-apps = true` в `termux_home/.termux/termux.properties`
  * Скачайте и установите Termux-x11 с [Github](https://github.com/termux/termux-x11/releases/tag/nightly)
  * Тест Termux-x11:
   ```
$ termux-x11 :1 &
$ pkg install firefox-esr     # или любое другое приложние с графическим интерфейсом
$ export DISPLAY=:1
$ firefox                     # или приложение которе вы установили
$ kill -                      # - это termux-x11 PID
   ```
2) Скрипт для запуска Termux-x11 из Android root shell:

  * `# wget https://github.com/erophey7/termux-x11-with-nethunter-root/blob/main/x11_start -O path/to/script/x11_start` рекомендованое расположение: `
/data/data/com.offsec.nhterm/files/home/.nhterm/script/x11_start`

 * `# nano path/to/script/x11_start`
  Отредактируйте `export USER=` выводом `whoami` из termux без рута

  * Сохраните скрипт и запустите от имени рута `chmod +x path/to/script/x11_start`

3) Использование:
  * Запустите скрипт из root shell `path/to/script/x11_start :1` :1 это номер дисплея
  * Установите дисплей в kali shell `export DISPLAY=:1`
  * Запуск PulseAudio: `export PULSE_SERVER=127.0.0.1 && pulseaudio --start --disable-shm=1 --exit-idle-time=-1`
  * Запустите приложние с графическим интерфейсом в kali shell
  * Для автоматизации добавте в  ~/.bashrc следующие строки:
 ```
export DISPLAY=:1
export PULSE_SERVER=127.0.0.1 && pulseaudio --start --disable-shm=1 --exit-idle-time=-1 &>>
 ```
  
