# scaling-san-umbrella
print("\t\t\t\t\t\t Welcome to locobus")
A=['name','age','gender','password','passengerid','status']
m=100;t=50;T=50
z=[];B=[];price=1000
cid="123";cpwd="123"
while True:
    print("1.Passenger\n2.Cashier\n3.Exit")
    n=int(input("CHOOSE ANY ONE:"))
    if n==1:        
        while True:
            print("1.Signup\n2.Login\n3.Goback")
            a=int(input("CHOOSE ANY ONE:"))
            x=[]
            if a==1:            
                name=input("Enter your name:")
                age=int(input("Enter your age:"))
                while True:
                    n=input("Enter your gender:")
                    gender=n.casefold()
                    if gender in ("male","female","others"):
                        break
                    else:
                        print("Invalid Gender")
                password=input("Enter your password:")
                x.append(name)
                x.append(age)
                n=(name[0]+gender[0]+str(m))
                newid=n.upper()
                x.append(gender)
                x.append(password)
                x.append(newid)
                status="no tickets booked"
                x.append(status)
                print("Sign up Successfully;)")
                print("Your ID is:",newid)
                B.append(dict(zip(A,x)))
                m+=1
            elif a==2:      
                pid=input("Enter passenger ID:")
                pwd=input("Enter password:")
                f=False
                for i in range(len(B)):
                    if B[i]["passengerid"]==pid and B[i]["password"]==pwd:
                        print("login successful")
                        f = True
                        if f==True:
                            print("1.Book tickets\n2.Check booking status\n3.Goback")
                            e=int(input("Enter your choice:"))
                            if e==1:
                                print("price per ticket:",price)
                                if B[i]['status']==True:
                                    t=t-B[i]['tickets']
                                print("No.of available seats:",t)
                                k=int(input("No.of Tickets you want to book?:"))
                                B[i]['tickets']=k
                                B[i]['status']=False
                                print("Your booking is in pending list...")
                            elif e==2:
                                if B[i]['status']==True:
                                    print("Your ticket is approved")
                                elif B[i]['status']=="no tickets booked":
                                    print("No tickets booked")
                                else:
                                    print("Your ticket is in still pending list...")
                            elif e==3:
                                break
                        break
                else:
                    print("Invalid Id or Password")
            elif a==3:
                break
        else:
            print("Invalid")
    elif n==2:      
        a=input("Enter €ashier Id:")
        b=input("Enter €ashier password:")
        if a==cid and b==cpwd:
            print("login successful")
            while True:
                print("1.Approve ticket\n2.Cancel ticket\n3.logout")
                n=int(input("Enter your choice:"))
                if n==1:
                    for i in range (len(B)):
                        if B[i]['status']==False:
                            for j,k in B[i].items():
                                if j != 'password':
                                    print(j,":",k,end=" ")
                            print('\n')
                    a=input("Enter passenger Id to approve:")
                    f=True
                    for i in range(len(B)):
                        if a==B[i]['passengerid']:
                            f=False
                            if B[i]['tickets']!=0:
                                B[i]['status']=True
                                print("ticket approved")
                                break
                            else:
                                print("No tickets booked")
                    if f:
                        print("Invalid passenger Id")
                elif n==2:
                    for i in range (len(B)):
                        if B[i]['status']==False:
                            for j,k in B[i].items():
                                if j != 'password':
                                    print(j,":",k,end=" ")
                            print('\n')
                    a=input("Enter passenger Id to cancel ticket:")
                    f=True
                    for i in range (len(B)):
                        if a==B[i]['passengerid']:
                            f=False
                            if B[i]['tickets']!=0:
                                a= B[i]['tickets']
                                B[i]['tickets']=0
                                B[i]['status'] = "no tickets booked"
                                print("Ticket cancelled successfully")
                                break
                            else:
                                print("No tickets booked")
                    if f:
                        print("Invalid passenger Id")
                elif n==3:
                    break
            else:
                print("Invalid")
        else:
            print("Wrong Id or Password")
    elif n==3:
        break
    else:
        print("Invalid Entry")






