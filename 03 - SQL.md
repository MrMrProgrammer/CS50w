# SQL

```python
class Flight(models.Model):
    origin = models.Foreignkey(Airport, on_delete = models.CASCADE, related_name = "departures")
    destination = models.ForeignKey(Airport, on_delete = models.CASCADE, related_name = "arrivals")
    duration = models.IntegerField()
```

If we use `related_name`, our query will be as follows :

```python
airport = Airport.objects.get(id=1)

departing_flights = airport.departures.all()

arriving_flights = airport.arrivals.all()
```

Otherwise, we must retrieve the data as follows :

```python
airport = Airport.objects.get(id=1)

departing_flights = airport.flight_set.all()
```

So if we don't use `related_name`, Django will automatically use a `_set` at the end of the table name as a reverse relation.

⚠️ **Warning:** If there are several foreign keys in a class and we do not use `related_name`, we will encounter an error.

```python
airport = Airport.objects.get(id=1)
departing_flights = airport.flight_set.all()
arriving_flights = airport.flight_set.all()
```

---

### Django Panel Admin

```python
# admin.py

class PassengerAdmin(admin.ModelAdmin):
    filter_horizontal = ("flights",)

admin.site.register(Passenger, PassengerAdmin)
```

---

### Authenticate in Django

```python
from django.contrib.auth import authenticate, login

def login_view(request):
    if request.method == "POST":
        username = request.POST["username"]
        password = request.POST["password"]

        user = authenticate(request, username=username, password=password)

        if user:
            login(request, user)
            return HttpResponseRedirect(reverse("index"))

        else:
            context = {
                "message" : "Invalid Credentials!"
            }
            return render(request, "users/login.html", context)

    return render(request, "users/login.html")
```

---

### Add a Field to a Record in Database

```python
# models.py
class Passenger(models.Model):
    first = models.CharField(max_length = 64)
    last = models.CharField(max_length = 64)
    flights = models.ManyToManyField(Fligth, blank = True, related_name = "passengers")


# views.py
def book(request, flight_id):
    if request.method == "POST":
        flight = Flight.objects.get(pk = flight_id)
        passenger = Passenger.objects.get(pk = int(request.POST["passenger"]))
        passenger.flight.add(flight)
        return HttpResponseRedirect(reverse("flight", args = (flight.id,)))
```