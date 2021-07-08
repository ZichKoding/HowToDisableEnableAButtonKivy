# HowToDisable&EnableAButtoninKivy-Python
This is for a shot I am writing for Edpresso|Educative.io called "How to Disable a button in Kivy?".

I will also post the published work here. Hopefully, this will help those that are searching for how to disable and enable buttons.

It is time to learn how to disable and enable a button in Kivy. This is necessary for many scenarios depending on the project you are working on or will be working on. If you wonder why think about a user accidentally hitting the submit button on one of your apps, and there’s nothing in the text input box. Disabling the submit button will come in handy because it will allow for those little moments that the user might accidentally hit the submit button when they are not ready to. Time to move on to learning how to code disabling a button!

First, we need to import the libraries and add the classes into our .py file, then load the .kv file.



`import kivy`
`from kivy.app import App`
`from kivy.uix.widget import Widget`
`from kivy.lang import Builder`

# load in the .kv file
Builder.load_file('main.kv')

class Shot(Widget):
  pass

class ShotApp(App):
  def build(self):
    return Shot()

if __name__ == '__main__':
  ShotApp().run()`

***main.kv***
`<Shot>`
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@


Now, we have the function of our app. It is time to start adding the buttons in the design file(main.kv).

Let’s add two buttons called “Button 1” and “Button 2”, and disable “Button 2”. To do this we will use a boolean statement from Kivy, disabled: True.


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
***main.py***
`import kivy
from kivy.app import App
from kivy.uix.widget import Widget
from kivy.lang import Builder

# load in the .kv file
Builder.load_file('main.kv')

class Shot(Widget):
  pass

class ShotApp(App):
  def build(self):
    return Shot()

if __name__ == '__main__':
  ShotApp().run()`

***main.kv***
`<Shot>
	BoxLayout:
		orientation: "horizontal"
        size: root.width, root.height

        Button:
            text: "Button 1"
            size_hint: (1,1)
            disabled: False
            
        Button:
            text: "Button 2"
            size_hint: (1,1)
            disabled: True`
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Our focus here is main.kv.


Every button you add into Kivy will read as disabled: False automatically, so there is no need to add the disabled method on each button. In our case though we will add it to both of our buttons.

You now know how to disable a button. However, this does not do you justice unless you know how to enable “Button 2” and disable “Button 1”. For the remainder of this shot we will go over how to do this. It is fairly simple.

We need to add a few more things to our buttons before we move back into the logic in the .py file. Each button needs to have an id: method and a on_press: method added.


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
***main.py***
`import kivy
from kivy.app import App
from kivy.uix.widget import Widget
from kivy.lang import Builder

# load in the .kv file
Builder.load_file('main.kv')

class Shot(Widget):
  pass

class ShotApp(App):
  def build(self):
    return Shot()

if __name__ == '__main__':
  ShotApp().run()`

***main.kv***
`<Shot>
	BoxLayout:
		orientation: "horizontal"
        size: root.width, root.height

        Button:
            # BELOW IS THE ID TAG
            id: but_one    
            text: "Button 1"
            size_hint: (1,1)
            disabled: False
            # BELOW IS THE ON_PRESS TAG
            on_press: root.disable_other()
            
        Button:
            # BELOW IS THE ID TAG
            id: but_two    
            text: "Button 2"
            size_hint: (1,1)
            disabled: True
            # BELOW IS THE ON_PRESS TAG
            on_press: root.disable_other()`
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Our focus here is main.kv.


Finally, we can move back into our .py file! All we need to do is add our disable_other() method to our class Shot(). Then we add an if statement to disable_other() for our app to determine when our enabled button is pressed it will disable itself and enable the other button.

It should look something like this:



@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
***main.py***
`import kivy
from kivy.app import App
from kivy.uix.widget import Widget
from kivy.lang import Builder

# load in the .kv file
Builder.load_file('main.kv')

class Shot(Widget):
	# Method to disable one button and activate the other.
	def disable_other(self):
		if self.ids.but_two.disabled == False:
			self.ids.but_two.disabled = True
			self.ids.but_one.disabled = False
            print('Button One is now disabled. Button Two is now enabled.')
		else:
			self.ids.but_one.disabled = True
			self.ids.but_two.disabled = False
            print('Button One is now enabled. Button Two is now disabled.')
            
class ShotApp(App):
  def build(self):
    return Shot()

if __name__ == '__main__':
  ShotApp().run()`

***main.kv***
`<Shot>
	BoxLayout:
		orientation: "horizontal"
        size: root.width, root.height

        Button:
            # BELOW IS THE ID TAG
            id: but_one`        
            text: "Button 1"
            size_hint: (1,1)
            disabled: False
            # BELOW IS THE ON_PRESS TAG
            on_press: root.disable_other()
            
        Button:
            # BELOW IS THE ID TAG
            id: but_two
            text: "Button 2"
            size_hint: (1,1)
            disabled: True
            # BELOW IS THE ON_PRESS TAG
            on_press: root.disable_other()`
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

You now have the knowledge to disable and enable your buttons with Kivy on demand! Have fun coding!
