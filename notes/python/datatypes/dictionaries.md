# Dictionaries

Reference:

  + https://docs.python.org/3/library/stdtypes.html#dict
  + https://docs.python.org/3/library/stdtypes.html#dictionary-view-objects
  + https://docs.python.org/3/tutorial/datastructures.html#dictionaries
  + https://docs.python.org/3/tutorial/datastructures.html#looping-techniques

Many programming languages provide an "associative array" datatype  which provides an opportunity to create objects with named attributes. In this way, an associative array is similar to a row in a CSV-formatted spreadsheet or a record in a database, where the associative array's "keys" represent the column names and its "values" represent the cell values. Associative arrays are said to have "key/value" pairs, where the "key" represents the name of the attribute and the "value" represents the attribute's value.

city | name | league
--- | --- | ---
New York | Yankees | major
New York | Mets | major
Boston | Red Sox | major
New Haven | Ravens | minor

```python
[
    {"city": "New York", "name": "Yankees", "league":"major"},
    {"city": "New York", "name": "Mets", "league":"major"},
    {"city": "Boston", "name": "Red Sox", "league":"major"},
    {"city": "New Haven", "name": "Ravens", "league":"minor"}
]
```

Python's implementation of the associative array concept is known as a "dictionary". A Python dictionary comprises curly braces (`{}`) containing one or more key/value pairs, with each key separated from its value by a colon (`:`) and each key/value pair separated by a comma (`,`). If you are familiar with JavaScript "Objects" (JSON) or Ruby "Hashes", the concept is the same. If you need to convert a Python dictionary to JSON, reference the [`json` module](../modules/json.md).

Example dictionaries:

```python
{}

{"a": 1, "b": 2, "c": 3}

{"a": 1, "b": 2, "c": 3, "fruits": ["apple", "banana", "pear"]} # dictionaries can contain lists, or even other nested dictionaries

{"first_name": "Santa", "last_name": "Claus", "message": "Ho Ho Ho"}
```

Access individual object attributes by their key:

```python
person = {
    "first_name": "Santa",
    "last_name": "Claus",
    "message": "Ho Ho Ho",
    "stops": ["New York", "Denver", "San Francisco"]
}

person["first_name"] #> "Santa"
person["last_name"] #> "Claus"
person["message"] #> "Ho Ho Ho"
person["stops"] #> ["New York", "Denver", "San Francisco"]
person["stops"][1] #> "Denver" (an array is still an array, even if it exists inside a dictionary!)
```

Add or update or remove attributes from an object:

```python
person = {
    "first_name": "Santa",
    "last_name": "Claus",
    "message": "Ho Ho Ho",
    "stops": ["New York", "Denver", "San Francisco"],
    "fav_color": "blue"
}

person["spouse"] = "Mrs. Claus" # this is mutating

person["fav_color"] = "red" # this is mutating

del person["stops"] # this is mutating

person #> {'first_name': 'Santa', 'last_name': 'Claus', 'message': 'Ho Ho Ho', 'spouse': 'Mrs. Claus', 'fav_color': 'red' }
```

Make use of built-in dictionary methods for easier data-processing:

```python
person = {
    "first_name": "Santa",
    "last_name": "Claus",
    "message": "Ho Ho Ho",
    "stops": ["New York", "Denver", "San Francisco"]
}

person.keys() #> dict_keys(['first_name', 'last_name', 'message', 'stops'])
list(person.keys()) #> ['first_name', 'last_name', 'message', 'stops']

person.values() #> dict_values(['Santa', 'Claus', 'Ho Ho Ho', ['New York', 'Denver', 'San Francisco']])
list(person.values()) #> ['Santa', 'Claus', 'Ho Ho Ho', ['New York', 'Denver', 'San Francisco']]

person.items() #> dict_items([('first_name', 'Santa'), ('last_name', 'Claus'), ('message', 'Ho Ho Ho'), ('stops', ['New York', 'Denver', 'San Francisco'])])

for k, v in person.items():
    print("KEY:", k, "... VALUE:", v)

#> KEY: first ... VALUE: Santa
#> KEY: last ... VALUE: Claus
#> KEY: message ... VALUE: Ho Ho Ho
#> KEY: stops ... VALUE: ['New York', 'Denver', 'San Francisco']
```
