# Advanced Python

``` Python
# Iterators for Dictionaries
my_dict = {
  "Name": "Bobb Dobbs",
  "Score": 350
}
print my_dict.items()
print my_dict.keys()
print my_dict.values()

# use print a, b rather than print a + " " + b.)
for key in my_dict:
  print key, my_dict[key]

# List comprehensions are a powerful way to generate lists using the [for/in and if] keywords

''' List Slicing Syntax: [start:end:stride]
The default starting index is 0.
The default ending index is the end of the list.
The default stride is 1
A negative stride progresses through the list from right to left.
'''

# Lambda functions are defined using the following syntax:
my_list = range(16)
filter(lambda x: x % 3 == 0, my_list)
```
