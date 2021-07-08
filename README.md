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
