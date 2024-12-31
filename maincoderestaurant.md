
import tkinter as tk
from tkinter import messagebox as ms
from tkinter import IntVar, Label, Radiobutton, Frame, RIDGE
from PIL import Image, ImageTk
from tkinter.ttk import Combobox
import sqlite3
from tkinter import filedialog

from tkinter import *
from tkinter import filedialog,messagebox
import random
import time


def reset():
    textReceipt.delete(1.0,END)
    e_daal.set('0')
    e_roti.set('0')
    e_sabji.set('0')
    e_fish.set('0')
    e_kebab.set('0')
    e_chawal.set('0')
    e_mutton.set('0')
    e_paneer.set('0')
    e_chicken.set('0')

    e_lassi.set('0')
    e_coffee.set('0')
    e_faluda.set('0')
    e_roohafza.set('0')
    e_shikanji.set('0')
    e_jaljeera.set('0')
    e_masalatea.set('0')
    e_badammilk.set('0')
    e_coldrinks.set('0')

    e_kitkat.set('0')
    e_oreo.set('0')
    e_apple.set('0')
    e_vanilla.set('0')
    e_banana.set('0')
    e_brownie.set('0')
    e_pineapple.set('0')
    e_chocolate.set('0')
    e_blackforest.set('0')


    textroti.config(state=DISABLED)
    textdaal.config(state=DISABLED)
    textsabji.config(state=DISABLED)
    textfish.config(state=DISABLED)
    textkebab.config(state=DISABLED)
    textpaneer.config(state=DISABLED)
    textchicken.config(state=DISABLED)
    textmutton.config(state=DISABLED)
    textchawal.config(state=DISABLED)


    textlassi.config(state=DISABLED)
    textcoffee.config(state=DISABLED)
    textjaljeera.config(state=DISABLED)
    textroohafza.config(state=DISABLED)
    textshikanji.config(state=DISABLED)
    textbadammilk.config(state=DISABLED)
    textmasalatea.config(state=DISABLED)
    textfaluda.config(state=DISABLED)
    textcolddrinks.config(state=DISABLED)



    textoreo.config(state=DISABLED)
    textapple.config(state=DISABLED)
    textkitkat.config(state=DISABLED)
    textvanilla.config(state=DISABLED)
    textbanana.config(state=DISABLED)
    textbrownie.config(state=DISABLED)
    textpineapple.config(state=DISABLED)
    textchocolate.config(state=DISABLED)
    textblackforest.config(state=DISABLED)

    var1.set(0)
    var2.set(0)
    var3.set(0)
    var4.set(0)
    var5.set(0)
    var6.set(0)
    var7.set(0)
    var8.set(0)
    var9.set(0)
    var10.set(0)
    var11.set(0)
    var12.set(0)
    var13.set(0)
    var14.set(0)
    var15.set(0)
    var16.set(0)
    var17.set(0)
    var18.set(0)
    var19.set(0)
    var20.set(0)
    var21.set(0)
    var22.set(0)
    var23.set(0)
    var24.set(0)
    var25.set(0)
    var26.set(0)
    var27.set(0)

    costofdrinksvar.set('')
    costoffoodvar.set('')
    costofcakesvar.set('')
    subtotalvar.set('')
    servicetaxvar.set('')
    totalcostvar.set('')



def save():
    if textReceipt.get(1.0,END)=='\n':
        pass
    else:
        url=filedialog.asksaveasfile(mode='w',defaultextension='.txt')
        if url==None:
            pass
        else:

            bill_data=textReceipt.get(1.0,END)
            url.write(bill_data)
            url.close()
            messagebox.showinfo('Information','Your Bill Is Succesfully Saved')

