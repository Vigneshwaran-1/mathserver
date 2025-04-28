# Ex.05 Design a Website for Server Side Processing
# Date:28/04/2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html
~~~~
<html>
<head>
    <title> mathapp </title>      
    <style>
body{
    background-color:blue;
}
h1{
    background-color:yellow;
}
form{
    background-color:orange;
}
</style>
</head >
<body>
    <h1 align="center"> POWER OF BULB </h1>
    <form align="center" method="POST">
        {% csrf_token %}
        Intensity <input name="I" value="{{i}}">
        <br>
        <br>
        Resistance <input name="R" value="{{r}}">
        <br>
        <br>
        <input type="submit" value="calculate">
        <br>
        <br>
        Power <input name="power"value={{power}}>
    </form>
    </body> 
</html>
~~~~
views.py
~~~~
from django.shortcuts import render 
def powerofbulb(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i) ** 2)*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r
        print('power=',power) 
    return render(request,'mathapp/math.html',context)
~~~~
url.py
~~~~

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerofbulb/',views.powerofbulb,name="powerofbulb"),
    path('',views.powerofbulb,name="powerofbulbroot")
]
~~~~

# SERVER SIDE PROCESSING:
![ssp](https://github.com/user-attachments/assets/456581c7-f72c-4a1d-a22c-c8694dafee97)

# HOMEPAGE:
![hp](https://github.com/user-attachments/assets/1c0b98e2-6285-4c9a-a70e-718d31e0543f)


# RESULT:
The program for performing server side processing is completed successfully.
