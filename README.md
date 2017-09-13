/tmp/scm_prepare_node.Y29CuxV1 
using SSH_CLIENT to get the SCM hostname: 10.237.36.112 44668 22 
opening logging file descriptor 
Starting installation script...
Acquiring installation lock...
BEGIN flock 4 
END (0) 
Detecting root privileges...
effective UID is 0 
Detecting distribution...
BEGIN grep 'Ubuntu' /etc/lsb-release 
DISTRIB_ID=Ubuntu 
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS" 
END (0) 
BEGIN grep DISTRIB_CODENAME /etc/lsb-release 
DISTRIB_CODENAME=xenial 
END (0) 
BEGIN echo DISTRIB_CODENAME=xenial | cut -d = -f 2 
END (0) 
xenial 
Detecting Cloudera Manager Server...
BEGIN host -t PTR 10.237.36.112 
Host 112.36.237.10.in-addr.arpa. not found: 3(NXDOMAIN) 
END (1) 
BEGIN which python 
END (0) 
/usr/bin/python 
BEGIN python -c 'import socket; import sys; s = socket.socket(socket.AF_INET); s.settimeout(5.0); s.connect((sys.argv[1], int(sys.argv[2]))); s.close();' 10.237.36.112 7182 
END (0) 
BEGIN which wget 
/usr/bin/wget 
END (0) 
BEGIN wget -qO- -T 1 -t 1 http://169.254.169.254/latest/meta-data/public-hostname && /bin/echo 
END (4) 
Installing package repositories...
validating format of repository file /tmp/scm_prepare_node.Y29CuxV1/repos/ubuntu_xenial/cloudera-manager.list 
installing repository file /tmp/scm_prepare_node.Y29CuxV1/repos/ubuntu_xenial/cloudera-manager.list 
repository file /tmp/scm_prepare_node.Y29CuxV1/repos/ubuntu_xenial/cloudera-manager.list installed 
BEGIN apt-key add /tmp/scm_prepare_node.Y29CuxV1/archive.key 
OK 
END (0) 
installing priority file /tmp/scm_prepare_node.Y29CuxV1/priorities/ubuntu_xenial/cloudera.pref 
priority file /tmp/scm_prepare_node.Y29CuxV1/priorities/ubuntu_xenial/cloudera.pref installed 
Refreshing package metadata...
BEGIN apt-get update 
Hit:1 http://repo.mysql.com/apt/ubuntu xenial InRelease 
Hit:2 http://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm xenial-cm5 InRelease 
Hit:3 https://archive.cloudera.com/cdh5/ubuntu/precise/amd64/cdh precise-cdh5 InRelease 
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease 
Hit:5 http://in.archive.ubuntu.com/ubuntu xenial InRelease 
Hit:6 https://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm xenial-cm5.12.1 InRelease 
Hit:7 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease 
Hit:8 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease 
Reading package lists... 
W: http://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm/dists/xenial-cm5/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
W: https://archive.cloudera.com/cdh5/ubuntu/precise/amd64/cdh/dists/precise-cdh5/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
W: https://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm/dists/xenial-cm5.12.1/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
END (0) 
BEGIN apt-get update 
Hit:1 http://repo.mysql.com/apt/ubuntu xenial InRelease 
Hit:2 http://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm xenial-cm5 InRelease 
Hit:3 https://archive.cloudera.com/cdh5/ubuntu/precise/amd64/cdh precise-cdh5 InRelease 
Hit:4 https://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm xenial-cm5.12.1 InRelease 
Hit:5 http://in.archive.ubuntu.com/ubuntu xenial InRelease 
Hit:6 http://security.ubuntu.com/ubuntu xenial-security InRelease 
Hit:7 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease 
Hit:8 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease 
Reading package lists... 
W: http://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm/dists/xenial-cm5/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
W: https://archive.cloudera.com/cdh5/ubuntu/precise/amd64/cdh/dists/precise-cdh5/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
W: https://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm/dists/xenial-cm5.12.1/InRelease: Signature by key F36A89E33CC1BD0F71079007327574EE02A818DD uses weak digest algorithm (SHA1) 
END (0) 
Installing cloudera-manager-agent package...
BEGIN dpkg -l cloudera-manager-agent | grep -E '^ii[[:space:]]*cloudera-manager-agent[[:space:]]*' 
ii cloudera-manager-agent 5.12.1-1.cm5121.p0.6~xenial-cm5 amd64 The Cloudera Manager Agent 
END (0) 
BEGIN echo oracle-j2sdk1.6 oracle-j2sdk1.7 cloudera-manager-agent cloudera-manager-daemons | grep cloudera-manager-agent 
oracle-j2sdk1.6 oracle-j2sdk1.7 cloudera-manager-agent cloudera-manager-daemons 
END (0) 
BEGIN apt-cache show cloudera-manager-agent 
Package: cloudera-manager-agent 
Source: enterprise 
Version: 5.12.1-1.cm5121.p0.6~xenial-cm5 
Architecture: amd64 
Maintainer: Cloudera Inc. <https://issues.cloudera.org> 
Installed-Size: 44057 
Depends: libc6 (>= 2.17), libcomerr2 (>= 1.01), libgcc1 (>= 1:3.0), libgssapi-krb5-2 (>= 1.10+dfsg~), libkrb5-3 (>= 1.6.dfsg.2), libssl1.0.0 (>= 1.0.2~beta3), libstdc++6 (>= 5.2), zlib1g (>= 1:1.2.0), lsb-base, psmisc, bash, libsasl2-modules, libsasl2-modules-gssapi-mit, libxslt1.1, libsqlite3-0, openssl, libssl-dev, libfuse2, fuse-utils | fuse, rpcbind, cloudera-manager-daemons (= 5.12.1-1.cm5121.p0.6~xenial-cm5), perl, python-psycopg2, python-mysqldb, apache2, iproute2 
Homepage: http://www.cloudera.com 
Priority: extra 
Section: misc 
Filename: pool/contrib/e/enterprise/cloudera-manager-agent_5.12.1-1.cm5121.p0.6~xenial-cm5_amd64.deb 
Size: 11200232 
SHA256: 4d7f39084478767515d4e7b3f97b21c2c860ee8ba8890fdfe00d92dc09cc1f5c 
SHA1: 3a1ee4f687940eb45ded50210cb4555b6a0e2349 
MD5sum: 6514449f4bb12e35a3bd6e3b72fba7dd 
Description: The Cloudera Manager Agent 
The Agent is deployed to machines running services managed by Cloudera Manager. 
Description-md5: 482a592ee859d31443f58aa3e48fe303 

