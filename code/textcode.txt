from tkinter import*
from tkinter import filedialog
from tkinter import messagebox
list=[10]
def a():
    r1=Tk()
    r1.title("text editor")
    r1.geometry('600x600')
    m=Menu(r1)
    t1=Text(r1,height=600,width=600,wrap=WORD,bd=6)
    t1.pack()
    r1.configure(menu=m)
    f=Menu(m)
    m.add_cascade(label="file",menu=f)
    e=Menu(m)
    m.add_cascade(label="edit",menu=e)
    f.add_command(label="save",command=lambda:s(t1))
    
    f.add_command(label="new",command=lambda:a())
    f.add_command(label="open",command=lambda:o(t1))
    f.add_command(label="exit",command=lambda:e1(r1))
    fo=Menu(m)
    m.add_cascade(label="font",menu=fo)
    fo.add_command(label="bold",command=lambda:bo(t1))
    fo.add_command(label="italic",command=lambda:it(t1))
    fo.add_command(label="regular",command=lambda:itb(t1))
    f4=Menu(e)
    e.add_cascade(label="color",menu=f4)
    f4.add_command(label="red",command=lambda:co(t1))
    f4.add_command(label="blue",command=lambda:bl(t1))
    f4.add_command(label="green",command=lambda:gr(t1))
    f4.add_command(label="orange",command=lambda:oa(t1))
    f5=Menu(e)
    e.add_cascade(label="font size",menu=f5)
    f5.add_command(label="+",command=lambda:ni(t1,list))
    f5.add_command(label="-",command=lambda:de(t1,list))

    
    
    
    r1.mainloop()
    
    
def s(t2):
    f=filedialog.asksaveasfile(mode="w",defaultextension=".txt")
    t3=t2.get(1.0,END)
    for l in t3:
        f.write(l)
def o(t4):
   r= filedialog.askopenfile(filetypes=[("python",".py"),("text document",".txt")])
   f=open("anuj.txt","w")
   
   for k in r:
       t4.insert(END,k)
   f.close()
                                 
        
                           
def p():
    p2=t.get(1.0,END)
    f=open("anuj.txt","w")
    for i in p2:
        f.write(i)
    f.close()
    f=open("anuj.txt","r")
    print(f.read())
    print(p2)
def e1(r2):
    l=messagebox.askquestion("EXIT","do u want to be exit ")
    print(l)
    if l=="yes":
        r2.destroy()
    
def c(t):
    h=t.selection_get()
    print(h)
    
    
    
def paste(t,r):
    print(r)
    for k in r:
        t.insert(END,k)
def bo(t):
    h=list.pop()
    t.configure(font=("bold",h))
    h=h+10
    list.append(10)
    
def it(t):
    h=list.pop()
    
    
    t.configure(font=("italic",h))
    h=h+10
    list.append(h)
    
def itb(t):
    h=list.pop()
    t.configure(font=("regular",h))
    h=h+10
    list.append(h)
    
def ni(t,list):
    h=list.pop()
    t.configure(font=("",h))
    h=h+10
    list.append(h)
def de(t,list):
    h=list.pop()
    t.configure(font=("",h))
    h=h-10
    list.append(h)
    
def co(t):
    t.configure(fg="red")
    
def bl(t):
    t.configure(fg="blue")
def gr(t):
    t.configure(fg="green")
def oa(t):
    t.configure(fg="orange")
    
r=Tk()
r.title("text editor")
r.geometry('600x500')
m=Menu(r)
r.config(menu=m)
f=Menu(m)
e=Menu(m)
s1=Scrollbar(r)
s1.pack(side=RIGHT,fill=Y)

t=Text(r,height=600,width=600,wrap=WORD,padx=20,selectbackground="red",pady=20 ,bd=6 ,yscrollcommand=s1.set)
t.pack(fill=BOTH)
s1.config(command=t.yview)



m.add_cascade(label="file",menu=f)
f.add_command(label="new",command=lambda:a())
f.add_command(label="save",command=lambda:s(t))
f.add_command(label="open",command=lambda:o(t))
m.add_cascade(label="edit",menu=e)
f.add_command(label="exit",command=lambda:e1(r))
f.add_command(label="copy",command=lambda:c(t))
f.add_command(label="paste",command=lambda:paste())
fo=Menu(m)
m.add_cascade(label="font",menu=fo)
fo.add_command(label="bold",command=lambda:bo(t))
fo.add_command(label="italic",command=lambda:it(t))
fo.add_command(label="regular",command=lambda:itb(t))
f4=Menu(e)
e.add_cascade(label="color",menu=f4)
f4.add_command(label="red",command=lambda:co(t))
f4.add_command(label="blue",command=lambda:bl(t))
f4.add_command(label="green",command=lambda:gr(t))
f4.add_command(label="orange",command=lambda:oa(t))
f5=Menu(e)
e.add_cascade(label="font size",menu=f5)
f5.add_command(label="+",command=lambda:ni(t,list))
f5.add_command(label="-",command=lambda:de(t,list))


b=Button(r,text="selct",command=p)
b.pack()
r.bind('<Control-o>',o)
t.pack()
r.mainloop()
