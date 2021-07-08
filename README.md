This is for a shot I am writing for Edpresso|Educative.io called "How to Disable a button in Kivy?".

--------------------------------------------------------------------------------------------------------------------------

# **How to Disable and Enable a button in Kivy**

It is time to learn how to disable and enable a button in Kivy. This is necessary for many scenarios depending on the project you are working on or will be working on. If you wonder why, think about a user accidentally hitting the submit button on one of your apps, and there's nothing in the text input box. Disabling the submit button will come in handy because it will allow for those little moments that the user might accidentally hit the submit button when they are not ready to. Time to move on to learning how to code disabling a button!

First, we need to import the libraries and add the classes into our .py file, then load the .kv file into our .py file.

**main.py**<br>
 
    import kivy
    from kivy.app import App
    from kivy.uix.widget import Widget
    from kivy.lang import Builder
    
    # load in the .kv file
    Builder.load_file('main.kv')
    
    class Shot(Wiget):
        pass
    
    class ShotApp(App):
        def build(self):
            return Shot()
            
    if __name__ == '__main__':
        ShotApp().run()
        
**main.kv**<br>

    <Shot>

Now, we have the function of our app. It is time to start adding the buttons in the design file (main.kv).

Let's add two buttons called "Button 1" and "Button 2", and disable "Button 2". To do this we will use a boolean statement from Kivy, `disabled: True`.

**__main.kv__**

    <Shot>
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
                disabled: True

Every button you add into Kivy will read as `disabled: False` automatically, so there is no need to add the `disabled` method on each button. In our case though we will add it to both of our buttons.

You now know how to disable a button. However, this does not do you justice unless you know how to enable "Button 2" and disable "Button 1". For the remainder of this shot we will go over how to do this. It is fairly simple.

We need to add a few more things to our buttons before we move back into the logic in the .py file. Each button needs to have an `id:` method and a `on_press:` method added.