END (0) 
Version: 5.12.1-1.cm5121.p0.6~xenial-cm5 
BEGIN apt-get -o Dpkg::Options::=--force-confdef -o Dpkg::Options::=--force-confold -y install cloudera-manager-agent 
Reading package lists... 
Building dependency tree... 
Reading state information... 
cloudera-manager-agent is already the newest version (5.12.1-1.cm5121.p0.6~xenial-cm5). 
0 upgraded, 0 newly installed, 0 to remove and 210 not upgraded. 
END (0) 
remote package cloudera-manager-agent installed 
Installing cloudera-manager-daemons package...
BEGIN dpkg -l cloudera-manager-daemons | grep -E '^ii[[:space:]]*cloudera-manager-daemons[[:space:]]*' 
ii cloudera-manager-daemons 5.12.1-1.cm5121.p0.6~xenial-cm5 all Provides daemons for monitoring Hadoop and related tools. 
END (0) 
BEGIN echo oracle-j2sdk1.6 oracle-j2sdk1.7 cloudera-manager-agent cloudera-manager-daemons | grep cloudera-manager-daemons 
oracle-j2sdk1.6 oracle-j2sdk1.7 cloudera-manager-agent cloudera-manager-daemons 
END (0) 
BEGIN apt-cache show cloudera-manager-daemons 
Package: cloudera-manager-daemons 
Source: enterprise 
Version: 5.12.1-1.cm5121.p0.6~xenial-cm5 
Architecture: all 
Maintainer: Cloudera Inc. <https://issues.cloudera.org> 
Installed-Size: 855727 
Depends: perl 
Homepage: http://www.cloudera.com 
Priority: extra 
Section: misc 
Filename: pool/contrib/e/enterprise/cloudera-manager-daemons_5.12.1-1.cm5121.p0.6~xenial-cm5_all.deb 
Size: 725069466 
SHA256: c459d7b9e7b2147e57f9c4f90ad314abb5287bfa7e50043dc6754093ff3ef839 
SHA1: a206fee98b64fdd6e0e92502a303fe10abca57e8 
MD5sum: 07a37ba0250ffe18ad511082dd4ec78f 
Description: Provides daemons for monitoring Hadoop and related tools. 
Provides daemons for monitoring Hadoop and related tools. 
Description-md5: 35bb5bc8fc2f296f791c3bda9e345340 

