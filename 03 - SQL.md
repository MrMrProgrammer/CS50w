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