---
title: Messages
---

I18n will attempt to find your messages on two different structures. Message Files and Message Folders.

### Message File

I18n follows a simple convention for naming messages file (a properties file).

    messages.properties => The file I18n will use if it can't find a specific message 
                      properties file.
    messages_something.properties => "something" will be the code for the language. So, 
                      if the file is named messages_pt-BR.properties, it will be 
                      responsible for pt-BR lang code.

Inside the files, just add your keys and values:

    your.key = Any text you want to display

### Message Folder

When we started using i18n everyday, sometimes we had to add really long messages that were quite hard to maintain on a property file. To deal with this problem, we created this way of adding messages.

Your message will be inside a file named after your message key. For example:

    i18n_lang == pt_BR
    your message key = your.key

I18n will look for your message at `/i18n/pt_BR/your.key` . If it's not there, it will try to read `/i18n/default/your.key` . 

### So, where is my key?

It's not really hard to get it. Let's assume that your `i18n_lang` is `pt_BR` and your i18n key is `your.awesome.message` :

- First, i18n will look for the key `your.awesome.message` inside /messages\_ptBR.properties
- if it's not there, it will look into /messages.properties
- if can't find again, will look inside /i18n/pt\_BR/your.awesome.message
- if it can't read the file, will attempt to read /i18n/default/your.awesome.message
- If at this point it couldn't find it, will simply give up and print ??? your.awesome.message ??? on the jsp. 