END (0) 
Version: 5.12.1-1.cm5121.p0.6~xenial-cm5 
BEGIN apt-get -o Dpkg::Options::=--force-confdef -o Dpkg::Options::=--force-confold -y install cloudera-manager-daemons 
Reading package lists... 
Building dependency tree... 
Reading state information... 
cloudera-manager-daemons is already the newest version (5.12.1-1.cm5121.p0.6~xenial-cm5).
0 upgraded, 0 newly installed, 0 to remove and 210 not upgraded. 
END (0) 
remote package cloudera-manager-daemons installed 
Installing Unlimited Strength Encryption policy files.
Installation not requested. Step will be skipped. 
Configuring Cloudera Manager Agent...
BEGIN grep server_host=10.237.36.112 /etc/cloudera-scm-agent/config.ini 
server_host=10.237.36.112 
END (0) 
scm agent is already configured 
BEGIN sed -e 's/#\(USER=.*\)/\1/' -i /etc/default/cloudera-scm-agent 
END (0) 
Starting Cloudera Manager Agent...
BEGIN /usr/sbin/service cloudera-scm-agent status 
* cloudera-scm-agent.service - LSB: Cloudera SCM Agent 
Loaded: loaded (/etc/init.d/cloudera-scm-agent; bad; vendor preset: enabled) 
Active: active (exited) since Wed 2017-09-13 11:55:55 IST; 1min 22s ago 
Docs: man:systemd-sysv-generator(8) 
Process: 14503 ExecStop=/etc/init.d/cloudera-scm-agent stop (code=exited, status=0/SUCCESS) 
Process: 14544 ExecStart=/etc/init.d/cloudera-scm-agent start (code=exited, status=0/SUCCESS) 

