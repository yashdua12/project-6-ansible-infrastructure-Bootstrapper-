# project-6-ansible-infrastructure-Bootstrapper-
these repo includes ansible roles that bootstrap 3 instances at the same time 
1. in this repo there is a inventory.yaml file that includes ips of ec2 instances and path ssh login key file of the target instances
2. in this repo there is a physically made ansible.cfg file that includes path of inventory file and ansible.log file , note prepare this in the same directory where your whole project is
3. in this repo there is a ansible yaml playbook that consists of roles like users,nginx,tomcat,ssh,firewall,memcached,dbiniti,update
4. in this repo there is a role directory and its structure looks like this:-
   ├── dbiniti
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── firewall
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── memcached
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── nginx
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── ssh
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── tomcat
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── updates
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
└── users
    ├── README.md
    ├── defaults
    │   └── main.yml
    ├── files
    │   ├── ansible
    │   └── ansible.pub
    ├── handlers
    │   └── main.yml
    ├── meta
    │   └── main.yml
    ├── tasks
    │   └── main.yml
    ├── templates
    ├── tests
    │   ├── inventory
    │   └── test.yml
    └── vars
        └── main.yml
5. these ansible tasks are defined in tasks folder in main.yml file in each roles
6. -> users role is for creating a user and adding it o sudo group with ssh key
7. -> ssh role is for disbaling root login and password authentication from target instances
8. -> firewall role is for installing firewall and allowing ssh traffic from that firewall only
9. -> tomcat role is for installing and setting up tomcat 9 version
10. -> nginx role is for installing and setting up nginx
11. -> dbiniti role is for installing and setting up mysql database in target instances
12. -> memcached role is for installing and setting up memcached
13. -> update role is for updating and upgrading existing packages in target instances
14. if you want to test connection of instances with your inventory file run command -> ansbile webhosts -m ping
15. it should show connection established of instances if not check ansible.cfg file or inventory file and make changes according to your info
16. to make roles first make a mkdir roles dir then cd into and run following commands :-
    -> ansible-galaxy init users
    -> ansible-galaxy init ssh
    -> ansible-galaxy init firewall
    -> ansible-galaxy init tomcat
    -> ansible-galaxy init nginx
    -> ansible-galaxy init memcached
    -> ansible-galaxy init dbiniti
    -> ansible-galaxy init update
17. this will create a well structured directory of every role the dir structure mentioned above
18. before running the playbook run these two commands becuase its important for mysql task or playbook will fail:-
    ->ansible-galaxy collection install community.mysql
    ->sudo apt install -y python3-mysqldb libmysqlclient-dev
19. thankyou
