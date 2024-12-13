1. Install Necessary Libraries:

 
!pip install kivy
!pip install buildozer
Use code with caution
2. Create the Python Script (main.py):

 
from kivy.app import App
from kivy.uix.button import Button
from kivy.uix.gridlayout import GridLayout
from kivy.uix.textinput import TextInput
from kivy.lang import Builder

# Kivy Language code for the app layout
kv_string = """
<CalculatorApp>:
    result: result
    GridLayout:
        cols: 4
        TextInput:
            id: result
            font_size: 32
            readonly: True
            halign: 'right'
            multiline: False
        # Buttons for digits and operations
        Button:
            text: '7'
            on_press: app.on_button_press(self)
        Button:
            text: '8'
            on_press: app.on_button_press(self)
        Button:
            text: '9'
            on_press: app.on_button_press(self)
        Button:
            text: '/'
            on_press: app.on_button_press(self)
        Button:
            text: '4'
            on_press: app.on_button_press(self)
        Button:
            text: '5'
            on_press: app.on_button_press(self)
        Button:
            text: '6'
            on_press: app.on_button_press(self)
        Button:
            text: '*'
            on_press: app.on_button_press(self)
        Button:
            text: '1'
            on_press: app.on_button_press(self)
        Button:
            text: '2'
            on_press: app.on_button_press(self)
        Button:
            text: '3'
            on_press: app.on_button_press(self)
        Button:
            text: '-'
            on_press: app.on_button_press(self)
        Button:
            text: 'C'
            on_press: app.on_button_press(self)
        Button:
            text: '0'
            on_press: app.on_button_press(self)
        Button:
            text: '='
            on_press: app.on_button_press(self)
        Button:
            text: '+'
            on_press: app.on_button_press(self)
"""

Builder.load_string(kv_string)

class CalculatorApp(App):
    def build(self):
        return  # Layout is defined in kv_string

    def on_button_press(self, instance):
        current_text = self.root.ids.result.text
        button_text = instance.text

        if button_text == 'C':
            self.root.ids.result.text = ''
        elif button_text == '=':
            try:
                self.root.ids.result.text = str(eval(current_text))
            except Exception:
                self.root.ids.result.text = 'Error'
        else:
            self.root.ids.result.text = current_text + button_text

if __name__ == '__main__':
    CalculatorApp().run()


   
3. Create the buildozer.spec File:

 
[app]
# (str) Title of your application
title = Calculator
# (str) Package name
package.name = mycalculator
# (str) Package domain (needed for android/ios packaging) (like 'org.test')
package.domain = org.test
# (str) Source code where the main.py live
source.dir = .
# (list) Source files to include (let empty to include all the files)
source.include_exts = py,png,jpg,kv,atlas
# (list) List of inclusions using pattern matching
#source.include_patterns = assets/*,images/*.png
# (list) Source files to exclude (let empty to not exclude any files)
#source.exclude_exts = spec
# (list) List of directory to exclude (let empty to not exclude any directories)
#source.exclude
