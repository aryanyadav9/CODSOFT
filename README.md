# CODSOFT
from tkinter import Tk, Frame, Label, Button
import tkinter as tk


class Question:
    def _init_(self, question, answers, correctLetter):
        self.question = question
        self.answers = answers
        self.correctLetter = correctLetter

    def check(self, letter, view):
        global right
        if (letter == self.correctLetter):
            label = Label(view, font="helvetica,8",
                          bg="#bad1c0", text="Right!")
            right += 1
        else:
            label = Label(view, font="helvetica,8",
                          bg="#bad1c0", text="Wrong!")
        label.pack(pady=10)
        view.after(1000, lambda *args: self.unpackView(view))

    def getView(self, window):
        view = Frame(window, bg="#bad1c0")
        Label(view, text=self.question, font="helvetica,8",
              bg="#bad1c0").pack(pady=10)
        Button(
            view, text=self.answers[0], height=1, width=15, font="helvetica,5", bg="#bad1c0", command=lambda *args: self.check("A", view)).pack(pady=10)
        Button(
            view, text=self.answers[1], height=1, width=15, font="helvetica,5", bg="#bad1c0", command=lambda *args: self.check("B", view)).pack(pady=10)
        Button(
            view, text=self.answers[2], height=1, width=15, font="helvetica,5", bg="#bad1c0", command=lambda *args: self.check("C", view)).pack(pady=10)
        Button(
            view, text=self.answers[3], height=1, width=15, font="helvetica,5", bg="#bad1c0", command=lambda *args: self.check("D", view)).pack(pady=10)
        return view

    def unpackView(self, view):
        view.pack_forget()
        askQuestion()


def askQuestion():
    global questions, window, index, button, right, number_of_questions
    if (len(questions) == index + 1):
        Label(window, font="helvetica,12", bg="#bad1c0", text="Thank you for answering the questions. " + str(right) +
              " of " + str(number_of_questions) + "\n questions answered right").pack(pady=10)
        return
    button.pack_forget()
    index += 1
    questions[index].getView(window).pack()


questions = []
file = open("questions.txt", "r")
line = file.readline()
while (line != ""):
    questionString = line
    answers = []
    for i in range(4):
        answers.append(file.readline())
    correctLetter = file.readline()
    correctLetter = correctLetter[:-1]
    questions.append(Question(questionString, answers, correctLetter))
    line = file.readline()
file.close()
index = -1
right = 0
number_of_questions = len(questions)

window = Tk()
window.title("Weather App")
window.config(bg="#bad1c0")
window.geometry("550x450")

heading = tk.Label(window, text="Quize App",
                   font="Arial,30,bold", bg="#bad1c0")
heading.pack(pady=20, padx=130)


button = Button(window, text="Start",
                command=askQuestion, font="Arial,30,bold")
button.pack()
window.mainloop()