def receipt():
    global billnumber,date
    if costoffoodvar.get() != '' or costofcakesvar.get() != '' or costofdrinksvar.get() != '':
        textReceipt.delete(1.0,END)
        x=random.randint(100,10000)
        billnumber='BILL'+str(x)
        date=time.strftime('%d/%m/%Y')
        textReceipt.insert(END,'Receipt Ref:\t\t'+billnumber+'\t\t'+date+'\n')
        textReceipt.insert(END,'***************************************************************\n')
        textReceipt.insert(END,'Items:\t\t Cost Of Items(Rs)\n')
        textReceipt.insert(END,'***************************************************************\n')
        if e_roti.get()!='0':
            textReceipt.insert(END,f'Roti\t\t\t{int(e_roti.get())*10}\n\n')

        if e_daal.get()!='0':
            textReceipt.insert(END,f'Daal\t\t\t{int(e_daal.get())*60}\n\n')

        if e_fish.get()!='0':
            textReceipt.insert(END,f'Fish\t\t\t{int(e_fish.get())*100}\n\n')

        if e_chawal.get() != '0':
            textReceipt.insert(END, f'Chawal:\t\t\t{int(e_chawal.get()) * 30}\n\n')

        if e_sabji.get() != '0':
            textReceipt.insert(END, f'Sabji:\t\t\t{int(e_sabji.get()) * 50}\n\n')

        if e_paneer.get() != '0':
            textReceipt.insert(END, f'Paneer:\t\t\t{int(e_paneer.get()) * 100}\n\n')

        if e_kebab.get() != '0':
            textReceipt.insert(END, f'Kebab:\t\t\t{int(e_kebab.get()) * 40}\n\n')

        if e_chicken.get() != '0':
            textReceipt.insert(END, f'Chicken:\t\t\t{int(e_chicken.get()) * 120}\n\n')

        if e_mutton.get() != '0':
            textReceipt.insert(END, f'Mutton:\t\t\t{int(e_mutton.get()) * 120}\n\n')

        if e_lassi.get() != '0':
            textReceipt.insert(END, f'Lassi:\t\t\t{int(e_lassi.get()) * 50}\n\n')

        if e_coffee.get() != '0':
            textReceipt.insert(END, f'Coffee:\t\t\t{int(e_coffee.get()) * 40}\n\n')

        if e_faluda.get() != '0':
            textReceipt.insert(END, f'Faluda:\t\t\t{int(e_faluda.get()) * 80}\n\n')

        if e_shikanji.get() != '0':
            textReceipt.insert(END, f'Shikanji:\t\t\t{int(e_shikanji.get()) * 30}\n\n')

        if e_jaljeera.get() != '0':
            textReceipt.insert(END, f'Jaljeera:\t\t\t{int(e_jaljeera.get()) * 40}\n\n')

        if e_roohafza.get() != '0':
            textReceipt.insert(END, f'Roohafza:\t\t\t{int(e_roohafza.get()) * 60}\n\n')

        if e_masalatea.get() != '0':
            textReceipt.insert(END, f'Masala Chai:\t\t\t{int(e_masalatea.get()) * 20}\n\n')

        if e_badammilk.get() != '0':
            textReceipt.insert(END, f'Badam Milk:\t\t\t{int(e_badammilk.get()) * 50}\n\n')

        if e_coldrinks.get() != '0':
            textReceipt.insert(END, f'Cold Drinks:\t\t\t{int(e_coldrinks.get()) * 80}\n\n')

        if e_oreo.get() != '0':
            textReceipt.insert(END, f'Oreo:\t\t\t{int(e_oreo.get()) * 400}\n\n')

        if e_apple.get() != '0':
            textReceipt.insert(END, f'Apple:\t\t\t{int(e_apple.get()) * 300}\n\n')

        if e_kitkat.get() != '0':
            textReceipt.insert(END, f'Kitkat:\t\t\t{int(e_kitkat.get()) * 500}\n\n')

        if e_banana.get() != '0':
            textReceipt.insert(END, f'Banana:\t\t\t{int(e_banana.get()) * 450}\n\n')

        if e_brownie.get() != '0':
            textReceipt.insert(END, f'Brownie:\t\t\t{int(e_brownie.get()) * 800}\n\n')

        if e_pineapple.get() != '0':
            textReceipt.insert(END, f'Pineapple:\t\t\t{int(e_pineapple.get()) * 620}\n\n')

        if e_chocolate.get() != '0':
            textReceipt.insert(END, f'Chocolate:\t\t\t{int(e_chocolate.get()) * 700}\n\n')

        if e_blackforest.get() != '0':
            textReceipt.insert(END, f'Black Forest:\t\t\t{int(e_blackforest.get()) * 550}\n\n')

        if e_vanilla.get() != '0':
            textReceipt.insert(END, f'Vanilla:\t\t\t{int(e_vanilla.get()) * 550}\n\n')

        textReceipt.insert(END,'***************************************************************\n')
        if costoffoodvar.get()!='0 Rs':
            textReceipt.insert(END,f'Cost Of Food\t\t\t{priceofFood}Rs\n\n')
        if costofdrinksvar.get() != '0 Rs':
            textReceipt.insert(END,f'Cost Of Drinks\t\t\t{priceofDrinks}Rs\n\n')
        if costofcakesvar.get() != '0 Rs':
            textReceipt.insert(END,f'Cost Of Cakes\t\t\t{priceofCakes}Rs\n\n')

        textReceipt.insert(END, f'Sub Total\t\t\t{subtotalofItems}Rs\n\n')
        textReceipt.insert(END, f'Service Tax\t\t\t{50}Rs\n\n')
        textReceipt.insert(END, f'Total Cost\t\t\t{subtotalofItems+50}Rs\n\n')
        textReceipt.insert(END,'***************************************************************\n')

    else:
        messagebox.showerror('Error','No Item Is selected')



