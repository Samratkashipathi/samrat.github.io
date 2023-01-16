# [26-05-2021] - Cases when YAML will not work if not properly declared

## Wrong Interpretation

- There are some cases where yaml will not work and can be hard to debug the error
    - Example 1:
        - Suppose you have to store user name in yaml and read it later. One of the user is named "Christopher Null"
        
        ```
        name:
          first_name: Christopher
          second_name: Null
        ```
        
    - Example 2
        - Suppose you are storing short form of some countries and one of the country is Norway
        
        ```
        countries:
          - IN
          - SA
          - NO
        ```
        

Expected behaviour when yaml is read. Since YAML considers everything as a string.

```python
{ 
	'countries': ['IN', 'SA', 'NO'], 
	'name': 
		{
			'first_name': 'Christopher', 
			'second_name': 'Null'
		}
}
```

Actual result:

```python
{ 
	'countries': ['IN', 'SA', False], 
	'name': 
		{
			'first_name': 'Christopher', 
			'second_name': None
		}
}
```

> NO is converted to False which was supposed to be short for Norway

Null is converted to None which was supposed to be second name
> 

## Data Type Mismatch

- Another example:
    - Suppose you want to store version information of the packages in yaml
    
    ```
    versions:
    	postgres: 9.3
      rabbitmq: 3.18.9
    ```
    
    Expectation
    
    ```python
    {
    'versions':
    	{
    		'postgres' : '9.3'
    		'rabbitmq' : '3.18.9'
    	}
    }
    ```
    

Actual

```python
{
'versions':
	{
		'postgres' : 9.3
		'rabbitmq' : '3.18.9'
	}
}
```

Since 9.3 is a floating value is is converted as floating value. We need to be extra careful in the parsing logic

## Learning

<aside>
💡 While declaring yaml if we know that value is string, encapsulate in double quotes

</aside>

## Code snippet

```python
import os
from yaml import safe_load

with open('sample.yaml') as file:
    data = safe_load(file) 

print(data)
```

```yaml
countries:
  - IN
  - SA
  - NO

name:
  first_name: Christopher
  second_name: Null

versions:
  postgres: 9.3
  rabbitmq: 3.18.9
```

### Related Reads
- https://ruudvanasseldonk.com/2023/01/11/the-yaml-document-from-hell?ref=architecture-notes
