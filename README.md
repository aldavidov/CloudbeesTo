# CloudbeesTo

12. $ cat ~/Conjur/policies/root.yml
13.	$ cat ~/Conjur/policies/jenkins.yml
14.	$ cat ~/Conjur/policies/butlers-pets.yml
15. $ docker exec conjur_client_1 conjur authn whoami

16. $ docker exec conjur_client_1 conjur policy load root /policies/root.yml
17. $ docker exec conjur_client_1 conjur policy load jenkins /policies/jenkins.yml

Copy the API KEYS !!!

26. docker exec conjur_client_1 conjur policy load butlers-pets /policies/butlers-pets.yml

27. $ docker exec conjur_client_1 conjur list

28.
$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_global_address 10.0.0.1

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_global_username global_dev

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_global_password globalpassword

29.
$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev1_address 10.0.0.1

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev1_username dev_group_1

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev1_password dev1password

30.
$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev2_address 10.0.0.1

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev2_username dev_group_2

$ docker exec conjur_client_1 conjur variable values add butlers-pets/mysql_dev2_password dev2password

31.docker exec conjur_client_1 conjur variable value butlers-pets/mysql_global_password

32.
Variable Path: butlers-pets/mysql_global_address
ID: mysql_address

34.
Global Credentials<br>
Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_global_username<br>
ID: mysql_username<br>

Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_global_password<br>
ID: mysql_password<br>

36.
Dev Group 1<br>
Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev1_address<br>
ID: mysql_address<br>

Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev1_username<br>
ID: mysql_username<br>

Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev1_password<br>
ID: mysql_password<br>

----------------------------------------------------

Dev Group 2<br>
Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev2_address<br>
ID: mysql_address<br>

Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev2_username<br>
ID: mysql_username<br>

Kind: Conjur Secret Credential<br>
Scope: Global<br>
Variable Path: butlers-pets/mysql_dev2_password<br>
ID: mysql_password<br>


38.
Account:			cloudbeesdays<br>
Appliance URL:		http://conjuross.cloudbeesdays.demo:8081<br>
Conjur Auth Credential:	host/jenkins/global<br>

40. /home/training/Conjur/jenkinsfiles/global/Jenkinsfile

46. /home/training/Conjur/jenkinsfiles/dev_group_1/Jenkinsfile

