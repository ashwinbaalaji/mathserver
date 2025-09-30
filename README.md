# Ex.05 Design a Website for Server Side Processing
# Date:30.09.2025
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
```
urls.py:

from django.urls import path
from mathapp import views

urlpatterns = [
    path('', views.calculate_power, name='calculate_power'),
]

math.html:

<!DOCTYPE html>
<html>
<head>
    <title>Power Calculator</title>
</head>
<body bgcolor="lightgrey">
    <center><h2>Power Calculation of Lamp Filament</h2>
    <form method="POST">
        {% csrf_token %}
        <label>Intensity (I):</label>
        <input type="text" name="intensity" required><br><br>

        <label>Resistance (R):</label>
        <input type="text" name="resistance" required><br><br>

        <button type="submit">Calculate Power</button>
    </form>

    {% if power is not None %}
        <h3>Result: Power (P) = {{ power }} watts</h3>
    {% endif %}
    </center>
</body>
</html>

views.py:

from django.shortcuts import render

def calculate_power(request):
    power = None
    if request.method == 'POST':
        try:
            I = float(request.POST.get('intensity'))
            R = float(request.POST.get('resistance'))
            power = I ** 2 * R
        except (ValueError, TypeError):
            power = "Invalid input. Please enter numbers."
    return render(request, 'mathapp/math.html', {'power': power})
```
# SERVER SIDE PROCESSING:<img width="1117" height="333" alt="Screenshot 2025-09-30 144520" src="https://github.com/user-attachments/assets/9d76f901-4252-4a96-8692-0b2a8930a773" />

# HOMEPAGE:<img width="1919" height="988" alt="Screenshot 2025-09-30 143742" src="https://github.com/user-attachments/assets/cb721d26-cb13-4d28-a397-caa1bbc6d721" />

# RESULT:
The program for performing server side processing is completed successfully.
