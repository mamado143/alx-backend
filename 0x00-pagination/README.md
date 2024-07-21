Curriculum
Short Specializations
Average: 79.19%
0x00. Pagination
Back-end
 Weight: 1
 Project will start Jul 18, 2024 6:00 AM, must end by Jul 23, 2024 6:00 AM
 Checker was released at Jul 19, 2024 12:00 PM
 An auto review will be launched at the deadline
  

Resources
Read or watch:

REST API Design: Pagination
HATEOAS
Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

How to paginate a dataset with simple page and page_size parameters
How to paginate a dataset with hypermedia metadata
How to paginate in a deletion-resilient manner
Requirements
All your files will be interpreted/compiled on Ubuntu 18.04 LTS using python3 (version 3.7)
All your files should end with a new line
The first line of all your files should be exactly #!/usr/bin/env python3
A README.md file, at the root of the folder of the project, is mandatory
Your code should use the pycodestyle style (version 2.5.*)
The length of your files will be tested using wc
All your modules should have a documentation (python3 -c 'print(__import__("my_module").__doc__)')
All your functions should have a documentation (python3 -c 'print(__import__("my_module").my_function.__doc__)'
A documentation is not a simple word, it’s a real sentence explaining what’s the purpose of the module, class or method (the length of it will be verified)
All your functions and coroutines must be type-annotated.
Setup: Popular_Baby_Names.csv
use this data file for your project

Tasks
0. Simple helper function
mandatory
Write a function named index_range that takes two integer arguments page and page_size.

The function should return a tuple of size two containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters.

Page numbers are 1-indexed, i.e. the first page is page 1.

bob@dylan:~$ cat 0-main.py
#!/usr/bin/env python3
"""
Main file
"""

index_range = __import__('0-simple_helper_function').index_range

res = index_range(1, 7)
print(type(res))
print(res)

res = index_range(page=3, page_size=15)
print(type(res))
print(res)

bob@dylan:~$ ./0-main.py
<class 'tuple'>
(0, 7)
<class 'tuple'>
(30, 45)
bob@dylan:~$
Repo:

GitHub repository: alx-backend
Directory: 0x00-pagination
File: 0-simple_helper_function.py
  
1. Simple pagination
mandatory
Copy index_range from the previous task and the following class into your code

import csv
import math
from typing import List


class Server:
    """Server class to paginate a database of popular baby names.
    """
    DATA_FILE = "Popular_Baby_Names.csv"

    def __init__(self):
