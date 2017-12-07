# Exploring Appium 

Appium is a cross platform testing framework which works on Android,iOS and for web development.
Appium for android can be used to automate UI elements and run tests.Appium has support for most of the popular languages and in our case we use python for its flexibility.
Appium can perform any task that involves human touch and also for scripting.

The major reason for using Appium is that we dont have to modify the source code of Application for testing it and also we can take advantage of UI elements to test out how a normal user would use the application and also handle corner cases.

### Installing Appium 


Do not install nodejs through apt-get, which will need sudo rights and appium will not work if node is installed as sudo user. If you have already installed remove it using

```
$ sudo apt-get remove nodejs
$ sudo apt-get remove npm
```

Download latest nodejs linux binaries form http://nodejs.org/download/

Extract into a folder that doesn't need sudo rights to access, for example your home folder.

```
$ tar -xvf <downloaded_binary_tar.gz>
```

<p>Add the following line to your <code>~/.bashrc   </code>   file.</p>

```
$ export PATH=$PATH:<full_path_of_the_extracted_node_folder>/bin
```

Open a now terminal and do

```
sudo npm install -g appium
appium -v 
```

Now the installation procedure of appium is complete.

### Installing UI Automator viewer

Appium solely depends upon the UI elements for its testing procedure.UI automator viewer is a tool which helps us find the text ,resource-id,content-desc,class ,package and several information which could be used to uniquely identify an UI element on the screen.

Xpath can be obtained by using a combination of the above mentioned meta-data and finally in the code the elements are identified by their Xpath.

```
$ sudo apt-get install androidsdk-uiautomatorviewer
```

> The UI automator must not capture screen when the appium server is On.This would throw an error message



### Structure of Appium 

Appium depends upon resource details of the UI elements for navigation.Each UI element will have these Node details 
* Index
* text
* resource-id
* class
* package
* content-desc
* checkable
* checked
* clickable
* enabled
* focused
* scrollable
* long-clickable
* password
* selected
* bounds

Any of these details can be used to form an Xpath through which we can access UI elements.

Examples of different locators that we will use (this is not an exhaustive list). We will keep all of our locators in xpath form
to simplify usage. We will still be able to take advantage of different fields such as text, resource-id, and content-desc.

ex1. - Exact match of text found in "text" field: "//*[@text='Call History']"

ex2. - Substring match of text found in "text" field: "//*[contains(@text, 'Please enter Password')]"

ex3. - Substring match of text found in "resource-id" field (this eliminates the need to include the package name): "//*[contains(@resource-id, 'main_call_iv')]"


Examples of using the locators:

ex1. - Finding an element with a unique locator:

find_element_by_xpath("//*[@text='Contacts']")

ex2. - Finding an element with a non-unique locator:

find_elements_by_xpath("//*[contains(@resource-id, 'addedit_phonenumber_et')]")[1]

Note the difference in this second example, "elements" vs "element" in the method call and the use of an index at the end. This is necessary because for some elements 
there can be more than one that has the same resource-id or text field




