

### nonce 
```php
<input type="hidden" name="nonce" value="<?php echo wp_create_nonce('form-nonce') ?>" />     
$nonce = $_POST['nonce'];
        if (!wp_verify_nonce($nonce, 'form-nonce')) {
            wp_die('Security check');
        }
```

### use sanitize_email() to try to fix any invalid email 
$user_email = sanitize_email ( $user_email ); 
$valid_email = is_email ( $user_email ); 
if ( ! $valid_email ) echo 'invalid email<br />' ;
 else 
echo 'valid email: ' . $user_email ;

Sanitize meta box 
$v = $_post[] 
$v = stripslashes(strip_tags($v)) 

//test if empty
    $name =  isset($_POST['myname']) ? trim($_POST['myname']) : 0;
    if( empty( $name ) ) $error = 'Please insert a user name<br>';
    
    
    
    /////////////////////////////////////////////////////////////
    // 3.2 Clean_text
function clean_text($clean) {
    $trimmed = trim($clean);
    $stripped = stripslashes($clean);
    $special = htmlspecialchars($clean);
    return $clean;
}
    
// 3.3 Submission form
if(isset($_POST['submit'])) {
    $success = true;

    if(empty($_POST['prenom']) OR empty($_POST['nom']) OR empty($_POST['email'])) {
        $error = '<p>Veuillez réessayer</p>';
    } else {
        $fname = clean_text($_POST['prenom']);
        $lname = clean_text($_POST['nom']);
        $email = clean_text($_POST['email']);
        }
 
