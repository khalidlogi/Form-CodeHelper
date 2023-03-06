## goreign key
FOREIGN KEY  (customer_codes_id) REFERENCES $table_name(id)
https://stackoverflow.com/questions/34707946

## Tests 
### Verify if insert query is valid 

```php
if($wpdb->insert('customers',array(.....)) === FALSE ) {
echo Error 
} 
Else {
Echo $wpdb->insert_id;  //show last id inserted 
} 
```

## Check if already exist before insertion

```php
$dmtable = 'repairman';
                $my_part_ID = (bool)$wpdb->get_var(
                    $wpdb->prepare(
                        "SELECT COUNT(email) FROM repairman
                                WHERE email = %s AND name = %s LIMIT 1",
                        $email, $name
                    )
                ); echo $wpdb->last_query ;echo"<br>"; echo $wpdb->last_error;
               
                if ($my_part_ID){
                    echo"already exist";
                }
                else{
                    global $wpdb;
                    echo"New entry found";
//                    $wpdb->insert('sb_trip_rate',array('trip'=>$trip, 'rating'=>$rating, 'r_name'=>$name,'r_email'=>$email, 'title'=>$title, 'review'=>$review,),array('%s', '%s', '%s', '%s','%s','%s'));
                    }
                    ```
                    
Or 
```php
<?php

if(!empty($_POST['client_name']) && isset($_POST['client_name'])) {
    $client_name = $_POST['client_name'];
}

//global $wpdb;
if(isset($client_name) && !empty($client_name)){
    $query = $wpdb->get_row("SELECT * FROM `wp_clients` WHERE `client_name`='".$client_name."'");

    if (!empty($query->client_id)) {
        echo 'Client already exists';
    }else{
        if($client_name != 'None'){
            $sql = $wpdb->prepare("INSERT INTO `wp_clients`(`client_name`) VALUES ('".$client_name."')");

            if ($wpdb->query($sql)) {
                echo "New client created successfully";
            } else {
                echo "Error: " . $sql . "<br>" . $wpdb->error;
            }
        }else {
            echo 'Please enter the client name';    
        }
    }
    
    ```
}
?>
