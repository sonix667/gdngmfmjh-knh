# gdngmfmjh-knh
/mnt/data/A_traditional_painting,_possibly_created_us 
import tkinter as tk
from tkinter import messagebox
import os

DOSYA = "notlar.txt"

def kaydet():
    with open(DOSYA, "a", encoding="utf-8") as f:
        f.write("\n")
    listele()

def listele():
    liste_text.delete("1.0", tk.END)
    if not os.path.exists(DOSYA):
        liste_text.insert(tk.END, "Henüz not yok.")
        return
    with open(DOSYA, "r", encoding="utf-8") as f:
        satirlar = f.readlines()
    if not satirlar:
        liste_text.insert(tk.END, "Henüz not yok.")
        return
    numara = 1
    for satir in satirlar:
        liste_text.insert(tk.END, f"{numara}.\n")
        numara += 1

root = tk.Tk()
root.title("Ultra Premium Not Defteri")
root.geometry("400x400")

frame = tk.Frame(root)
frame.pack(pady=10)

kaydet_btn = tk.Button(frame, text="Not Ekle", command=kaydet)
kaydet_btn.grid(row=0, column=0, padx=5)

liste_text = tk.Text(root, width=50, height=20)
liste_text.pack(pady=10)

listele()

root.mainloop()