def totalcost():
    global priceofFood,priceofDrinks,priceofCakes,subtotalofItems
    if var1.get() != 0 or var2.get() != 0 or var3.get() != 0 or var4.get() != 0 or var5.get() != 0 or \
        var6.get() != 0 or var7.get() != 0 or var8.get() != 0 or var9.get() != 0 or var10.get() != 0 or\
        var11.get() != 0 or var12.get() != 0 or var13.get() != 0 or var14.get() != 0 or var15.get() != 0 or \
        var16.get() != 0 or var17.get() != 0 or var18.get() != 0 or var19.get() != 0 or var20.get() != 0 or \
        var21.get() != 0 or var22.get() != 0 or var23.get() != 0 or var24.get() != 0 or var25.get() != 0 or\
        var26.get() != 0 or var27.get() != 0:

        item1=int(e_roti.get())
        item2=int(e_daal.get())
        item3=int(e_fish.get())
        item4 = int(e_sabji.get())
        item5 = int(e_kebab.get())
        item6 = int(e_chawal.get())
        item7 = int(e_mutton.get())
        item8 = int(e_paneer.get())
        item9 = int(e_chicken.get())

        item10 = int(e_lassi.get())
        item11 = int(e_coffee.get())
        item12 = int(e_faluda.get())
        item13 = int(e_shikanji.get())
        item14 = int(e_jaljeera.get())
        item15 = int(e_roohafza.get())
        item16 = int(e_masalatea.get())
        item17 = int(e_badammilk.get())
        item18 = int(e_coldrinks.get())

        item19 = int(e_oreo.get())
        item20 = int(e_apple.get())
        item21 = int(e_kitkat.get())
        item22 = int(e_vanilla.get())
        item23 = int(e_banana.get())
        item24 = int(e_brownie.get())
        item25 = int(e_pineapple.get())
        item26 = int(e_chocolate.get())
        item27 = int(e_blackforest.get())

        priceofFood=(item1*10)+(item2*60)+(item3*100)+(item4*50)+ (item5*40) + (item6 * 30) + (item7 * 120) \
                    + (item8 * 100) + (item9 * 120)

        priceofDrinks=(item10*50)+(item11*40)+ (item12 * 80) + (item13 * 30) + (item14 * 40) + (item15 * 60) \
                      + (item16 * 20) + (item17 * 50) + (item18 * 80)

        priceofCakes=(item19*400)+(item20*300)+ (item21 * 500) + (item22 * 550) + (item23 * 450) + (item24 * 800) \
                     + (item25 * 620) + (item26 * 700) + (item27 * 550)

        costoffoodvar.set(str(priceofFood)+ ' Rs')
        costofdrinksvar.set(str(priceofDrinks)+ ' Rs')
        costofcakesvar.set(str(priceofCakes)+ ' Rs')

        subtotalofItems=priceofFood+priceofDrinks+priceofCakes
        subtotalvar.set(str(subtotalofItems)+' Rs')

        servicetaxvar.set('25 Rs')

        tottalcost=subtotalofItems+25
        totalcostvar.set(str(tottalcost)+' Rs')

    else:
        messagebox.showerror('Error','No Item Is selected')



def roti():
    if var1.get()==1:
        textroti.config(state=NORMAL)
        textroti.delete(0,END)
        textroti.focus()
    else:
        textroti.config(state=DISABLED)
        e_roti.set('0')

def daal():
    if var2.get()==1:
        textdaal.config(state=NORMAL)
        textdaal.delete(0,END)
        textdaal.focus()

    else:
        textdaal.config(state=DISABLED)
        e_daal.set('0')

def fish():
    if var3.get()==1:
        textfish.config(state=NORMAL)
        textfish.delete(0,END)
        textfish.focus()

    else:
        textfish.config(state=DISABLED)
        e_fish.set('0')

def sabji():
    if var4.get() == 1:
        textsabji.config(state=NORMAL)
        textsabji.focus()
        textsabji.delete(0, END)
    elif var4.get() == 0:
        textsabji.config(state=DISABLED)
        e_sabji.set('0')


def kebab():
    if var5.get() == 1:
        textkebab.config(state=NORMAL)
        textkebab.focus()
        textkebab.delete(0, END)
    elif var5.get() == 0:
        textkebab.config(state=DISABLED)
        e_kebab.set('0')


def chawal():
    if var6.get() == 1:
        textchawal.config(state=NORMAL)
        textchawal.focus()
        textchawal.delete(0, END)
    elif var6.get() == 0:
        textchawal.config(state=DISABLED)
        e_chawal.set('0')


def mutton():
    if var7.get() == 1:
        textmutton.config(state=NORMAL)
        textmutton.focus()
        textmutton.delete(0, END)
    elif var7.get() == 0:
        textmutton.config(state=DISABLED)
        e_mutton.set('0')


def paneer():
    if var8.get() == 1:
        textpaneer.config(state=NORMAL)
        textpaneer.focus()
        textpaneer.delete(0, END)
    elif var8.get() == 0:
        textpaneer.config(state=DISABLED)
        e_paneer.set('0')


def chicken():
    if var9.get() == 1:
        textchicken.config(state=NORMAL)
        textchicken.focus()
        textchicken.delete(0, END)
    elif var9.get() == 0:
        textchicken.config(state=DISABLED)
        e_chicken.set('0')


def lassi():
    if var10.get() == 1:
        textlassi.config(state=NORMAL)
        textlassi.focus()
        textlassi.delete(0, END)
    elif var10.get() == 0:
        textlassi.config(state=DISABLED)
        e_lassi.set('0')


