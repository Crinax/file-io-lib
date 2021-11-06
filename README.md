# file-io-lib

# Usage
## Importing

```python
  from fileIOLib import *
```

## FileIO
- Create or clear file
```python
  io = FileIO('path/to/file.txt')
  io - 0 # Clear or create file
```
- Append information to file
```python
  io << 'Some information'
```
- Read information from file and conversion to specified type
```python
  result = io >> str
  print(result) # Some information
```

- Read N symbols from file
```python
  N = 6
  result = io >> N
  print(result) # Some i
```

- Deleting N symbols from file
```python
  N = 5
  io - N
  result = io >> str
  print(result) # Some inform
```

## JsonIO
**The operations are the same as for FileIO, except for the following**
For example, we have next object
```python
  class SomeObj(object):
    def __init__(self, obj):
      self.__obj = obj

    @property
    def field(self):
      return self.__obj['field']

    @property
    def another_field(self):
      return self.__obj['another_field']
```
And we have following dictionary
```python
  s = {
    'field': 7,
    'another_field': 3
  }
```
- Append information in file
```python
  json_io = JsonIO('path/to/file.json')
  json_io << s # Information has been written
```

- Read file and conversion to specified type
```python
  some_var = json_io >> SomeObj # from dict to SomeObj type
```

- Append more in file
```python
  json_io - 0 # Clear file
  json_io << s
  # We have next file now
  # {"field": 7, "another_field": 3}
  # So we can add more
  json_io << s
  # And we have next file
  # [{"field": 7, "another_field": 3}, {"field": 7, "another_field": 3}]
```