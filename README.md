# PART A: Code Reading & Debugging

1. Code Reading
# answer a:
1 0
Because 0 is the default value of ref, it is the old value. When opening the page, mounted is used to add 1 to the 'count' variable, so the watch that is watching this variable will be triggered and log the values.
# answer b:
double is a function in computed. computed watches the variables inside it, so every time 'count' changes, double will be triggered.


2. Debugging
# answer a:
Yes, it does. There is no default value. If the parent page doesn't pass any value, the toUpperCase function won't find any value in 'title', and this will cause a bug.
# answer b:
Normally, I like to protect it by checking the value like this:
return this.title ? this.title.toUpperCase() : '';