Jinja2 has its own syntax and expression language, which does not include the ability to directly use f-strings.

However, you can achieve a similar result by using Jinja2's built-in string formatting capabilities. In your example, if you want to add a dollar sign to the value of the `total` variable, you can use the `format()` method within the template expression. Here's an example:

```jinja2
{{ "${:.2f}".format(total) }}
```

In this example, the `"{:.2f}"` part formats the `total` variable as a floating-point number with two decimal places. Then, the dollar sign is prepended to the formatted value using the curly braces.

So, if `total` is a variable with a value of 10.5, the expression `{{ "${:.2f}".format(total) }}` will output "$10.50".

By using Jinja2's formatting capabilities, you can achieve similar results to f-strings within your templates, allowing you to format and manipulate values according to your needs.
