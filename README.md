# Homework

## Merging datasources

We have two data sources.

The first one is like

```json
{ 
  "id":  "The key",
  "targeting_path": "/code1/code2/code3",
  "time": "2020-01-23",
  "count": 12
}
```

and the second one

```json
{ 
  "target_path": "/code1/code2/code3",
  "time": "2020-01-23",
  "count": 13
}
```
```json
{ 
  "target_path": "/code1/code2",
  "time": "2020-01-23",
  "count": 5
}
```
```json
{ 
  "target_path": "/code1",
  "time": "2020-01-23",
  "count": 15
}
```


The idea is to merge those data and end up with a count for each matching hierarchy.

In this example, the expected output it 
```json
[
{
  "target": "/code1",
  "time": "2020-01-23",
  "count": 45
},
{
  "target": "/code1/code2",
  "time": "2020-01-23",
  "count": 40
},
{
  "target": "/code1/code2/code3",
  "time": "2020-01-23",
  "count": 25
}
]
```

where the first element is the top level aggregation "code1" with a count of 45 (The sum of all elements having `code1` as first part of their path)

### Work

Your job is to implement the funtion `merge` in main.py.

It takes two arguments:
* first argument is the folder containing the json files of the first datasource
* second argument is the folder containing the json files of the second datasource

It returns an array of objects ( containing target, time and cound ) ordered by target hierarchy

