# Python and JavaScript 

### 1. Fetching Session Data
```
rappe.ui.form.on('Student', {
    refresh: function(frm) {
        frm.add_custom_button('View Session Data', function() {
            frappe.call({
                method: 'frappe.popup.doctype.student.student.get_session_data',
                callback: function(response) {
                    var session_data = response.message;
                    frappe.msgprint('<pre>' + JSON.stringify(session_data, null, 2) + '</pre>');
                }
            });
        });
    }
});

@frappe.whitelist()
def get_session_data():
session_data = frappe.session.data
return session_data

@frappe.whitelist()
def get_dob():
dob = frappe.session.data.get("date_of_birth")
return dob
```

### 2.Fetching Values from One DocType to Another
```
frappe.ui.form.on('Av production form', {
	ifsc_code: function(frm) {
    	frappe.call({
			method: "frappe.production_houses.doctype.av_production_form.api.get_bank",
			args: {
				doctype:"Bank Details IFSC av",
				name:frm.doc.ifsc_code,
			},
			
			callback: (r) => {
				if(r.message) {
					frm.set_value('micr',r.message.micr)
					frm.set_value('branch_address',r.message.branch_address)
					frm.set_value('bank_name', r.message.bank_name)
					frm.set_value('branch',r.message.branch)
					
				}
			}
		});
		
    },
    
});

@frappe.whitelist()
def get_bank(doctype, name=None ,filters=None, parent=None):
        
		if frappe.is_table(doctype):
			check_parent_permission(parent, doctype)
				
		if filters and not name:
			name = frappe.db.get_value(doctype, json.loads(filters))
			if not name:
				frappe.throw(_("No document found for given filters"))

		doc = frappe.get_doc(doctype, name)
		if not doc.has_permission("read"):
			raise frappe.PermissionError
		return frappe.get_doc(doctype, name).as_dict()
```
