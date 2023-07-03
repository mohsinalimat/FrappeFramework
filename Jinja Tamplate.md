# Jinja Tanplate 

### 1. Fetching Data from Another DocType
```
{% set value = frappe.db.get_value("[doctype]", "[name]", "[fieldname]")%} {{value}}
```
### 2. Fetching Data from Linked Field DocType
```
{% set value = frappe.get_all('linked_field_doctype_name', filters = {'linked_field': doc.linked_field}, fields=['fild_name']) %} {{value[0]['fild_name']}}
```
### 3. Fetching Data from Child Table
```
{% set  value = frappe.get_all('DocType Name', filters = {'name': doc.name}, fields  = ['doctype_table_field_name.child_table_field_name'])%} {{value[0]['child_table_field_name']}}
```
