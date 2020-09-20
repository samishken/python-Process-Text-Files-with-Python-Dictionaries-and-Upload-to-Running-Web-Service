# python-Process-Text-Files-with-Python-Dictionaries-and-Upload-to-Running-Web-Service

Project is to take customer reviews (saved as .txt files) and display them on Django website. </br>
To do this:</br>
1 - we need to write a script to convert those .txt files and process them into Python dictionaries, </br>
2 - Then upload the data onto your company's website (currently using Django). </br>
3 - Files are all written in the same format (i.e. title, name, date, and feedback). </br>

The below is a Python script that uploads all the .txt files stored in a particular folder, 
without having to turn it into a dictionary one by one.



`#! /usr/bin/env python3` </br>

`import os, requests` </br>
`path="WHERE THE TXT FILES ARE LOCATED"` </br>
`url= "http://IP-ADDRESS/file_content/"` </br>
 
`for file in os.listdir(path):` </br>
    `keys = ["title","name","date","file_content"]` </br>
    `feedback_json = {}` </br>

    with open(path + "/" + file, "r" ) as txtfile:  
        x = 0  
        for line in txtfile:  
            feedback_json[keys[x]] = line.rstrip('\n')  
            x += 1  
    response = requests.post(url, json=feedback_json)  
