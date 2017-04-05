# Template Generation Tool

<p>Created a `tinker.php` file here (instafunnels.co/app/admin/views/besma/tinker.php) that takes care of 
theme and template insertion automatically. This tool allows the admin to upload templates with ease, without being
too concerned about conflicting files or missing database entries.</p>

# Re-created tables

<p>`Auto Incrementation` was bugged on some of the tables in the database. I re-created them
with the same blueprint to avoid conflict, and the A_I can easily be reset now, as opposed to before.</p>


# Code snippet for updating HTML/CSS properly

<p>Before this fix, the `HTML/CSS` for given projects were being generated automatically from an unknown place, 
probably by the builder itself. 

However, now, after adding this snippet of code:

![Code](http://image.prntscr.com/image/a6fdde6af8884ba0b19488666309407c.png)


I've made the page re-set all of the required fields to the correct values, and there are no problems.</p>


# 'create_project'

<p>The previous image is only a snippet from the middleware-file that I made the application go through... here is the full code:


![Code](http://image.prntscr.com/image/82eb820c539c45cf9d79d79ab6f25d7a.png)

</p>


# Editing error

<p>For some reason... when you create a step in the <or>FUNNEL STEPS</bl> phase...

Like this:
![Code](http://image.prntscr.com/image/10aae3a93cd24005b6909e7cf143ca2f.png)

It gets put in the database, two tables (by reference of name), `funnelsteps` and `projects`:

![Code](http://image.prntscr.com/image/0124d30d259042ab95a74cf412d257e4.png)

But suppose the funnel name was mispelled and then edited (in the proper manner,) the application
would only update the name on one table, resulting in the `funnelsteps` table (the one the builder
coincidentally also uses) being unaware of this modification, which would result in the project
no longer being recognised in the builder...


![Code](http://image.prntscr.com/image/e3b4965debc74f58a64a8e9eabd03d7e.png)


With a fre changes to the custom <bl>ORM</bl> currently in place (funnel-steps line 1800~), that's now also taken care of, 
and when the funnel-step aka 'project' is edited, the edit is submitted to both departments.


</p>

# Other Minor fixes

* Certain bugs and missing sessions are now fixed
* Now Loading images from correct path
* Now Loading javscript/stylesheets from correct path
* Located `funnel-steps.tpl.php` & changed some code to make it work with the right database table.
* Changed Foreign Key Constraining issues
* Upon deleting a funnel-step, it gets deleted everywhere, including the auto-enerated thumbnail for it.
* Reduced the width in created-step GUI, post-theme-selection
* Correctly assign HTML/CSS to the pages
* Deleting a funnel now deletes it in `pages`, `projects`, `users_projects`, and `funnelsteps`



# Currently

* Creating an `Exit Popup Element`
