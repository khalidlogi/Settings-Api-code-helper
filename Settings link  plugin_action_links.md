setting link under plugin name in plugins page.
```php
add_filter('plugin_action_links_kh-wpform/main.php', array($this, 'misha_settings_link'), 10, 2);


  function misha_settings_link($links_array)
    {
        $Settings = '<a href="admin.php?page=khwplist.php">Settings DB</a>';
        array_unshift($links_array, $Settings);
        return $links_array;
    }

```
<img width="446" alt="image" src="https://github.com/khalidlogi/Settings-Api-code-helper/assets/20868071/3c016a72-a149-4be5-af2e-32683811c38b">
