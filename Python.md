# Python

### 1. By Script Naming Rule 
- Need to select "By Script" in Naming Rule and fill "autoname" in "Auto Name"
```
from frappe.model.naming import make_autoname

class ClassName(Document):

    def autoname(self):
        prefix = "SUP-"
        project = self.project
        naming_series = f"{prefix}{project}-.#####"
        self.name = make_autoname(naming_series)
```