def coffee():
    if var11.get() == 1:
        textcoffee.config(state=NORMAL)
        textcoffee.focus()
        textcoffee.delete(0, END)
    elif var11.get() == 0:
        textcoffee.config(state=DISABLED)
        e_coffee.set('0')


def faluda():
    if var12.get() == 1:
        textfaluda.config(state=NORMAL)
        textfaluda.focus()
        textfaluda.delete(0, END)
    elif var12.get() == 0:
        textfaluda.config(state=DISABLED)
        e_faluda.set('0')


def shikanji():
    if var13.get() == 1:
        textshikanji.config(state=NORMAL)
        textshikanji.focus()
        textshikanji.delete(0, END)
    elif var13.get() == 0:
        textshikanji.config(state=DISABLED)
        e_shikanji.set('0')


def jaljeera():
    if var14.get() == 1:
        textjaljeera.config(state=NORMAL)
        textjaljeera.focus()
        textjaljeera.delete(0, END)
    elif var14.get() == 0:
        textjaljeera.config(state=DISABLED)
        e_jaljeera.set('0')


def roohafza():
    if var15.get() == 1:
        textroohafza.config(state=NORMAL)
        textroohafza.focus()
        textroohafza.delete(0, END)
    elif var15.get() == 0:
        textroohafza.config(state=DISABLED)
        e_roohafza.set('0')


def masalatea():
    if var16.get() == 1:
        textmasalatea.config(state=NORMAL)
        textmasalatea.focus()
        textmasalatea.delete(0, END)
    elif var16.get() == 0:
        textmasalatea.config(state=DISABLED)
        e_masalatea.set('0')


def badammilk():
    if var17.get() == 1:
        textbadammilk.config(state=NORMAL)
        textbadammilk.focus()
        textbadammilk.delete(0, END)
    elif var17.get() == 0:
        textbadammilk.config(state=DISABLED)
        e_badammilk.set('0')


def colddrinks():
    if var18.get() == 1:
        textcolddrinks.config(state=NORMAL)
        textcolddrinks.focus()
        textcolddrinks.delete(0, END)
    elif var18.get() == 0:
        textcolddrinks.config(state=DISABLED)
        e_coldrinks.set('0')


def oreo():
    if var19.get() == 1:
        textoreo.config(state=NORMAL)
        textoreo.focus()
        textoreo.delete(0, END)
    elif var19.get() == 0:
        textoreo.config(state=DISABLED)
        e_oreo.set('0')


def apple():
    if var20.get() == 1:
        textapple.config(state=NORMAL)
        textapple.focus()
        textapple.delete(0, END)
    elif var20.get() == 0:
        textapple.config(state=DISABLED)
        e_apple.set('0')


def kitkat():
    if var21.get() == 1:
        textkitkat.config(state=NORMAL)
        textkitkat.focus()
        textkitkat.delete(0, END)
    elif var21.get() == 0:
        textkitkat.config(state=DISABLED)
        e_kitkat.set('0')


def vanilla():
    if var22.get() == 1:
        textvanilla.config(state=NORMAL)
        textvanilla.focus()
        textvanilla.delete(0, END)
    elif var22.get() == 0:
        textvanilla.config(state=DISABLED)
        e_vanilla.set('0')


def banana():
    if var23.get() == 1:
        textbanana.config(state=NORMAL)
        textbanana.focus()
        textbanana.delete(0, END)
    elif var23.get() == 0:
        textbanana.config(state=DISABLED)
        e_banana.set('0')


def brownie():
    if var24.get() == 1:
        textbrownie.config(state=NORMAL)
        textbrownie.focus()
        textbrownie.delete(0, END)
    elif var24.get() == 0:
        textbrownie.config(state=DISABLED)
        e_brownie.set('0')


def pineapple():
    if var25.get() == 1:
        textpineapple.config(state=NORMAL)
        textpineapple.focus()
        textpineapple.delete(0, END)
    elif var25.get() == 0:
        textpineapple.config(state=DISABLED)
        e_pineapple.set('0')


def chocolate():
    if var26.get() == 1:
        textchocolate.config(state=NORMAL)
        textchocolate.focus()
        textchocolate.delete(0, END)
    elif var26.get() == 0:
        textchocolate.config(state=DISABLED)
        e_chocolate.set('0')


def blackforest():
    if var27.get() == 1:
        textblackforest.config(state=NORMAL)
        textblackforest.focus()
        textblackforest.delete(0, END)
    elif var27.get() == 0:
        textblackforest.config(state=DISABLED)
        e_blackforest.set('0')





##########################################################################################################

root = tk.Tk()
#root.geometry('1250x700+210+100')
root.geometry('1270x690+0+0')
#root.resizable(0, 0)
root.title('Restaurant Management System created by Akshay')
root.config(bg='white')


topFrame = Frame(root, bd=10, relief=RIDGE, bg='purple')
topFrame.pack(side=tk.TOP)




labelTitle = Label(topFrame,text='Welcome To Indian Restaurant',font=('arial', 30, 'bold'),fg='black',bd=9,bg='orange red',width=60)
labelTitle.grid(row=0, column=0)


