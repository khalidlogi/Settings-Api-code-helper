```php
public function rfq_create_settings_submenu() {
        //create new top-level menu
        // This page will be under "Settings"
        add_options_page(
                'Request For Quote Settings', 
                'RFQ Settings', 
                'manage_options', 
                'rfq-setting-admin', 
                array($this, 'create_options_page')
        );
    }

    public function fme_rfq_settings_submenu() {
		
		add_submenu_page(
			'manage-quotes',
			'Settings Request for Quote Plugin Menu', 
			'Settings', 
			'manage_options', 
			'rfq-setting-admin', 
			array($this, 'create_options_page')
        );
	}
```

The functions rfq_create_settings_submenu() and fme_rfq_settings_submenu() are used to create a submenu under the "Settings" menu in WordPress. 
The rfq_create_settings_submenu() function creates a top-level menu, while the fme_rfq_settings_submenu() 
function creates a submenu under the "Manage Quotes" menu. Both functions take the same arguments:

$page_title: The title of the menu page.
$menu_title: The title that will be displayed in the menu.
$capability: The capability required to access the menu page.
$menu_slug: The slug used to identify the menu page.
$callback: The function that will be called when the menu page is loaded.
The rfq_create_settings_submenu() function uses the add_options_page() function to create a top-level menu. The add_submenu_page() function is used to create a submenu under the "Manage Quotes" menu.

The callback argument for both functions is used to specify the function that will be called when the menu page is loaded. This function should contain the code that will be used to display the settings page.

Here is an example of how to use the rfq_create_settings_submenu() function to create a settings page:

```php
function rfq_create_settings_submenu() {

    // Set the page title, menu title, capability, menu slug, and callback.
    $page_title = 'Request For Quote Settings';
    $menu_title = 'RFQ Settings';
    $capability = 'manage_options';
    $menu_slug = 'rfq-setting-admin';
    $callback = 'my_rfq_settings_page';

    // Create the menu page.
    add_options_page(
        $page_title,
        $menu_title,
        $capability,
        $menu_slug,
        $callback
    );
}

```
The my_rfq_settings_page() function is the callback function that will be called when the settings page is loaded. This function should contain the code that will be used to display the settings page.

Here is an example of how to create a settings page:

function my_rfq_settings_page() {

Code snippet
// Get the current settings.
$settings = get_option('rfq_settings');

// Display the settings form.
?>
<form action="options.php" method="post">
    <?php settings_fields('rfq_settings'); ?>
    <h1>Request For Quote Settings</h1>
    <p>This is the settings page for the Request For Quote plugin.</p>
    <p>
        <label for="rfq_enabled">Enable Request For Quote</label>
        <input type="checkbox" name="rfq_enabled" id="rfq_enabled" value="1" <?php checked($settings['enabled'], 1); ?> />
    </p>
    <p>
        <label for="rfq_email_address">Email Address</label>
        <input type="text" name="rfq_email_address" id="rfq_email_address" value="<?php echo esc_attr($settings['email_address']); ?>" />
    </p>
    <?php submit_button(); ?>
</form>
<?php
