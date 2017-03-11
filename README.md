[https://coinwink.com](https://coinwink.com)

# Coinwink

COINWINK is an automated web application for sending crypto-currency (Bitcoin, Ethereum...) price alerts via e-mail.

The application gets price and coin data from coinmarketcap.com API.

Stack: JavaScript, JQuery, PHP, MySQL database, minimal Wordpress backend and HTML5 Blank Theme.


## How it works?

The app doesn't use accounts. Anyone can create alert instantly. User will receive a unique ID that can be used to delete alerts. With the last deleted alert also the ID and e-mail address are deleted from the database. E-mails and IDs are deleted also when there are no active alerts left.


## How to launch COINWINK application?

First you need to install Wordpress and download [HTML5 Blank Wordpress Theme](http://html5blank.com/).

Then upload coinwink-html5-child-theme to your themes folder and activate it. Create new empty home page and set it to use Coinwink Template.

Upload create_db.php on your server, edit database login details and then open this file in your browser. This will create database tables.

Also upload backend.php and coin_list.php on your server.

backend.php is checking the current price agains existing alerts and sending e-mails when it is time to alert. It automatically deletes from the database e-mail addresses that no longer have active alerts. So no private data is kept in Coinwink database. It also gets coin data as JSON and submits it into the MySQL database. During the coinwink.com page load, the page takes this JSON from MySQL and presents as price information for each coin - this helps to avoid too many direct calls to the API. The "backend.php" script needs to run each few minutes. On the production version the cron for the scripts is set to */3 minutes. Keep in mind that coinmarketcap.com API updates each 5 minutes.

coin_list.php gets coin dada from coinmarketcap.com API, converts this data into a html string and puts it into a database for the "Coin to watch:" input field on the front end. Because coin list is not updating frequently, the cronjob for this file can be set to */12 hours.

For web spam protection the [Captcha](https://wordpress.org/plugins/captcha/) plugin is being used. In Wordpress Settings->Coinwink click Enable.
For filterable select the [Select2](https://select2.github.io/) is being used.