var1=IntVar()
var2=IntVar()
var3=IntVar()
var4=IntVar()
var5 = IntVar()
var6 = IntVar()
var7 = IntVar()
var8 = IntVar()
var9 = IntVar()
var10 = IntVar()
var11 = IntVar()
var12 = IntVar()
var13 = IntVar()
var14 = IntVar()
var15 = IntVar()
var16 = IntVar()
var17 = IntVar()
var18 = IntVar()
var19 = IntVar()
var20 = IntVar()
var21 = IntVar()
var22 = IntVar()
var23 = IntVar()
var24 = IntVar()
var25 = IntVar()
var26 = IntVar()
var27 = IntVar()

e_roti=StringVar()
e_daal=StringVar()
e_sabji = StringVar()
e_chawal = StringVar()
e_fish = StringVar()
e_mutton = StringVar()
e_kebab = StringVar()
e_chicken = StringVar()
e_paneer = StringVar()

e_lassi=StringVar()
e_coffee = StringVar()
e_faluda = StringVar()
e_shikanji = StringVar()
e_roohafza = StringVar()
e_jaljeera = StringVar()
e_masalatea = StringVar()
e_badammilk = StringVar()
e_coldrinks = StringVar()

e_oreo=StringVar()
e_kitkat = StringVar()
e_vanilla = StringVar()
e_apple = StringVar()
e_blackforest = StringVar()
e_banana = StringVar()
e_brownie = StringVar()
e_pineapple = StringVar()
e_chocolate = StringVar()

costoffoodvar=StringVar()
costofdrinksvar=StringVar()
costofcakesvar=StringVar()
subtotalvar=StringVar()
servicetaxvar=StringVar()
totalcostvar=StringVar()

e_roti.set('0')
e_daal.set('0')
e_sabji.set('0')
e_fish.set('0')
e_kebab.set('0')
e_chawal.set('0')
e_mutton.set('0')
e_chicken.set('0')
e_paneer.set('0')

e_lassi.set('0')
e_coffee.set('0')
e_faluda.set('0')
e_roohafza.set('0')
e_shikanji.set('0')
e_jaljeera.set('0')
e_masalatea.set('0')
e_badammilk.set('0')
e_coldrinks.set('0')

e_kitkat.set('0')
e_banana.set('0')
e_pineapple.set('0')
e_apple.set('0')
e_chocolate.set('0')
e_oreo.set('0')
e_blackforest.set('0')
e_brownie.set('0')
e_vanilla.set('0')

#####################################################
#####Food

frame1 = tk.LabelFrame(root, text='Food Menu', width=300, height=490, bd=4, font=('Arial', 14, 'bold'), bg="pink", fg="black", labelanchor='n')
frame1.place(x=40, y=110)
var1 = tk.IntVar()
var2= tk.IntVar()
var3 = tk.IntVar()
var4 = tk.IntVar()
var5 = tk.IntVar()
var6 = tk.IntVar()
var7 = tk.IntVar()
var8 = tk.IntVar()
var9 = tk.IntVar()



##FOOD
price_item = Label(frame1, text="Food", font=('arial', 18, 'bold'), bg='pink')
price_item.grid(row=0, column=0, sticky=W)
price_quntity = Label(frame1, text="Quntity", font=('arial', 18, 'bold'), bg='pink')
price_quntity.grid(row=0, column=1, sticky=W)
price_price = Label(frame1, text="Price", font=('arial', 18, 'bold'), bg='pink')
price_price.grid(row=0, column=2, sticky=W)


roti=Checkbutton(frame1,text='Roti',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var1,bg='pink',command=roti)
roti.grid(row=1,column=0,sticky=W)
price_roti = Label(frame1, text="₹10/-", font=('arial', 18, 'bold'), bg='pink')
price_roti.grid(row=1, column=2, sticky=W)



daal=Checkbutton(frame1,text='Daal',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var2,bg='pink',command=daal)
daal.grid(row=2,column=0,sticky=W)
price_daal = Label(frame1, text="₹60/-", font=('arial', 18, 'bold'), bg='pink')
price_daal.grid(row=2, column=2, sticky=W)



fish=Checkbutton(frame1,text='Fish',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var3,bg='pink',command=fish)
fish.grid(row=3,column=0,sticky=W)
price_fish = Label(frame1, text="₹100/-", font=('arial', 18, 'bold'), bg='pink')
price_fish.grid(row=3, column=2, sticky=W)



sabji=Checkbutton(frame1,text='Sabji',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var4,bg='pink',command=sabji)
sabji.grid(row=4,column=0,sticky=W)
price_sabji = Label(frame1, text="₹50/-", font=('arial', 18, 'bold'), bg='pink')
price_sabji.grid(row=4, column=2, sticky=W)



kebab=Checkbutton(frame1,text='kebab',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var5,bg='pink',command=kebab)
kebab.grid(row=5,column=0,sticky=W)
price_kebab = Label(frame1, text="₹40/-", font=('arial', 18, 'bold'), bg='pink')
price_kebab.grid(row=5, column=2, sticky=W)


