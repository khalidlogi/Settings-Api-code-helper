### add setting link under the plugin name
```php
add_filter("plugin_action_links_wpretro/wpretro.php", array($this, 'add_settings_link'));

function add_settings_link($links)
	{
		$settings = esc_html__('Settings', 'wpretro');
		$links[] = '<a href="tools.php?page=wpretro">' . $settings . '</a>';
		return $links;
	}
  ```
  
