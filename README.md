# Homework

## Merging datasources

We have one data source.


```json
{ 
  "target_path": "/code1/code2/code3",
  "time": "2020-01-23",
  "count": 12
}
```
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

```json
{ 
  "target_path": "/code1",
  "time": "2020-01-24",
  "count": 15
}
```


The idea is to merge those data and end up with a count for each matching hierarchy.

In this example, the expected output is
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
  "count": 30
},
{
  "target": "/code1/code2/code3",
  "time": "2020-01-23",
  "count": 25
},
{
  "target": "/code1",
  "time": "2020-01-24",
  "count": 15
}
]
```

where the first element is the top level aggregation "code1" with a count of 45 (The sum of all elements having `code1` as first part of their path)

### Work

Your job is to implement the funtion `merge` in main.py.

It takes as the only argument the path to a folder containing all the json files

It returns an array of objects ( containing `target`, `time` and `count` ) ordered by `time` then `target` hierarchy

