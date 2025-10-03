# Ex.05 Design a Website for Server Side Processing
## Date:03.10.2025

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
ex5.html

<!DOCTYPE html>
<html>
<head>


    <title>Lamp Power Calculator</title>
</head>
<body style="text-align:center; margin-top:50px; background: linear-gradient(to right, black, grey, white, sandybrown);">
    <h2>Power of Lamp Filament</h2>
    <p><b>Formula:</b> P = I² × R</p>

    <form method="post">
        {% csrf_token %}
        <label style="font-size: large;">Current (I in Amperes):</label><br>
        <input type="number" name="current" step="0.01" required  width: 250px;    height: 30px;     font-size: 16px;><br><br>

        <label style="font-size: larger;">Resistance (R in Ohms):</label><br>
        <input type="number" name="resistance" step="0.01" required  width: 250px;    height: 30px;     font-size: 16px><br><br>

        <button type="submit" aria-setsize="50">Calculate The Power</button>
    </form>

    {% if Power %}
        <h3>Power: {{ Power }} W</h3>
    {% endif %}
</body>
</html>

views.py

from django.shortcuts import render

def calculate_power(request):
    power = None
    if request.method == "POST":
        current = float(request.POST.get("current"))   # I
        resistance = float(request.POST.get("resistance"))  # R
        power = (current ** 2) * resistance            # P = I² × R
        print(f"Current: {current} A, Resistance: {resistance} Ω, Power: {power:.2f} W")

    return render(request, 'ex5/ex5.html', {'Power': power})

urls.py

from django.contrib import admin
from django.urls import path
from ex5 import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.calculate_power),
]

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-03 114033.png>)

## HOMEPAGE:
![alt text](<Screenshot 2025-10-03 114001.png>)

## RESULT:
The program for performing server side processing is completed successfully.
