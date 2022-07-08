# _pickle.UnpicklingError-invalid-load-key-x00-.
#Problem in Updating a Binary File Data in Python

import pickle as p
with open("employee5.dat", "wb") as f:
    emp1 = {"Empno":1201,"Name":"Vijay1","Age":32}
    emp2 = {"Empno":1202,"Name":"Vijay2","Age":32}
    emp3 = {"Empno":1203,"Name":"Vijay3","Age":32}
    emp4 = {"Empno":1204,"Name":"Vijay4","Age":32}
    emp5 = {"Empno":1205,"Name":"Vijay5","Age":32}
    p.dump(emp1, f)
    p.dump(emp2, f)
    p.dump(emp3, f)
    p.dump(emp4, f)
    p.dump(emp5, f)
    
 emp = {}
f = open("employee5.dat", "rb+")

try:
    while True:
        pos = f.tell()
        print("File pointer position : ", pos)        
        emp = p.load(f)
        if emp["Empno"] == 1204:
            emp["Name"] = "New Vijay4"
            f.seek(pos)
            p.dump(emp, f)
            break    
except EOFError:
    f.close()
