# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Desing your website for calculation using wireframe work.

### Step 2:
Then to execute the wireframe work desing use html,css.

### Step 3:
Use views.py to execute the coding in serverside.

### Step 4:
Mention the path of the website in urls.py.

### Step 5:

Publish the website in the given URL.

## PROGRAM :
## math.html:
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Calculation</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    *{
        box-sizing: border-box;
        font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
    }

    body{
        background-color: #F7C4D1;
    }

    .container{
        width: 1080px;
        height: 350px;
        margin-top: 100px;
        margin-left: auto;
        margin-right: auto;
        border-radius: 25px;
        background-color:#EF6786;
    }
    h1{
        text-align: center;
        padding-top: 15px;
    }
    .content {
      display: block;
      width: 100%;
      background-color: #D71B47;
      min-height: 350px;
      margin-top: 50px;
      margin-bottom: 50px;
      border-radius: 10px;
      border: 1px solid whitesmoke;
    }
    .formelement {
      text-align: center;
      font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
      font-size: x-large;
      font-weight: bold;
      margin-top: 5px;
      margin-bottom: 5px;
    }
    .footer {
      display: block;
      width: 100%;
      height: 40px;
      margin-top: 50px;
      margin-bottom: 50px;
      background-color: #7B0F28;
      text-align: center;
      padding-top: 10px;
      border-radius: 5px;
      color: #FCE3E9;
    }
</style>
<body>
    <div class="container">
        <div class="content">
        <h1>AREA OF A TRIANGLE</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="formelement"> 
                Base:<input type="text" name="base" value={{b}}></input><br/>
            </div>
            <div class="formelement">
                Height:<input type="text" name="height" value={{h}}></input><br/>
            </div>
            <div class="formelement">
                <input type="submit" value="Calculatearea"></input><br/>
            </div>
            <div class="formelement">
                Area:<input type="text" name="area" value={{area}}></input>
            </div>
        </form>
        </div>
        <div class="footer">
            Math Calculator Program, Developed by Kaushika Anandharaman.
        </div>
    </div>
    
</body>
</html>
```
### views.py:
```
from django.shortcuts import render

def areacalculation(request):
    context ={}
    context["area"]='0'
    context["b"]='0'
    context["h"]='0'
    if request.method == 'POST':
        
        b=request.POST.get('base','0')
        h=request.POST.get('height','0')
        area=0.5*int(b)*int(h)
        context['area'] = area
        context['b']=b
        context['h']=h
    return render(request,"app/math.html",context)
```
### urls.py:
```
from django.contrib import admin
from django.urls import path
from app import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaoftriangle/',views.areacalculation,name="areaoftriangle"),
    path('',views.areacalculation,name="areaoftriangleroot")
]
```
## OUTPUT:
![](output1.png)
![](output2.png)

## Result:
A website to perform mathematical calculations in server side is created.
