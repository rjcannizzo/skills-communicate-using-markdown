```python
"""
MVC Pattern using the Observer pattern with Tkinter
Using the Observer pattern is supposed to decuple the View from the Model.
"""
import tkinter as tk
import sqlite3

class ClickModel:
    def __init__(self):
        self._observers = []
        self._click_count = 0

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def increment_click_count(self):
        self._click_count += 1
        self.notify()

    def get_click_count(self):
        return self._click_count

    def notify(self):
        for observer in self._observers:
            observer.update()

class ClickView:
    def __init__(self, master, model):
        self._master = master
        self._model = model
        self._label = tk.Label(self._master, text="Clicks: 0")
        self._label.pack()
        self._button = tk.Button(self._master, text="Click me!", command=self._handle_button_click)
        self._button.pack()

    def _handle_button_click(self):
        self._model.increment_click_count()

    def update(self):
        click_count = self._model.get_click_count()
        self._label.config(text=f"Clicks: {click_count}")

class ClickController:
    def __init__(self, model):
        self._model = model
    def save_click_count(self):
        db_connection = sqlite3.connect("clicks.db")
        cursor = db_connection.cursor()
        cursor.execute("CREATE TABLE IF NOT EXISTS clicks (count INTEGER)")
        count = self._model.get_click_count()
        cursor.execute("INSERT INTO clicks (count) VALUES (?)", (count,))
        db_connection.commit()
        db_connection.close()

if __name__ == "__main__":
    root = tk.Tk()
    click_model = ClickModel()
    click_view = ClickView(root, click_model)
    click_model.attach(click_view)
    click_controller = ClickController(click_model)
    root.protocol("WM_DELETE_WINDOW", click_controller.save_click_count)
    root.mainloop()
```
