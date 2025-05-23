# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<html>
    <head>
        <center>
            <h1>POWER CALCULATION</h1>
            <hr color="black">
        </center>
        <style>
            /* Styling the container with a border and centering it */
            .container {
                border: 3px solid black; /* Border around the content */
                padding: 20px; /* Add padding inside the box */
                width: 300px; /* Set width for the box */
                margin: 50px auto; /* Center the container horizontally and add margin from the top */
                background-color: white; /* Background color of the box */
                border-radius: 10px; /* Rounded corners (optional) */
                text-align: left; /* Ensure text inside the container is aligned left */
            }
            input {
                width: 100%; /* Make inputs take full width inside the box */
                padding: 8px; /* Padding inside input fields */
                margin-bottom: 10px; /* Space between input fields */
                border-radius: 5px; /* Rounded corners for inputs */
                border: 1px solid #ccc; /* Border for input fields */
            }
            button {
                background-color: green;
                color: white;
                padding: 10px;
                border: none;
                border-radius: 5px;
                width: 100%; /* Make button full width */
                cursor: pointer;
            }
            button:hover {
                background-color: darkgreen; /* Darker green on hover */
            }
        </style>
        <script>
            function cal() {
                var x = document.getElementById("t1").value;
                var y = document.getElementById("t2").value;
                document.getElementById("t3").value = x * x * y;
            }
        </script>
    </head>
    <body bgcolor="pink">
        <div class="container">
            <label for="intensity">Enter Intensity: </label>
            <input type="text" id="t1"><br><br>
            <label for="resistance">Enter Resistance: </label>
            <input type="text" id="t2"><br><br>
            <button onclick="cal();">Calculate</button><br><br>
            <label for="output">The Output:</label>
            <input type="text" id="t3" disabled><br><br>
        </div>
    </body>
</html>

```
```
views.py
from django.shortcuts import render
def power(request):
    context = {}
    context['power'] = "0"
    context['i'] = "0"
    context['r'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        i = request.POST.get('intensity', '0') 
        r = request.POST.get('resistance', '0') 
        print('intensity =', i)
        print('resistance =', r)
        power =  int(i) * int(i) * int(r)
        context['power'] = power
        context['i'] = i
        context['r'] = r
        print('Power =', power)
    
    return render(request, 'mathapp/math.html',context)
```
```
urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('power/',views.power,name="power"),
    path('',views.power,name="power")
]
```


## SERVER SIDE PROCESSING:

![alt text](<Screenshot 2025-04-27 215313.png>)


## HOMEPAGE:

![alt text](<Screenshot 2025-04-27 215657.png>)


## RESULT:
The program for performing server side processing is completed successfully.
