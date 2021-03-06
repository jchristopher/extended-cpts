[![Build Status](https://travis-ci.org/johnbillion/extended-cpts.svg?branch=master)](https://travis-ci.org/johnbillion/extended-cpts)
[![Stable Release](https://img.shields.io/packagist/v/johnbillion/extended-cpts.svg)](https://packagist.org/packages/johnbillion/extended-cpts)
[![License](https://img.shields.io/badge/license-GPL--2.0%2B-red.svg)](https://github.com/johnbillion/extended-cpts/blob/master/LICENSE)

# Extended CPTs #

Extended CPTs is a library which provides extended functionality to WordPress custom post types, allowing developers to quickly build post types without having to write the same code again and again.

See also: [Extended Taxonomies](https://github.com/johnbillion/extended-taxos).

## Improved defaults ##

 * Automatically generated labels and post updated messages
 * Public post type with admin UI enabled
 * Hierarchical with `page` capability type
 * Support post thumbnails
 * Optimal admin menu placement
 * Remove `with_front` from rewrite rules

## Extended admin features ##

 * Ridiculously easy custom columns on the post type listing screen:
    * Columns for post meta, taxonomy terms, featured images, post fields, [Posts 2 Posts](https://wordpress.org/plugins/posts-to-posts/) connections, and callback functions
    * Sortable columns for post meta, taxonomy terms, and post fields
    * User capability restrictions
    * Default sort column and sort order
 * Filter controls on the post type listing screen for filtering by post meta fields and taxonomy terms
 * Override the 'Featured Image' and 'Enter title here' text
 * Add the post type to the 'At a Glance' section on the dashboard
 * Add the post type archive link to the nav menus screen

## Extended front-end features ##

 * Easily specify custom permalink structures
     * For example `reviews/%year%/%month%/%review%/`
     * Supports all relevant rewrite tags including dates and custom taxonomies
     * Automatic integration with the [Rewrite Rule Testing](https://wordpress.org/plugins/rewrite-testing/) plugin
 * Easily specify public query vars for filtering by post meta fields
 * Override public or private query variables such as `posts_per_page`, `orderby`, `order` and `nopaging`
 * Add the post type to the site's main RSS feed

## Usage ##

Need a simple post type with no frills? You can register a post type with a single parameter:

```php
register_extended_post_type( 'article' );
```

Try it. You'll have a hierarchical public post type with an admin UI, and all the labels and post updated messages will be automatically generated. Or for a bit more functionality:

```php
register_extended_post_type( 'story', array(

	# Add the post type to the site's main RSS feed:
	'show_in_feed' => true,

	# Show all posts on the post type archive:
	'archive' => array(
		'nopaging' => true
	),

	# Add some custom columns to the admin screen:
	'admin_cols' => array(
		'featured_image' => array(
			'title'          => 'Illustration',
			'featured_image' => 'thumbnail'
		),
		'published' => array(
			'title'       => 'Published',
			'meta_key'    => 'published_date',
			'date_format' => 'd/m/Y'
		),
		'genre' => array(
			'taxonomy' => 'genre'
		)
	),

	# Add a dropdown filter to the admin screen:
	'admin_filters' => array(
		'genre' => array(
			'taxonomy' => 'genre'
		)
	)

), array(

	# Override the base names used for labels:
	'singular' => 'Story',
	'plural'   => 'Stories',
	'slug'     => 'stories'

) );
```

Bam, we have a 'Stories' post type, with correctly generated labels and post updated messages, three custom columns in the admin area (two of which are sortable), stories added to the main RSS feed, and all stories displayed on the post type archive.

There's quite a bit more you can do. See the wiki for more examples.

## License: GPLv2 or later ##

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
