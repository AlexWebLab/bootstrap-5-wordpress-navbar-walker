# Bootstrap 5 WordPress navbar walker
[bootstrap-5-wordpress-navbar-walker](https://github.com/AlexWebLab/bootstrap-5-wordpress-navbar-walker)
## How to use:
1. Copy and paste the [bootstrap_5_wp_nav_menu_walker](https://github.com/AlexWebLab/bootstrap-5-wordpress-navbar-walker/blob/main/functions.php) class into the functions.php file of your theme;
2. Register a new menu by adding the follow code into the functions.php file of your theme:
```php
register_nav_menu('main-menu', 'Main menu');
```
3. Add the following html code in your header.php file or wherever you want to place your menu:
```html
<nav class="navbar navbar-expand-md navbar-light bg-light">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#main-menu" aria-controls="main-menu" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        
        <div class="collapse navbar-collapse" id="main-menu">
            <?php
            wp_nav_menu(array(
                'theme_location' => 'main-menu',
                'container' => false,
                'menu_class' => '',
                'fallback_cb' => '__return_false',
                'items_wrap' => '<ul id="%1$s" class="navbar-nav me-auto mb-2 mb-md-0 %2$s">%3$s</ul>',
                'depth' => 2,
                'walker' => new bootstrap_5_wp_nav_menu_walker()
            ));
            ?>
        </div>
    </div>
</nav>
```
