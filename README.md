granted=False
def grant():
    granted=True
def login(username , password):
    success = False
    file=open("user_login.txt","r")
    for i in file:
        A,B=i.split(",")
        B=B.strip()
        if (A==username and B==password) :
            success = True
            break
    file.close()
    if(success):
        print("Login Successful")
        grant()
    else: 
        print("Wrong Username or Password")
def register(username, password):
    print("registered")
    file=open ("user_register.txt","a")
    file.write("\n"+username+","+password)
    file.close()
    grant()
def access(option):
    global name
    if(option=="login"):
        username=input("Enter your username:")
        password=input("Enter your password:")
        login(username,password)
    else:
        print("Enter your name and password to register")
        username=input("Enter your username:")
        password=input("Enter yourpassword:")
        register(username,password)

def begin ():
    global option
    print( "Welcome to Bank Malaysia's Online Branch!\n"
           "\t""1)login"
           "\t""2)register"
           " 3)Exit" )
    option = input("Enter your choose ").upper()
    if option != "login" and option != "register" and option!="Exit":
        begin()


begin()
access(option)
    