chawal=Checkbutton(frame1,text='Chawal',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var6,bg='pink',command=chawal)
chawal.grid(row=6,column=0,sticky=W)
price_chawal = Label(frame1, text="₹30/-", font=('arial', 18, 'bold'), bg='pink')
price_chawal.grid(row=6, column=2, sticky=W)



mutton=Checkbutton(frame1,text='Mutton',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var7,bg='pink',command=mutton)
mutton.grid(row=7,column=0,sticky=W)
price_mutton = Label(frame1, text="₹120/-", font=('arial', 18, 'bold'), bg='pink')
price_mutton.grid(row=7, column=2, sticky=W)


paneer=Checkbutton(frame1,text='Paneer',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var8,bg='pink',command=paneer)
paneer.grid(row=8,column=0,sticky=W)
price_paneer = Label(frame1, text="₹100/-", font=('arial', 18, 'bold'), bg='pink')
price_paneer.grid(row=8, column=2, sticky=W)


chicken=Checkbutton(frame1,text='Chicken Handi',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var9,bg='pink',command=chicken)
chicken.grid(row=9,column=0,sticky=W)
price_chicken = Label(frame1, text="₹120/-", font=('arial', 18, 'bold'), bg='pink')
price_chicken.grid(row=9, column=2, sticky=W)


# #Entry  Food Items

textroti=Entry(frame1,font=('arial',18,'bold'),bd=7,width=6,state=DISABLED,textvariable=e_roti)
textroti.grid(row=1,column=1)

textdaal=Entry(frame1,font=('arial',18,'bold'),bd=7,width=6,state=DISABLED,textvariable=e_daal)
textdaal.grid(row=2,column=1)

textfish=Entry(frame1,font=('arial',18,'bold'),bd=7,width=6,state=DISABLED,textvariable=e_fish)
textfish.grid(row=3,column=1)

textsabji = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_sabji)
textsabji.grid(row=4, column=1)

textkebab = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_kebab)
textkebab.grid(row=5, column=1)

textchawal = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_chawal)
textchawal.grid(row=6, column=1)

textmutton = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_mutton)
textmutton.grid(row=7, column=1)

textpaneer = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_paneer)
textpaneer.grid(row=8, column=1)

textchicken = Entry(frame1, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_chicken)
textchicken.grid(row=9, column=1)


##########################################

############Drink

frame2 = tk.LabelFrame(root, text='Drinks Menu', width=300, height=490, bd=4, font=('Arial', 14, 'bold'), bg="pink", fg="black", labelanchor='n')
frame2.place(x=450, y=110)

var10 = tk.IntVar()
var11 = tk.IntVar()
var12 = tk.IntVar()
var13 = tk.IntVar()
var14 = tk.IntVar()
var15 = tk.IntVar()
var16 = tk.IntVar()
var17 = tk.IntVar()
var18 = tk.IntVar()




price_item = Label(frame2, text="Drinks", font=('arial', 18, 'bold'), bg='pink')
price_item.grid(row=0, column=0, sticky=W)
price_quntity = Label(frame2, text="Quntity", font=('arial', 18, 'bold'), bg='pink')
price_quntity.grid(row=0, column=1, sticky=W)
price_price = Label(frame2, text="Price", font=('arial', 18, 'bold'), bg='pink')
price_price.grid(row=0, column=2, sticky=W)



lassi=Checkbutton(frame2,text='Lassi',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var10,bg='pink',command=lassi)
lassi.grid(row=1,column=0,sticky=W)
price_lassi = Label(frame2, text="₹50/-", font=('arial', 18, 'bold'), bg='pink')
price_lassi.grid(row=1, column=2, sticky=W)


coffee=Checkbutton(frame2,text='Coffee',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var11,bg='pink',command=coffee)
coffee.grid(row=2,column=0,sticky=W)
price_coffee = Label(frame2, text="₹40/-", font=('arial', 18, 'bold'), bg='pink')
price_coffee.grid(row=2, column=2, sticky=W)


faluda=Checkbutton(frame2,text='Faluda',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var12,bg='pink',command=faluda)
faluda.grid(row=3,column=0,sticky=W)
price_faluda = Label(frame2, text="₹80/-", font=('arial', 18, 'bold'), bg='pink')
price_faluda.grid(row=3, column=2, sticky=W)


shikanji=Checkbutton(frame2,text='Shikanji',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var13,bg='pink',command=shikanji)
shikanji.grid(row=4,column=0,sticky=W)
price_shikanji = Label(frame2, text="₹30/-", font=('arial', 18, 'bold'), bg='pink')
price_shikanji.grid(row=4, column=2, sticky=W)


jaljeera=Checkbutton(frame2,text='Jaljeera',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var14,bg='pink',command=jaljeera)
jaljeera.grid(row=5,column=0,sticky=W)
price_jaljeera = Label(frame2, text="₹40/-", font=('arial', 18, 'bold'), bg='pink')
price_jaljeera.grid(row=5, column=2, sticky=W)


