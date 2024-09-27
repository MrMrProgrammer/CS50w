# DJANGO

```python
# app1/urls.py

from django.urls import path
from . import views

app_name = "app1"   <---

urlpatterns = [
    path("", views.index, name="index")
]
```

```python
# templates/index.html

<a href="{% url 'app1:index' %}">Go To Index</a>   <---
```

## Session
save data in session
```python
def index(request):
    if "tasks" not in request.session:
        request.session["tasks"] = []
    
    context = {
        "tasks" : request.session["tasks"] = []
    }
    return render(request, "tasks/index.html", context)

def add_task(request):
    if request.method == "POST":
        from = NewTaskForm(request.POST)
        if form.is_valid():
            task = form.cleaned_data["task"]
            request.session["tasks"] += ["task"]
            return HttpResponseRedirect(reverse("task:index"))

        else:
            context = {
                "form" : form
            }
            return render(request, "tasks/add.html", context)
```

## Empty List

```html
<h1>Tasks</h1>
<ul>
    {% for task in tasks %}
        <li>{{task}}</li>
    {% empty %}            <---
        <li>No Tasks</li>
    {% endfor %}
</ul>
```