# Ajax use in Wordpress

### Debug
Make sure that you are sending the correct <strong>action name<strong> in your AJAX request. 
The action name should match the one used when registering your AJAX action in your PHP code (e.g., my_ajax_action).

In WordPress, the ajaxurl variable is automatically defined in the admin area. If you’re trying to use it on the front-end of your site, you’ll need to define it yourself. You can do this by adding the following code to your theme’s functions.php file:

add_action( 'wp_head', 'my_ajaxurl' );
function my_ajaxurl() {
   echo '<script type="text/javascript">
           var ajaxurl = "' . admin_url('admin-ajax.php') . '";
         </script>';
}
