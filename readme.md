<!-- DO NOT EDIT THIS FILE; it is auto-generated from readme.txt -->
# Prevent Concurrent Logins

Prevents users from staying logged into the same account from multiple places.

**Contributors:** [fjarrett](http://profiles.wordpress.org/fjarrett)  
**Tags:** [login](http://wordpress.org/plugins/tags/login), [users](http://wordpress.org/plugins/tags/users), [membership](http://wordpress.org/plugins/tags/membership), [security](http://wordpress.org/plugins/tags/security), [sessions](http://wordpress.org/plugins/tags/sessions)  
**Requires at least:** 4.1  
**Tested up to:** 4.1  
**Stable tag:** trunk (master)  
**License:** [GPLv2 or later](http://www.gnu.org/licenses/gpl-2.0.html)  

[![Build Status](https://travis-ci.org/fjarrett/prevent-concurrent-logins.png?branch=master)](https://travis-ci.org/fjarrett/prevent-concurrent-logins) 

## Description ##

**Did you find this plugin helpful? Please consider [writing a review](https://wordpress.org/support/view/plugin-reviews/prevent-concurrent-logins).**

* Deters members/subscribers from sharing their accounts with others
* Hardens security by destoying old sessions automatically
* Prompts old sessions to login again if they want to continue
* Ideal for membership sites and web applications

If for some reason you don't want to use a plugin to do this, you can also just add these functions and hooks to your theme: https://gist.github.com/fjarrett/0fa79273bd879f7ab6b3

**Development of this plugin is done [on GitHub](https://github.com/fjarrett/prevent-concurrent-logins). Pull requests welcome. Please see [issues reported](https://github.com/fjarrett/prevent-concurrent-logins/issues) there before going to the plugin forum.**

## Frequently Asked Questions ##

### Can I still allow concurrent logins for certain users? ###
Yes, you can do this by using the `pcl_prevent_concurrent_logins` filter:

```php
function fjarrett_pcl_bypass_admins( $user_id ) {
    $user = get_user_by( 'id', absint( $user_id ) );

    if ( ! empty( $user->roles[0] ) && 'administrator' === $user->roles[0] ) {
        return false;
    }

    return true;
}
add_filter( 'pcl_prevent_concurrent_logins', 'fjarrett_pcl_bypass_admins', 10, 1 );
```


## Changelog ##

### 0.1.1 - January 2, 2015 ###
* Added filter to allow certain users to have concurrent sessions when necessary

Props [fjarrett](https://profiles.wordpress.org/fjarrett/), [nutsandbolts](https://github.com/nutsandbolts)

### 0.1.0 - December 31, 2014 ###
* Initial release

Props [fjarrett](https://profiles.wordpress.org/fjarrett/)


