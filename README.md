# How to configure TLS for VSFTPD

As the name suggest 'Very Secure File Transfer Protocol Deamon' (VSFTPD) is one of the most secure FTP daemons available, vsftpd is used as the default FTP server in the Ubuntu, CentOS, Fedora, NimbleX, Slackware and RHEL Linux distros. It is authorized under the GNU General Public License. It is secure and very quick. It is stable. VSFTPD is a developed and trusted arrangement which sustains virtual clients with PAM (pluggable confirmation modules). In this short tutorial we will see how to secure your FTP connections with TLS. 

## Configuring TLS/SSL/FTPS

If you connect to your system remotely then you should go through these settings thoroughly, or else your passwords will be sent in plain text. Just make sure to add these options to your config file, some of them are already available check those and then change the options.

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
# listen_port=990
```

This will be it with the basic configuration part.

To apply the above settings just close your config file and type:
```
sudo /etc/init.d/vsftpd restart
```
Restarting the service will use the new settings and you are done :)

## To make it easier
If you don't wanna mess with the config file, you can just run our script that will do all the work for you:

```sh
wget -nv https://raw.githubusercontent.com/EasyFixIt/FTP_ubuntu_TLS/master/FTP_TLS.sh && sudo bash FTP_TLS.sh; rm -f FTP_TLS.sh
```
