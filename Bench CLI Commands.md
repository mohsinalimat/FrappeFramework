# Bench CLI Commands

### 1. Create New App
```
bench new-app <app_name>
```
### 2. Set App on Developer Mode
```
bench --site <site-name> set-config developer_mode 1
```
### 3. Create New Site
```
bench new-site <site_name> --db-type <db_name>
```
### 4. Install App on Site
```
bench --site <site_name> install-app <app_name>
```
### 5. Use a Particular Site
```
bench use <site_name>
```
### 6. Open a Python Console for the Specific Site
```
bench --site <site_name> console
```
### 7. Set Site on Develoiper Mode
```
bench --site <site_name> --force set-config developer_mode 1
```

# Important Terminal Commands

### A. Change Ownership of frappe-bench Directory and its Contents to Root User
```
sudo chown -R <root_user_name> frappe-bench
```
### B. Using Mariadb CLI
```
source env/bin/activate
bench mariadb
```
