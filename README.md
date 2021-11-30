# GUI-Project
GUI progress
import tkinter as tk
from tkinter import scrolledtext
import tkinter

mainwindow = tk.Tk()
mainwindow.title("Multi-window demo code - 3")
mainwindow.geometry("600x500")

mainwindow.columnconfigure(0, weight=1)
mainwindow.rowconfigure(1, weight=1)

def showRed():
    redFrame.tkraise()

def showGreen():
    greenFrame.tkraise()

def showBlue():
    blueFrame.tkraise()


# Parent widget for the buttons
top_frame = tk.Frame(mainwindow, bg="cyan", highlightbackground="black", highlightthickness=1)

top_frame.grid(row=0, column=0, columnspan=3, sticky=tk.N+tk.W+tk.E)

btn_r1 = tk.Button(top_frame, text='red', width='5', command=showRed)
btn_r1.grid(row=0, column=0, padx=(10), pady=10)

btn_g1 = tk.Button(top_frame, text='green', width='5', command=showGreen)
btn_g1.grid(row=0, column=1, padx=(10), pady=10)

btn_b1 = tk.Button(top_frame, text='blue', width='5', command=showBlue)
btn_b1.grid(row=0, column=2, padx=(10), pady=10)

# bottom Frame ----------------------------------------------------
bottom_frame = tk.Frame(mainwindow, bg="yellow", padx=5, pady=5)
bottom_frame.grid_propagate(False)
bottom_frame.grid(row=1, column=0, padx=10, pady=10, sticky=(tk.NSEW))

bottom_frame.columnconfigure(0, weight=1)
bottom_frame.rowconfigure(0, weight=1)

# 4th Frame -------------------------------------------------------


# red Frame ----------------------------------------------------

redFrame = tk.Frame(bottom_frame, bg="red", padx=5, pady=5)
redFrame.place(x=0, y=0, relwidth=1.0, relheight=1.0)


butt1 = False
butt2 = False

def func_one():
    label_1.configure(text = "you pushed the button 1")
    global butt1
    butt1 = True

def func_two():
    other_label.configure(text = "that was button 2")
    other_label.configure(foreground="blue", background="yellow")
    global butt2
    butt2 = True

def do_reset():
    global butt1
    global butt2
    if(butt1 == True and butt2 == True):
        label_1.configure(text = "I'm reset")
        other_label.configure(text = "Also reset")
        butt1 = False
        butt2 = False

label_1 = tkinter.Label(redFrame, text="A Label")
label_1.pack()

other_label = tkinter.Label(redFrame, text="Label B - other")
other_label.pack()                          

button_1 = tkinter.Button(redFrame, text="Button ONE", command=func_one)
button_1.pack()

two_button = tkinter.Button(redFrame, text="Button TWO", command=func_two)
two_button.pack()

resetButt = tkinter.Button(redFrame, text="do the reset", command=do_reset)
resetButt.pack()


btn_b2 = tk.Button(redFrame, fg="blue", text='blue', width='5', command=showBlue)
btn_b2.place(x=0, y=0)

btn_g2 = tk.Button(redFrame, fg="green", text='green', width='5', command=showGreen)
btn_g2.place(relx=1.0, y=0, anchor=(tk.NE))

# green Frame ----------------------------------------------------
greenFrame = tk.Frame(bottom_frame, bg="green", padx=5, pady=5)
greenFrame.place(x=0, y=0, relwidth=1.0, relheight=1.0)


def func_three():
    str_var1 = E1.get()
    if str_var1 == 'blue':
        greenFrame.config(bg='blue')
    if str_var1 == 'red':
        greenFrame.config(bg='red')
    if str_var1 == '':
        str_var1="Empty-reset"
        greenFrame.config(bg='gray95')
    L2.configure(text=str_var1)

L1 = tk.Label(greenFrame, text = "Enter string or color")
L1.pack()

E1 = tk.Entry(greenFrame)
E1.pack()

B1 = tk.Button(greenFrame, text="post the entry", command=func_three)
B1.pack()

L2 = tk.Label(greenFrame, text = "---------------")
L2.pack()



btn_r3 = tk.Button(greenFrame, fg="red", text='red', width='5', command=showRed)
btn_r3.place(x=0, y=0)

btn_b3 = tk.Button(greenFrame, fg="blue", text='blue', width='5', command=showBlue)
btn_b3.place(relx=1.0, y=0, anchor=(tk.NE))

# blue Frame ----------------------------------------------------
blueFrame = tk.Frame(bottom_frame, bg="blue", padx=5, pady=5)
blueFrame.place(x=0, y=0, relwidth=1.0, relheight=1.0)

my_tkVar = tk.IntVar()
my_tkVar.set(2)


def doButt():
    temp_var = my_tkVar.get()
    L3.configure(text=temp_var)

L3 = tk.Label(blueFrame, text="selection", font=('arial', 20))
L3.pack()

my_radio_1 = tk.Radiobutton(blueFrame)
my_radio_1.config(text="Radiobutton 1", variable=my_tkVar, value=1)

my_radio_2 = tk.Radiobutton(blueFrame)
my_radio_2.config(text="Radiobutton 2", variable=my_tkVar, value=2)

my_radio_3 = tk.Radiobutton(blueFrame)
my_radio_3.config(text="Radiobutton 3", variable=my_tkVar, value=3)

my_radio_1.pack()
my_radio_2.pack()
my_radio_3.pack()

L4 = tk.Label(blueFrame, text="---------------------------")
L4.pack()

B2 = tk.Button(blueFrame, text="push", command=doButt)
B2.pack()


btn_g4 = tk.Button(blueFrame, fg="green", text='green', width='5', command=showGreen)
btn_g4.place(x=0, y=0)

btn_r4 = tk.Button(blueFrame, fg="red", text='red', width='5', command=showRed)
btn_r4.place(relx=1.0, y=0, anchor=(tk.NE))


mainwindow.mainloop()