```python
from jinja2 import Environment, FileSystemLoader

# Create the Jinja2 environment and configure it
env = Environment(loader=FileSystemLoader('.'))
template = env.get_template('macros_example.html')

# Render the template with user name
rendered_template = template.render(user_name='Alice')

# Output the rendered template
print(rendered_template)
```

