=== Keily ===
Contributors: templatesell
Author: templatesell
Author URI: https://templatesell.com/
Tags: block-patterns, block-styles, blog, custom-background, custom-colors, custom-logo, custom-menu, editor-style, full-site-editing, grid-layout, one-column, photography, portfolio, template-editing, threaded-comments, translation-ready, wide-blocks
Requires at least: 6.0
Tested up to: 7.1
Requires PHP: 7.4
Stable tag: 1.0.2
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

== Description ==

A WordPress Full Site Editing theme named Keily is designed to take full advantage of WordPress's Full Site Editing capabilities, providing users with extensive control over the entire website layout, design, and content. It enables users to customize and edit every aspect of their website, including headers, footers, sidebars, templates, and individual page elements, without the need for coding or advanced technical skills. The theme empowers users to create unique and visually stunning websites by offering a wide range of customizable blocks, templates, and styling options. With Keily, users can craft a personalized website that reflects their brand while ensuring a seamless and intuitive editing experience.

== Copyright ==

Keily WordPress Theme, (C) 2022 Template Sell.
Keily is distributed under the terms of the GNU GPL v2 or later.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.


== Font License ==
Montserrat font
License: SIL Open Font License, 1.1, https://opensource.org/licenses/OFL-1.1
Source: https://fonts.google.com/specimen/Montserrat

Work Sans font
License: SIL Open Font License, 1.1, https://opensource.org/licenses/OFL-1.1
Source: https://fonts.google.com/specimen/Work+Sans


= Images License =
== Hero and About ==
License: CC0 1.0 Universal (CC0 1.0) Credit Direct Media
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/business-woman-FPQIEQBMPA

== Projects ==
License: CC0 1.0 Universal (CC0 1.0) Credit Bango Renders
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/dog-sunglasses-ZVCXJVXL75

License: CC0 1.0 Universal (CC0 1.0)
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/volcano-mountain-AUACFKUQ5L

License: CC0 1.0 Universal (CC0 1.0) Credit Bango Renders
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/golden-gate-JBREGHUFA4

License: CC0 1.0 Universal (CC0 1.0) Credit Bango Renders
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/camera-object-GJ8ZDV9GVE

License: CC0 1.0 Universal (CC0 1.0) Credit Bango Renders
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/color-ink-XZRMQHLJBC

License: CC0 1.0 Universal (CC0 1.0) Credit Pxhere
License URL: https://pxhere.com/en/license
Source: https://pxhere.com/en/photo/1588175

== Testimonial ==
License: CC0 1.0 Universal (CC0 1.0) Credit Pxhere
License URL: https://pxhere.com/en/license
Source: https://pxhere.com/en/photo/1588175

License: CC0 1.0 Universal (CC0 1.0) Credit Kristin Hardwick
License URL: https://stocksnap.io/license
Source: https://stocksnap.io/photo/young-man-CACAIXFZ2V

== Changelog ==
= 1.0.2 - August 24 2026 =

Fixed
* Nine of the theme's ten block styles were never registered. keily_register_block_styles() built three arrays and assigned each over the last instead of merging them, so only the final group - a single core/post-terms style - ever reached register_block_style(). core/button and core/list had none at all, in a theme tagged "block-styles". Eight of the ten also had no CSS behind them, which would have made them menu entries that changed nothing; they are implemented now
* Every visible string in every pattern was written as esc_html( 'text', 'keily' ). esc_html() takes one argument and does no translation - it is a WordPress function rather than a PHP internal, so the extra argument was silently discarded and nothing errored. 117 strings across ten pattern files, none of them translatable, in a theme tagged "translation-ready". They use esc_html__() now
* The theme never set a font family at the root. styles.typography in theme.json carried a size and a line height and no fontFamily, and the family was applied block by block inside the patterns instead - so anything the patterns did not cover fell back to the browser default. The whole 404 message and its Search button, the search page's dates, excerpts and "Older Posts" pagination, and the "Skip to content" link on every page rendered in Times New Roman while Work Sans was being served for the text beside them
* The Contact pattern's right-hand column was a Contact Form 7 shortcode hardcoded to form ID 362, an ID from the theme author's own site. Without the plugin WordPress leaves the shortcode as text, so the front page - which composes this pattern - rendered the literal string [contact-form-7 id="362" title="Contact form 1"] inside a white card. With the plugin, form 362 still does not exist. It is built from core blocks now
* WorkSans-Light.woff2 was declared as the family's italic at weight 300, so a browser asking for italic loaded the Light file and rendered it upright, and weight 300 upright had no face at all
* Montserrat's two variable fonts declared a font-weight of "100 300 400 500 600 700 900". The descriptor takes a range - two values - so this one is invalid, is discarded, and the variable axis the files exist to provide went unused: every weight but 400 was synthesised by the browser
* Montserrat was declared with no fallback stack
* The link colour inside post content and post terms, and the hover colour for every link in the theme, was #0693E3 - 3.34:1 against white, below the minimum for body text. It is #0B74C4 now, 4.87:1
* Link hover removed the underline, taking away the affordance at the moment a reader reaches for it. It keeps the underline and changes colour
* In the Blues style variation, button labels were #c8d6ef on #4B6CB7 - 3.47:1. The blue is deeper now and the label measures 4.55:1
* Three typos in shipped pattern text: "QA Servives", "User Eexperience", and a support address at gmial.com - a real typosquatting domain, now the reserved example.com
* Dropped add_theme_support() for experimental-link-color and custom-units, both long removed from WordPress
* wp_get_theme( 'keily' ) asked for that directory by name rather than for the active theme, so under a child theme the stylesheet version and the stylesheet could disagree

Accessibility
* The front page rendered with nine H1 elements. Eight of the ten patterns opened with an <h5> kicker followed by an <h1> section title, and front-page.html composes nine patterns in a row, so the heading order ran 1 2 5 5 5 5 5 5 1 2 6 2 6 2 6 5 1 6 5 ... Section titles are H2 now and the kickers are paragraphs, which is what they are
* Six decorative step counters - "01" through "06" - were marked up as headings, putting them in the document outline and in the heading list a screen-reader user navigates by. So were three counter captions and three counter figures
* The Experience and Project patterns had their hierarchy inverted: the date range, the employer and the category tag carried the heading, and the job title and project title were nested beneath them. The titles are the headings now
* Four personal-detail labels in the Banner pattern were headings; three of them were wrapped in <strong><strong>

Other
* Corrected the readme: the Theme URI and Author headers had collapsed onto one line, leaving no Author header at all; the tag list appeared twice; the stable tag and version said 1.0.0 where the theme was on 1.0.1; and the copyright section said the theme is distributed under the terms of Template Sell rather than the GPL
* Added languages/keily.pot
* Tested up to WordPress 7.1

= 1.0.1 August 14 2023 =
* Fixed reviewer issues.

= 1.0.0 August 09 2023 =
* Initial public release.




