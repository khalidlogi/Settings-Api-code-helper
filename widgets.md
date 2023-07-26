 ## Widgets : y can see them in from the Dashboard panel

```php

dd_action('wp_dashboard_setup', array($this, 'ip_add_dashboard_widgets'));


function ip_add_dashboard_widgets()
        {

            wp_add_dashboard_widget('ip_dashboard_widget', __('Your IP Address & Hostname', 'admin-ip-address'), array($this, 'ip__widget'));

        }

function ip__widget()
        {

            // admin ip address

            $admin_ip_address = $_SERVER['REMOTE_ADDR'];

            if (!$admin_ip_address)

                $admin_ip_address = 'unknown';


            // admin hostname

            $admin_hostname = @gethostbyaddr($admin_ip_address);

            if (!$admin_hostname or $admin_hostname == $admin_ip_address)

                $admin_hostname = 'Not known';


            // display information

            echo '<div style="display:table; width: 100%;">';

            echo '<div style="display:table-cell;"><big><strong>' . $admin_ip_address . '</strong></big></div>';


            if ($admin_hostname != 'unknown')

                echo '<div style="display:table-cell; text-align: right;"><small>(' . __('hostname', 'admin-ip-address') . ' : ' . $admin_hostname . ')</small></div>';

            echo "</div>\n\n";

            echo '<div class="box-ip"><hr> Your IP address is something you might rarely think about, it\'s important to know what your IP address is and when it changes. Your IP address is used to identify computers on the Internet. <hr> Want to know more about IP addresses, or to get the latest updates on this plugin, go to the "Show IP Info" using the menu on the left side. <hr>Show IP address. Latest version 1.6</div>';

        }
```
