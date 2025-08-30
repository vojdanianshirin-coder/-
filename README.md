import random
def slot_machine():
    x=["apple" , "grapes" , "banana" , "orange"]
    a=random.choice(x)
    b=random.choice(x)
    c=random.choice(x)
    print(a,b,c)
    if a==b==c:
        print("jackpot")
slot_machine()
while True:
    y=input("do you want to continiuo")
    if y.lower()=='yes':
        slot_machine()
    else:
        break
