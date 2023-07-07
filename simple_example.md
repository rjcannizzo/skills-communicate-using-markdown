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

#### Environment
The Environment object in Jinja2 represents the runtime environment for rendering templates. It acts as a container that holds various configuration options and settings related to template loading, template rendering, and template customization.
#### Filesystemloader()
The FileSystemLoader class takes a directory path as an argument and looks for templates within that directory. When a template is requested, Jinja2 uses the FileSystemLoader to locate the template file based on its name and directory structure.

