# Installing nginx from scratch
<ol>
<li>apt install -y build-essential git tree software-properties-common dirmngr apt-transport-https<br>
  yum groupinstall 'Development Tools'<br>
  dnf install epel-release
</li><li>apt install -y perl libperl-dev libgd3 libgd-dev libgeoip1 libgeoip-dev geoip-bin libxml2 libxml2-dev libxslt1.1 libxslt1-dev<br>
  dnf install perl perl-devel perl-ExtUtils-Embed libxslt libxslt-devel libxml2 libxml2-devel gd gd-devel GeoIP GeoIP-devel
</li><li>Download source nginx terbal file
</li><li>Download modules
<ul>
  <li>PCRE version 8.44<br>
wget https://ftp.pcre.org/pub/pcre/pcre-8.44.tar.gz && tar xzvf pcre-8.44.tar.gz
 </li>  <li>
zlib version 1.2.11<br>
wget https://www.zlib.net/zlib-1.2.11.tar.gz && tar xzvf zlib-1.2.11.tar.gz
   </li><li>
OpenSSL version 1.1.1h<br>
wget https://www.openssl.org/source/openssl-1.1.1h.tar.gz && tar xzvf openssl-1.1.1h.tar.gz
</li>
 <li>
git clone https://github.com/aperezdc/ngx-fancyindex.git ngx-fancyindex   
 </li>  
</ul>
  
</li><li>./configure (lihat skrip)
</li><li>make
</li><li>make install
</li><li>ln -s /usr/lib/nginx/modules /etc/nginx/modules
</li><li>adduser --system --home /nonexistent --shell /bin/false --no-create-home --disabled-login --disabled-password --gecos "nginx user" --group nginx<br>
  useradd --system --home /var/cache/nginx --shell /sbin/nologin --comment "nginx user" --user-group nginx
</li><li>mkdir -p /var/cache/nginx
</li><li>nano /etc/systemd/system/nginx.service<br><pre>
  [Unit]
Description=nginx - high performance web server
Documentation=https://nginx.org/en/docs/
After=network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/var/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t -c /etc/nginx/nginx.conf
ExecStart=/usr/sbin/nginx -c /etc/nginx/nginx.conf
ExecReload=/bin/kill -s HUP $MAINPID
ExecStop=/bin/kill -s TERM $MAINPID

[Install]
WantedBy=multi-user.target
</pre>
</li><li>systemctl enable nginx.service<br>
systemctl start nginx.service
</li><li>
Checking...
<pre>systemctl status nginx.service
 or
curl -I 127.0.0.1
</pre>
</li><li>
  Create Uncomplicated Firewall (UFW) Nginx application profile:
  <pre>
[nginx HTTP]
title=Web Server (nginx, HTTP)
description=Small, but very powerful and efficient web server
ports=80/tcp

[nginx HTTPS]
title=Web Server (nginx, HTTPS)
description=Small, but very powerful and efficient web server
ports=443/tcp

[nginx Full]
title=Web Server (nginx, HTTP + HTTPS)
description=Small, but very powerful and efficient web server
ports=80,443/tcp
</pre>
</li><li>Sudah bosan mau buang ? <br>
  <pre>
make deinstall clean
rm -rf /etc/nginx /etc/default/nginx /usr/sbin/nginx* /usr/local/nginx /var/run/nginx.pid /var/log/nginx

</pre>     
</li>
</ol>
