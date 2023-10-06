// Current plugin version
define('MYPLUGIN_VERSION', '1.0.0'); 

class MyPlugin {

  public function __construct() {

    add_action('admin_notices', [$this, 'check_version']);

  }

  public function check_version() {

    $remote_version = $this->get_remote_version();

    if( version_compare(MYPLUGIN_VERSION, $remote_version, '<') ) {

      $this->display_update_notice($remote_version);

    }

  }

  private function get_remote_version() {

    // Make API request
    $response = wp_remote_get('https://api.example.com/plugins/myplugin');

    // Decode JSON response
    $data = json_decode($response['body']);

    return $data->version;

  }

  private function display_update_notice($remote_version) {

    $message = sprintf(
       'A new version (%s) of My Plugin is available!', 
       $remote_version
     );

     echo '<div class="notice notice-warning">' . $message . '</div>';

  }

}

new MyPlugin();
