import tkinter as tk
from tkinter import *
from tkinter import messagebox

# Add a new task


def add_task():
    task = entry.get()
    if task:
        listbox.insert(tk.END, task)
        entry.delete(0, tk.END)
    else:
        messagebox.showwarning("Warning", "Please enter a task.")

# Delete a selected task


def delete_task():
    try:
        index = listbox.curselection()
        listbox.delete(index)
    except:
        messagebox.showwarning("Warning", "Please select a task to delete.")

# Edit a selected task


def edit_task():
    try:
        index = listbox.curselection()
        task = entry.get()
        task = listbox.get(index)
        entry.delete(0, tk.END)
        entry.insert(tk.END, task)
        listbox.delete(index)
    except:
        messagebox.showwarning("Warning", "Please select a task to edit.")


# Create the main window
window = tk.Tk()
window.title("To-Do List")
window.config(bg="#223441")
window.geometry('550x450')
window.resizable(0, 0)

heading = tk.Label(window, text="To-Do List", bg="#223441",
                   fg="#fff", font=('Times', 15))
heading.pack(pady=15)


# Create a listbox
listbox = tk.Listbox(window, height=10, width=50)
listbox.pack(pady=10)

# Create and set the scrollbar for the listbox
scrollbar = tk.Scrollbar(window)
listbox.config(yscrollcommand=scrollbar.set)
scrollbar.config(command=listbox.yview)

# Create an entry widget for adding/editing tasks
entry = tk.Entry(window, font=("Helvetica", 12))
entry.pack(pady=10)

# Create buttons for adding, editing, and deleting
add_button = tk.Button(window, text="Add Task",
                       command=add_task, background="#c5f776")
add_button.pack(pady=5)
edit_button = tk.Button(window, text="Edit Task",
                        command=edit_task, background="#4c6a9c")
edit_button.pack(pady=5)
delete_button = tk.Button(window, text="Delete Task",
                          command=delete_task, background="#ff8b61")
delete_button.pack(pady=5)

# Start the main loop
window.mainloop()