roohafza=Checkbutton(frame2,text='Roohafza',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var15,bg='pink',command=roohafza)
roohafza.grid(row=6,column=0,sticky=W)
price_roohafza = Label(frame2, text="₹60/-", font=('arial', 18, 'bold'), bg='pink')
price_roohafza.grid(row=6, column=2, sticky=W)



masalatea=Checkbutton(frame2,text='Masala Tea',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var16,bg='pink',command=masalatea)
masalatea.grid(row=7,column=0,sticky=W)
price_masalatea = Label(frame2, text="₹20/-", font=('arial', 18, 'bold'), bg='pink')
price_masalatea.grid(row=7, column=2, sticky=W)



badammilk=Checkbutton(frame2,text='Badam Milk',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var17,bg='pink',command=badammilk)
badammilk.grid(row=8,column=0,sticky=W)
price_badammilk = Label(frame2, text="₹50/-", font=('arial', 18, 'bold'), bg='pink')
price_badammilk.grid(row=8, column=2, sticky=W)


colddrinks=Checkbutton(frame2,text='Cold Drinks',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var18,bg='pink',command=colddrinks)
colddrinks.grid(row=9,column=0,sticky=W)
price_colddrinks = Label(frame2, text="₹80/-", font=('arial', 18, 'bold'), bg='pink')
price_colddrinks.grid(row=9, column=2, sticky=W)


#entry drink items

textlassi = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_lassi)
textlassi.grid(row=1, column=1)

textcoffee = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_coffee)
textcoffee.grid(row=2, column=1)

textfaluda = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_faluda)
textfaluda.grid(row=3, column=1)

textshikanji = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_shikanji)
textshikanji.grid(row=4, column=1)

textjaljeera = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_jaljeera)
textjaljeera.grid(row=5, column=1)

textroohafza = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_roohafza)
textroohafza.grid(row=6, column=1)

textmasalatea = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_masalatea)
textmasalatea.grid(row=7, column=1)

textbadammilk = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_badammilk)
textbadammilk.grid(row=8, column=1)

textcolddrinks = Entry(frame2, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_coldrinks)
textcolddrinks.grid(row=9, column=1)





#############################+++++++++++++++++++++++++++++++++++++++++++++++++
##cakes
frame3 = tk.LabelFrame(root, text='Cake Menu', width=300, height=490, bd=6, font=('Arial', 14, 'bold'), bg="pink", fg="black", labelanchor='n')
frame3.place(x=820, y=110)


var19 = tk.IntVar()
var20 = tk.IntVar()
var21 = tk.IntVar()
var22 = tk.IntVar()
var23 = tk.IntVar()
var24 = tk.IntVar()
var25 = tk.IntVar()
var26 = tk.IntVar()
var27 = tk.IntVar()

price_item = Label(frame3, text="Cakes", font=('arial', 18, 'bold'), bg='pink')
price_item.grid(row=0, column=0, sticky=W)
price_quantity = Label(frame3, text="Quantity", font=('arial', 18, 'bold'), bg='pink')
price_quantity.grid(row=0, column=1, sticky=W)
price_price = Label(frame3, text="Price", font=('arial', 18, 'bold'), bg='pink')
price_price.grid(row=0, column=2, sticky=W)

#Cakes

oreocake=Checkbutton(frame3,text='Oreo',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var19,bg='pink',command=oreo) 
oreocake.grid(row=1,column=0,sticky=W)
price_oreocake = Label(frame3, text="₹400/-", font=('arial', 18, 'bold'), bg='pink')
price_oreocake.grid(row=1, column=2, sticky=W)


applecake=Checkbutton(frame3,text='Apple',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var20,bg='pink',command=apple)
applecake.grid(row=2,column=0,sticky=W)
price_applecake = Label(frame3, text="₹300/-", font=('arial', 18, 'bold'), bg='pink')
price_applecake.grid(row=2, column=2, sticky=W)


kitkatcake=Checkbutton(frame3,text='Kitkat',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var21,bg='pink',command=kitkat)
kitkatcake.grid(row=3,column=0,sticky=W)
price_kitkatcake = Label(frame3, text="₹500/-", font=('arial', 18, 'bold'), bg='pink')
price_kitkatcake.grid(row=3, column=2, sticky=W)


vanillacake=Checkbutton(frame3,text='Vanilla',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var22,bg='pink',command=vanilla)
vanillacake.grid(row=4,column=0,sticky=W)
price_vanillacak = Label(frame3, text="₹550/-", font=('arial', 18, 'bold'), bg='pink')
price_vanillacak.grid(row=4, column=2, sticky=W)


bananacake=Checkbutton(frame3,text='Banana',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var23,bg='pink',command=banana)
bananacake.grid(row=5,column=0,sticky=W)
price_bananacake = Label(frame3, text="₹450/-", font=('arial', 18, 'bold'), bg='pink')
price_bananacake.grid(row=5, column=2, sticky=W)