Sep 13 11:55:53 PC355406 systemd[1]: Starting LSB: Cloudera SCM Agent... 
Sep 13 11:55:53 PC355406 su[14563]: Successful su for cloudera-scm by root 
Sep 13 11:55:53 PC355406 su[14563]: + ??? root:cloudera-scm 
Sep 13 11:55:53 PC355406 su[14563]: pam_unix(su:session): session opened for user cloudera-scm by (uid=0) 
Sep 13 11:55:55 PC355406 cloudera-scm-agent[14544]: Starting cloudera-scm-agent: * cloudera-scm-agent started 
Sep 13 11:55:55 PC355406 systemd[1]: Started LSB: Cloudera SCM Agent. 
END (0) 
BEGIN /usr/sbin/service cloudera-scm-agent restart 
END (0) 
agent logs: 
BEGIN tail -n 50 /var/log/cloudera-scm-agent//cloudera-scm-agent.out | sed 's/^/>>/' 
>>[06/Sep/2017 11:48:04 +0000] 4465 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>[06/Sep/2017 11:48:04 +0000] 4465 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[12/Sep/2017 21:08:41 +0000] 1393 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:49:06 +0000] 9087 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:51:08 +0000] 10430 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:51:50 +0000] 11731 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:53:43 +0000] 13179 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:55:55 +0000] 14565 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:260: SyntaxWarning: name 'REDACTOR' is assigned to before global declaration 
>> global REDACTOR 
>>/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/redaction.py:261: SyntaxWarning: name 'NOP_REDACTOR' is assigned to before global declaration 
>> global NOP_REDACTOR 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent INFO SCM Agent Version: 5.12.1 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent WARNING Expected mode 0751 for /run/cloudera-scm-agent but was 0755 
>>[13/Sep/2017 11:57:19 +0000] 15897 MainThread agent INFO Re-using pre-existing directory: /run/cloudera-scm-agent 
END (0) 
BEGIN tail -n 50 /var/log/cloudera-scm-agent//cloudera-scm-agent.log | sed 's/^/>>/' 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:12 +0000] 14579 MainThread agent ERROR Heartbeating to 10.237.36.112:7182 failed. 
>>Traceback (most recent call last): 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/agent.py", line 1409, in _send_heartbeat 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:17 +0000] 14579 MainThread agent ERROR Heartbeating to 10.237.36.112:7182 failed. 
>>Traceback (most recent call last): 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/agent.py", line 1409, in _send_heartbeat 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO Stopping agent... 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO 1 processes are being managed; Supervisor will continue to run. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE HTTP Server cherrypy._cpwsgi_server.CPWSGIServer(('PC355406', 9000)) shut down 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Stopped thread '_TimeoutMonitor'. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE HTTP Server cherrypy._cpwsgi_server.CPWSGIServer(('PC355406', 9000)) already shut down 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE No thread running for None. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus EXITING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus EXITED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO Agent exiting; caught signal 15 
>>[13/Sep/2017 11:57:18 +0000] 14579 Dummy-13 daemonize WARNING Stopping daemon. 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:12 +0000] 14579 MainThread agent ERROR Heartbeating to 10.237.36.112:7182 failed. 
>>Traceback (most recent call last): 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/agent.py", line 1409, in _send_heartbeat 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:17 +0000] 14579 MainThread agent ERROR Heartbeating to 10.237.36.112:7182 failed. 
>>Traceback (most recent call last): 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/agent.py", line 1409, in _send_heartbeat 
>> self.max_cert_depth) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/cmf-5.12.1-py2.7.egg/cmf/https.py", line 134, in __init__ 
>> self.conn.connect() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/httpslib.py", line 59, in connect 
>> sock.connect((self.host, self.port)) 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 195, in connect 
>> ret = self.connect_ssl() 
>> File "/usr/lib/cmf/agent/build/env/lib/python2.7/site-packages/M2Crypto-0.24.0-py2.7-linux-x86_64.egg/M2Crypto/SSL/Connection.py", line 188, in connect_ssl 
>> return m2.ssl_connect(self.ssl, self._timeout) 
>>SSLError: unknown protocol 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO Stopping agent... 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO 1 processes are being managed; Supervisor will continue to run. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE HTTP Server cherrypy._cpwsgi_server.CPWSGIServer(('PC355406', 9000)) shut down 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Stopped thread '_TimeoutMonitor'. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE HTTP Server cherrypy._cpwsgi_server.CPWSGIServer(('PC355406', 9000)) already shut down 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE No thread running for None. 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus STOPPED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus EXITING 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread _cplogging INFO [13/Sep/2017:11:57:18] ENGINE Bus EXITED 
>>[13/Sep/2017 11:57:18 +0000] 14579 MainThread agent INFO Agent exiting; caught signal 15 
>>[13/Sep/2017 11:57:18 +0000] 14579 Dummy-13 daemonize WARNING Stopping daemon. 
END (0) 
end of agent logs. 
scm agent restarted 
Installation script completed successfully.
all done 
closing logging file descriptor 
