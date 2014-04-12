---
layout: post
title: "WordPress Posts Sorted By a Menu"
comments: true
date: 2012-07-07 14:37
categories: WordPress, PHP
published: false
---

A WordPress menu (as created under *Appeareance -> Menus* in the admin interface) is a way of creating an *ordered* set of posts. WordPress uses this functionality out of the box to create navigation menus using [wp_nav_menu()](http://codex.wordpress.org/Function_Reference/wp_nav_menu) but other uses are possible too.

As an example, when creating an website for an artist, I might create an 'Artwork' custom post type and populate it with appropriate content. My client obviously wants to control which artworks are shown on the homepage and in what order. I think the cleanest way is to create a Menu

### Advantages

* You get all the Admin functionality for creating & updating the list from WordPress.
* There is a good chance the client already knows how to maniuplate WordPress menus. If not, there are a lot of resources online to help This probably won't be the case for your custom solution.

### Disadvantages

* WordPress does not provide a way to stop users creating nested menus in the Admin Interface. A nested menu will not work this case. The only way to work around this problem is by educating your client. This is kludgy and puts extra training burden on the client if they have new staff members etc.

# The Code

## Step 1

Register a new menu location in your theme using [register_nav_menu()](http://codex.wordpress.org/Template_Tags/register_nav_menu). This "Theme Location" will appear in the *Appearance  -> Menus* section of the WordPress Admin. You can create a new menu of artworks there and link it to this location just as you would with any other navigation menu.

{% codeblock Using register_nav_menu() to create a new menu location in your theme lang:php %}
<?php
  register_nav_menu('artworks', 'Homepage Artworks');
?>
{% endcodeblock %}

### Step 2

 Paste this code in your ```functions.php```

{% gist 2398047 %}

### Step 3
This is an example of how to use the query to create a page template:

{% codeblock A new page template using our query lang:php pt-art-home.php %}
<?php
/**
* Template Name: Artworks Homepage
*/
?>

<?php get_header(); ?>

<?php
  $allib_query = allib_get_posts_from_menu(array(
              'theme_location' => 'primary'
          ));

  if ($allib_query->have_posts()):
    while ($allib_query->have_posts() ): $allib_query->the_post();
      // All your usual post functions work here e.g.
      the_title();
      the_content();
    endwhile;
  endif;

  wp_reset_postdata();
?>

<?php get_sidebar(); ?>
<?php get_footer(); ?>
{% endcodeblock %}