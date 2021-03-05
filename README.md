# Bootstrap 5 WordPress navbar walker menu
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
### v1.3.0 Added support for dropdown menu (responsive) alignment: https://getbootstrap.com/docs/5.0/components/dropdowns/#menu-alignment

**Here is how it works**:
- From _Appearance -> Menus_ page of WordPress, check the _CSS Classes_ checkbox under _Screen Options_;
- Add a _Custom Link_ with "#" in the URL field (this would be the parent of your dropdown);
- On the _CSS Classes_ field add any of the following alignment classes: 'dropdown-menu-start', 'dropdown-menu-end', 'dropdown-menu-sm-start', 'dropdown-menu-sm-end', 'dropdown-menu-md-start', 'dropdown-menu-md-end', 'dropdown-menu-lg-start', 'dropdown-menu-lg-end', 'dropdown-menu-xl-start', 'dropdown-menu-xl-end', 'dropdown-menu-xxl-start', 'dropdown-menu-xxl-end';
- If any of the mentioned above class is detected, then they will automatically copied into the _ul.dropdown-menu_ element following the Bootstrap 5 structure;
- Any other class that is not related to the dropdown menu alignment will stay where it is.
