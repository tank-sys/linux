<ul>
<li>
wget https://bin.equinox.io/c/VdrWdbjqyF/cloudflared-stable-linux-amd64.rpm
</li>
<li>
cloudflared -v
</li>
<li>
useradd -s /usr/sbin/nologin -r -M cloudflared
</li>
<li>
mkdir /etc/cloudflared/<br>
nano /etc/cloudflared/config.yml
<pre>
proxy-dns: true
proxy-dns-port: 5053
proxy-dns-upstream:
  - https://doh-sg.blahdns.com/uncensor
 

</pre>
</li>
<li>
/usr/local/bin/cloudflared service install<br>
systemctl start cloudflared<br>
systemctl status cloudflared
</li>
</ul>
