# -XO Game
import random
a=['-','-','-']
b=['-','-','-']
c=['-','-','-']
def insert(a,b,c,sign,num):
    if 1<=num<=3:
        a[num-1]=sign
    elif 4<=num<=6:
        b[num-4]=sign
    elif 7<=num<=9:
        c[num-7]=sign
def table(a,b,c):
    for i in [a,b,c]:
        for j in range(3):
            print(i[j],end=' ')
        print()
def winner(a,b,c):
    if a[0]==a[1]==a[2]!='-':
        return a[0]
    elif b[0]==b[1]==b[2]!='-':
        return b[0]
    elif c[0]==c[1]==c[2]!='-':
        return c[0]
    elif a[0]==b[0]==c[0]!='-':
        return a[0]
    elif a[1]==b[1]==c[1]!='-':
        return a[1]
    elif a[2]==b[2]==c[2]!='-':
        return a[2]
    elif a[0]==b[1]==c[2]!='-':
        return a[0]
    elif a[2]==b[1]==c[0]!='-':
        return a[2]
def user_input():
    sn=input("please enter your sign and number:").split()
    sign=sn[0]
    num=int(sn[1])
    return sign,num
def c_choice(remain_empty):
    c_num=random.choice(remain_empty)
    remain_empty.remove(c_num)
    return c_num
print("""Do you want to play with:
1.Friend
2.computer""")
answer=int(input("just write a number"))
if answer==1:
    i=1
    while i<=9:
        table(a,b,c)
        sign,num=user_input()
        i+=1
        insert(a,b,c,sign,num)
        if winner(a,b,c)!=None:
            print("The winner is:",winner(a,b,c))
            break
elif answer==2:
    i=1
    remain_empty=[1,2,3,4,5,6,7,8,9]
    while i<=9:
        table(a,b,c)
        user_sign,user_num=user_input()
        i+=1
        insert(a,b,c,user_sign,user_num)
        remain_empty.remove(user_num)
        if user_sign=="x":
            c_sign="o"
        elif user_sign=="o":
            c_sign="x"
        c_num=c_choice(remain_empty)
        insert(a,b,c,c_sign,c_num)
        i+=1
        if winner(a,b,c)!=None:
            print("The winner is:",winner(a,b,c))
            break
