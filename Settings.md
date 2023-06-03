### add setting link under the plugin name
<img width="148" alt="image" src="https://user-images.githubusercontent.com/20868071/235437916-f96b57a9-e08e-4234-ad71-fa53dc5b280b.png">

```php
add_filter("plugin_action_links_wpretro/wpretro.php", array($this, 'add_settings_link'));

function add_settings_link($links)
	{
		$settings = esc_html__('Settings', 'wpretro');
		$links[] = '<a href="tools.php?page=wpretro">' . $settings . '</a>';
		return $links;
	}
  ```
https://codex.wordpress.org/images/7/7e/editing-settings-api-example.png
![editing-settings-api-example](https://github.com/khalidlogi/Settings-Api-code-helper/assets/20868071/5d1bb590-3a71-4849-b493-2431f866a1cc)
