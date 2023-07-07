
```python
sum(iterable, attribute=None, start=0)
```
Returns the sum of a sequence of numbers plus the value of parameter ‘start’ (which defaults to 0). When the sequence is empty it returns start.

It is also possible to sum up only certain attributes:

```
Total: {{ items|sum(attribute='price') }}

```
** The attribute parameter was added to allow summing up over attributes. Also the start parameter was moved on to the right.
