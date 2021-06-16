---
layout: post
title: AutoHotkey and Todoist
subtitle: A script to quickly add a task to Todoist using AutoHotkey
categories: scripts
tags: [script]
---

A way to add a task quickly using an AutoHotkey script.

## What you will need

1. You will need [Todoist](https://todoist.com) or if you want to try Todoist Premium free for 2 months then please use my referal link [Todoist](https://todoist.com/r/darren_baker_njsbhh). You will need to know your API token and here is how to get yours. Launch Todoist and navigate to ```Settings --> Integrations --> Scroll down to your API token```. Note this string you will need it later.

2. You will need [Autohotkey](https://www.autohotkey.com). Autohotkey is an automation scripting language for Windows. If you are here you probably know what this is capable of.

## Environment Variable

We are going to set up an Environment variable for your API token. The variable will be called ```TTOKEN```

To add a new environment variable, follow the steps listed below.

1. Open the Start menu by pressing the ```Windows Key```.
2. Type ```Environment variables``` and click on the ```Edit the system environment variables``` result.
3. Click the ```Environment variables``` button under the ```Advanced``` tab.
4. You can either create a User Variable or a System Variable.
   - **User variable**: available to only that specific user.
   - **System variable**: available to all users including the system programs.
5. To create a user variable, click ```New``` under the ```User Variables``` section.
6. To create a system variable, click ```New``` under the ```System Variables``` section.
7. Now, type ```TTOKEN``` into the first field.
8. Next, type your API token into the second field.
9. Click ```Ok``` to add the environment variable.
10. Click ```Ok``` in the environment variables window.
11. In the main window, click ```Apply``` and ```Ok``` buttons.
12. Restart Windows to apply the new environment variable.

## AutoHotkey Script

In your AutoHotkey Script add the following lines below.

After adding these lines you will need to reload your AutoHotkey script.

``` ahk
;quick add a task to todoist
;store your API Token in an Environment Variable called TTOKEN
;e.g. TTOKEN 0123456789abcdef0123456789abcdef01234567
;press ctrl-alt-n combination to get a popup box
!^n::
EnvGet, tToken, TTOKEN
InputBox, UserInput, Todoist Quick Add, "e.g. Task1 @Label1 #Project1 +ExampleUser"
if ErrorLevel
    MsgBox, CANCEL was pressed.
else
    run, curl https://api.todoist.com/sync/v8/quick/add -d token=%tToken% -d text="%UserInput%"
```

## Usage

Now everything is set up you can simply CTRL-ALT-n and a pop box will ask for your task. Enter your task information and upon pressing ```OK``` it will appear in your Todoist a few moments later.
