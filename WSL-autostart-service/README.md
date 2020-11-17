# WSL-autostart-service
1.  sudo visudo
    %sudo ALL=NOPASSWD: /etc/init.d/cron
    %sudo ALL=NOPASSWD: /etc/init.d/nginx
    %sudo ALL=NOPASSWD: /etc/init.d/php-fpm
    %sudo ALL=NOPASSWD: /etc/init.d/ssh
    %sudo ALL=NOPASSWD: /etc/init.d/xrdp
2. Task Scheduler
    Run wheter user log on or not
    Program/script : %windir%\System32\bash.exe
    Add arguments (optional) : -c "sudo /etc/init.d/ssh start"
