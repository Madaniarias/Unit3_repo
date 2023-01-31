# GUI Building Tasks

## Instrutions

1. Create a file inside your repository called "gui_task.md"
2. Reproduce the Examples inside the slide
3. Solve the Task 1 if you are SL and Task1 and Task 2 if you are HL

## Reproducing examples

## Example 1

### Python file

```.py
from kivymd.app import MDApp

class example1(MDApp):
    def build(self):
        return

test = example1()
test.run()
```

### Kivy file

```.py

Screen:
    size: 500, 500

    MDLabel:
        text: "Hello World"
        halign: "center"
        font_size: "34pt"
```

### Test 
![Screen Shot 2023-01-31 at 16 45 52](https://user-images.githubusercontent.com/111761417/215698034-6c1864f7-779b-4dac-89cf-d06df097f3ef.png)

![Screen Shot 2023-01-31 at 16 45 30](https://user-images.githubusercontent.com/111761417/215698050-df740bcf-344c-4ad8-9cad-500bea824309.png)

## Example 2

### Python file

```.py

from kivymd.app import MDApp

class example2(MDApp):
    def build(self):
        return
    def close(self):
        exit()

test = example2()
test.run()

```

### Kivy file

```.py
Screen:
    size: 500,500
    MDBoxLayout:
        pos_hint: {"center_x":0.5}
        size_hint: .7,.7
        md_bg_color: "#fdfcdc"
        orientation: "vertical"

        MDLabel:
            text: "Hello World"
            halign: "center"
            font_size: "34pt"

        MDRaisedButton:
            text: "Close"
            size_hint: .5, 1
            font_size: "34pt"
            md_bg_color: "#f07167"
            pos_hint: {"center_x":0.5}
            on_press:
                app.close()

```

### Test

![Screen Shot 2023-01-31 at 16 48 28](https://user-images.githubusercontent.com/111761417/215698512-09376589-74fe-47d4-b6bb-cdde1b5f2c21.png)

![Screen Shot 2023-01-31 at 16 48 47 1](https://user-images.githubusercontent.com/111761417/215698526-dca4628f-c2dd-4ca4-b4bd-94c7c46a1f90.png)


## Example 3

### Python file

```.py
from kivymd.app import MDApp

class example3(MDApp):
    def build(self):
        return
    def change_author(self,name):
        self.root.ids.title.text = f"Author{name}"

test = example3()
test.run()
```

### Kivy file

```.py
Screen:
    size: 500, 500
    MDLabel:
        id: title
        text: ""
        font_style: "H1"
        pos_hint: {"center_y":.8}
        halign: "center"

    MDBoxLayout:
        pos_hint: {"center_x":.5,"center_y":.5}
        size_hint: .7, .2
        orientation: "horizontal"

        MDChip:
            text: "Author A"
            pos_hint: {"center_y": .5}
            icon_right: "close-circle-outline"
            md_bg_color: "#003049"
            text_color: "#FFFFFF"
            on_press: app.change_author("A")

        MDChip:
            text: "Author B"
            pos_hint: {"center_y": .5}
            icon_right: "close-circle-outline"
            md_bg_color: "#D62828"
            on_press: app.change_author("B")

        MDChip:
            text: "Author C"
            pos_hint: {"center_y":.5}
            icon_right: "close-circle-outline"
            md_bg_color: "#F77F00"
            on_press: app.change_author("C")

        MDChip:
            text: "Author D"
            pos_hint: {"center_y":.5}
            icon_right: "close-circle-outline"
            md_bg_color: "#FCBF49"
            on_press: app.change_author("D")

        MDChip:
            text: "Author E"
            pos_hint: {"center_y":.5}
            icon_right: "close-circle-outline"
            md_bg_color: "#EAE2B7"
            on_press: app.change_author("E")

```

### Test

![Screen Shot 2023-01-31 at 16 49 51](https://user-images.githubusercontent.com/111761417/215698868-eb066831-6682-4344-b621-15cdd9f343d7.png)
![Screen Shot 2023-01-31 at 16 50 47](https://user-images.githubusercontent.com/111761417/215698880-17235461-9ed2-4164-bc87-24df3ec1a46e.png)
![Screen Shot 2023-01-31 at 16 50 50](https://user-images.githubusercontent.com/111761417/215698890-8c29c2a9-9071-4495-bad8-ea4769d08b43.png)

## TASK 1

### Instructions

Create a Currency Converter GUI that takes an integer representing an amount from your home country currency and converts it into USD and JPY rounded to 2 decimals.
⚠️ Remember to validate user inputs

### Python file
```.py

# currency_convertor.py

from kivymd.app import MDApp


class convert(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.count = 0
        self.dollar_count = 0
        self.japanese_count = 0

    # we have to use to build the screen
    def build(self):
        return
    def close(self):
        exit()

    def set_money(self):
        # validate that it is a digit

        user_start = self.root.ids.user_start_x.text
        if user_start.isdigit():
            self.count = user_start
            self.root.ids.counter_label.text = f"B/.{self.count}"
        elif user_start == '':
            self.count = 0
            self.root.ids.counter_label.text = f"B/.{self.count}"

    def change(self, name: str):
        if 'dollar' in name:
            self.dollar_count = f"{self.count}"
            self.root.ids.counter_label.text = f"{self.dollar_count} $"
        else:
            self.count = int(self.count)
            self.japanese_count = f"{self.count * 130}"
            self.root.ids.counter_label.text = f"{self.japanese_count} ¥ "

# demo_class is an object of the class layout_demo
demo_convertor = convert()
demo_convertor.run()

```
### Kivy file

```.py
#currency_convertor.k

Screen:
    id: 500,500

    MDBoxLayout:
        id: welcome_box
        orientation: "vertical"
        size_hint: 1, .1
        md_bg_color: "#6978E9"
        pos_hint: {"center_x":.5, "center_y":.7}

        MDLabel:
            id: label
            text: "Welcome to the Currency Convertor!"
            halign: "center"
            font_size: '30pt'

    MDBoxLayout:
        id: close_box
        orientation: "vertical"
        size_hint: 1, .1
        md_bg_color: "#6978E9"
        pos_hint: {"center_x":.5, "center_y":.3}

        MDRaisedButton:
            text: "Close"
            size_hint: 1, 1
            font_size: "20pt"
            md_bg_color: "#f07167"
            pos_hint: {"center_x":0.5}
            on_press: app.close()

    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint: 1, .3
        md_bg_color: "#6978E9"
        pos_hint: {"center_x":.5, "center_y":.5}

        MDTextField:
            id: user_start_x
            hint_text: "Enter Balboa amount"
            mode: "rectangle"
            icon_left: 'cash'
            size_hint: .25, .50
            md_bg_color: "#a699d0"
            pos_hint: {"center_x":.5}
            on_text: app.set_money()

        MDBoxLayout:
            id: second_box
            orientation: "horizontal"
            md_bg_color: "#9D9EF2"

            MDLabel:
                id: counter_label
                font_style: "H3"
                halign: "center"

            MDBoxLayout:
                id: third_box
                orientation: "vertical"

                MDRaisedButton:
                    id: on_btn
                    text: "USD"
                    on_press: app.change("dollar")
                    size_hint: 1,1
                    md_bg_color: "#B888E8"
                    font_size: "16pt"

                MDRaisedButton:
                    id: on_btn
                    text: "Japanese Yen"
                    on_press: app.change("yen")
                    size_hint: 1,1
                    md_bg_color: "#B888E8"
                    font_size: "16pt"

```

### Test

![Screen Shot 2023-01-31 at 17 01 17](https://user-images.githubusercontent.com/111761417/215701262-0acc2b4f-165e-400e-b7ec-5d2a5ef4bbf7.png)

https://user-images.githubusercontent.com/111761417/215701548-ccac7284-f61e-43f2-85fb-798d5612b0cc.mov

## TASK 2 (HL)

### Instructions

Create a GUI for a converter of Bits to Bytes following the table below:


### Python file

### Kivy file

### Test






