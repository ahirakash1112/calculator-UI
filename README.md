# main.py

import tkinter as tk
from calculator import Calculator

def button_click(value):
    if value == "=":
        result = calc.evaluate_expression()
        display.set(result)
    elif value == "C":
        display.set(calc.clear_expression())
    else:
        calc.add_to_expression(value)
        display.set(calc.expression)

# Initialize the main window
root = tk.Tk()
root.title("Simple Calculator")

calc = Calculator()

display = tk.StringVar()

# Entry widget to display the expression or result
entry = tk.Entry(root, textvariable=display, font=("Arial", 20), bd=10, insertwidth=4, width=14, borderwidth=4)
entry.grid(row=0, column=0, columnspan=4)

# Calculator buttons
buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', 'C', '=', '+'
]

# Create and place buttons on the grid
row = 1
col = 0
for button in buttons:
    action = lambda x=button: button_click(x)
    tk.Button(root, text=button, padx=20, pady=20, font=("Arial", 18), command=action).grid(row=row, column=col)
    col += 1
    if col > 3:
        col = 0
        row += 1

root.mainloop()
