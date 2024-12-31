import tkinter as tk
from tkinter import *
from tkinter import filedialog, messagebox as ms
import sqlite3
from tkinter import ttk
from PIL import Image, ImageTk
from tkinter.ttk import Combobox
import re
# root = Tk()
# root.geometry("1200x600")
# root.title("Restaurant Management System")


# w, h = root.winfo_screenwidth(), root.winfo_screenheight()
# image2 = Image.open('C:/Users/Akshay/Desktop/python/restaurant/restaurant (2).jpg')
# image2 = image2.resize((w, h), Image.LANCZOS)
# background_image = ImageTk.PhotoImage(image2)
# background_label = Label(root, image=background_image)
# background_label.place(x=0, y=0, relwidth=1, relheight=1)

root = tk.Tk()
root.geometry('1270x690+0+0')
root.title('Restaurant Management System created by Akshay')
root.config(bg='white')
bg_image = Image.open('C:/Users/Akshay/Downloads/restaurant (2).jpg')  
bg_image = bg_image.resize((1540, 790), Image.LANCZOS) 
bg_photo = ImageTk.PhotoImage(bg_image)
bg_label = tk.Label(root, image=bg_photo)
bg_label.place(x=0, y=0, relwidth=1, relheight=1)  
topFrame = Frame(root, bd=10, relief=RIDGE, bg='purple')
topFrame.pack(side=tk.TOP)
topFrame.lift()  


def action():
    from subprocess import call
    call(["python", "mainpagerestaurant.py"])


def window():
    root.destroy()

button3 = tk.Button(root, text="View Menu", command=action, width=10, height=1, bg="black", fg="pink",
                    font=('times', 20, 'bold'))
button3.place(x=1200, y=700)




root.mainloop()


