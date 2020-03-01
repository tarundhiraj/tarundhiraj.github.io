---
layout: post
title: Slots in Python
---

The special attribute *\_\_slots__* allows you to explicitly state which instance attributes you expect your object instances to have.
The benefits of using *\_\_slots__* are as follows:

- **faster** attribute access.
- **space savings** in memory.

The *space savings* is from the following:

- Storing value references in slots instead of *\_\_dict__*
- Denying *\_\_dict__* and *\_\_weakref__* creation if parent classes deny them and you declare *\_\_slots__*

Example:

	class Person(object):
		__slots__ = ('a', 'b')


Now, you can't have dynamic properties in person class ie. You can only access and modify properties a and b.


	person = Person()
	person.a = 'a'
	person.b = 'b'
	person.c = 'c'.  -> gives error

Requirements:

- To have attributes named in `__slots__` to actually be stored in slots instead of a `__dict__`, a class must inherit from object.
- To prevent the creation of a `__dict__`, you must inherit from object and all classes in the inheritance must declare `__slots__` and none of them can have a `__dict__` entry.

