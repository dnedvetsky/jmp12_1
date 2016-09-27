Notes before verification:
1. mod_jk.so - wasn't working for my combination of Apache/Tomkat - tried every file version and this resulted only in
failures during initialization; Even simple mod inclusion. So Tomcat + Apache was connected by using proxy just to
finish required task.
2. Web MVC application was mostly taken from Internet mycong guides. Only difference - another page helloWorld which
added random string at the end of the message.


To deploy given application:
1. Install Apache/Tomcat.
2. Navigate to httpd.conf and:
- Uncomment (if commented) "LoadModule proxy_module modules/mod_proxy.so"
- Add:
<VirtualHost *:80>
  ServerAdmin <admin name>
  DocumentRoot "c:/xampp/apache/htdocs"
  ServerName localhost
  ErrorLog "logs/localhost-error.log"
  CustomLog "logs/localhost-access.log" common
  ProxyRequests off
  ProxyPreserveHost on
  ProxyPass /jmp http://localhost:8080/jmp/
  ProxyPassReverse /jmp http://localhost:8080/jmp/
</VirtualHost>
3. Navigate to link localhost:8080/manager (input username and password)
4. Deploy provided jmp.war file.

Re-initiate Apache;
Navigate to localhost/jmp (page should be displayed). localhost/jmp/helloWorld will display hello world page