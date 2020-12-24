# WSL-autostart-service
1.  sudo visudo<br>
    %sudo ALL=NOPASSWD: /etc/init.d/cron<br>
    %sudo ALL=NOPASSWD: /etc/init.d/nginx<br>
    %sudo ALL=NOPASSWD: /etc/init.d/php-fpm<br>
    %sudo ALL=NOPASSWD: /etc/init.d/ssh<br>
    %sudo ALL=NOPASSWD: /etc/init.d/xrdp
2. Task Scheduler<br>
    Run wheter user log on or not<br>
    Program/script : %windir%\System32\bash.exe<br>
    Add arguments (optional) : -c "sudo /etc/init.d/ssh start"