browniecake=Checkbutton(frame3,text='Brownie',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var24,bg='pink',command=brownie)
browniecake.grid(row=6,column=0,sticky=W)
price_browniecake = Label(frame3, text="₹800/-", font=('arial', 18, 'bold'), bg='pink')
price_browniecake.grid(row=6, column=2, sticky=W)


pineapplecake=Checkbutton(frame3,text='Pineapple',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var25,bg='pink',command=pineapple)
pineapplecake.grid(row=7,column=0,sticky=W)
price_pineapplecake = Label(frame3, text="₹620/-", font=('arial', 18, 'bold'), bg='pink')
price_pineapplecake.grid(row=7, column=2, sticky=W)


chocolatecake=Checkbutton(frame3,text='Chocolate',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var26,bg='pink',command=chocolate)
chocolatecake.grid(row=8,column=0,sticky=W)
price_chocolatecake = Label(frame3, text="₹700/-", font=('arial', 18, 'bold'), bg='pink')
price_chocolatecake.grid(row=8, column=2, sticky=W)


blackforestcake=Checkbutton(frame3,text='Black Forest',font=('arial',18,'bold'),onvalue=1,offvalue=0,variable=var27,bg='pink',command=blackforest)
blackforestcake.grid(row=9,column=0,sticky=W)
price_blackforestcake = Label(frame3, text="₹550/-", font=('arial', 18, 'bold'), bg='pink')
price_blackforestcake.grid(row=9, column=2, sticky=W)



##entry cake
textoreo = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_oreo)
textoreo.grid(row=1, column=1)

textapple = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_apple)
textapple.grid(row=2, column=1)

textkitkat = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_kitkat)
textkitkat.grid(row=3, column=1)

textvanilla = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_vanilla)
textvanilla.grid(row=4, column=1)

textbanana = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_banana)
textbanana.grid(row=5, column=1)

textbrownie = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_brownie)
textbrownie.grid(row=6, column=1)

textpineapple = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_pineapple)
textpineapple.grid(row=7, column=1)

textchocolate = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_chocolate)
textchocolate.grid(row=8, column=1)

textblackforest = Entry(frame3, font=('arial', 18, 'bold'), bd=7, width=6, state=DISABLED,textvariable=e_blackforest)
textblackforest.grid(row=9, column=1)

######################################++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
##Billing menue
frame4 = tk.LabelFrame(root, text='', width=940, height=150, bd=4, font=('time', 14, 'bold'), bg="firebrick4")
frame4.place(x=100, y=650)


labelCostofFood=Label(frame4,text='Cost Of Food',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofFood.place(x=10,y=10)

textCostofFood=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=costoffoodvar)
textCostofFood.place(x=200,y=10)

labelCostofdrink=Label(frame4,text='Cost Of Drinsk',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofdrink.place(x=10,y=60)

textCostofdrink=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=costofdrinksvar)
textCostofdrink.place(x=200,y=60)

labelCostofcake=Label(frame4,text='Cost Of Cake',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofcake.place(x=10,y=110)

textCostofcake=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=costofcakesvar)
textCostofcake.place(x=200,y=110)


labelCostofFood=Label(frame4,text='Sub Total',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofFood.place(x=500,y=10)

textCostofsub=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=subtotalvar)
textCostofsub.place(x=680,y=10)

labelCostofFood=Label(frame4,text='Service Tax',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofFood.place(x=500,y=60)

textCostofsub=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=servicetaxvar)
textCostofsub.place(x=680,y=60)


labelCostofFood=Label(frame4,text='Total Cost',font=('arial',16,'bold'),bg='firebrick4',fg='white')
labelCostofFood.place(x=500,y=110)

textCostofsub=tk.Entry(frame4,font=('arial',16,'bold'),bd=2,width=10,state='readonly',textvariable=totalcostvar)
textCostofsub.place(x=680,y=110)
###########################################################################
##Buttons
frame5 = tk.LabelFrame(root, text='Receip', width=390, height=590, bd=4, font=('Arial', 14, 'bold'), bg="azure", fg="black", labelanchor='n')
frame5.place(x=1200, y=105)

textReceipt = Text(frame5, font=('arial', 12, 'bold'), bd=5, width=39, height=15)
textReceipt.place(x=10,y=100)

buttonTotal=tk.Button(frame5,text='Total',font=('arial',14,'bold'),fg='white',bg='red4',bd=3,padx=5,command=totalcost)
buttonTotal.place(x=10,y=450)

buttonReceipt=tk.Button(frame5,text='Receipt',font=('arial',14,'bold'),fg='white',bg='red4',bd=3,padx=5,command=receipt)
buttonReceipt.place(x=100,y=450)

buttonSave=tk.Button(frame5,text='Save',font=('arial',14,'bold'),fg='white',bg='red4',bd=3,padx=5,command=save)
buttonSave.place(x=210,y=450)

buttonReset=tk.Button(frame5,text='Reset',font=('arial',14,'bold'),fg='white',bg='red4',bd=3,padx=5,command=reset)
buttonReset.place(x=300,y=450)

#########################################################
root.mainloop()
