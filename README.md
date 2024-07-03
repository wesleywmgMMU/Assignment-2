Here's guideline video of how to setup: https://youtu.be/x3E_F0o5G7E 

1.  In the AWS Management Console choose Services then choose EC2 and select Launch instances.

2. Setup the instance with the following setting:
  Name and tags: 
    Assignment
  Application and OS Images: 
    Ubuntu Server 24.04 LTS (HVM), SSD Volume Type
  Instance type: 
    t2.micro
  Network settings: 
    Create security group
    Allow SSH traffic from (0.0.0.0/0)

3. Fill in the name for the instance.

4. Choose the application and OS images (Amazon Machine Image).

5. Choose the instance type.

6. Ensure the network settings are default.

7. Launch the instance and proceed without the key pair.

8. Wait and refresh until the instance is ready.

9. Add port 8000 to the security group of the created instance.

10. Connect to the created instance using EC2 Instance Connect.

11. Connect to the created instance using EC2 Instance Connect.
    
13. Update the package lists in the Ubuntu system: sudo apt-get update
    
14. Clone the git repository from GitHub to the Ubuntu system: git clone https://github.com/wesleywmgMMU/Assignment-2.git
    
15. Change directory to the cloned project directory: cd Assignment-2

16. Install the Python Package Manager: sudo apt install python3-pip -y

17. Install all the Python dependencies used in the cloned project: pip3 install --break-system-packages -r requirements.txt

18. In the AWS Management Console choose Services then choose RDS and select Create database.

19. Setup the instance with the following setting:
  Engine options:
    PostgreSQL 16.3-R2
  Templates:
    Free tier
  Settings:
    Master username: myuser
    Master password: mypassword
  Connectivity:
    Public access: Yes
  Additional configuration:
    Initial database name: mydatabase

20. Create the database.

21. Wait and refresh until the database is ready.

22. Delete all ports and add port 5432 to the security group of the created database.

23. Copy the endpoint address.

24. Return back to the EC2 Instance Connect.

25. Paste the endpoint address into the settings.py in the cloned project directory: nano assignment/settings.py
  Press Ctrl+O to save
  Press Enter to confirm saving
  Press Ctrl+X to exit edit mode

26. Make migrations for the cloned project: python3 manage.py makemigrations

27. Migrate the cloned project: python3 manage.py migrate

28. Create an admin user for the cloned project: python3 manage.py createsuperuser

29. Run the server: python3 manage.py runserver 0.0.0.0:8000
