# Acceptance Testing

For running acceptance tests, you will need [Selenium](http://www.seleniumhq.org/) installed.

    # Reset the database

    php artisan migrate:reset
    php artisan migrate --seed

    # Run the server
    # (In another console)

    php artisan serve

    # Run Selenium
    # (In another console)
    # (Replace the path and version you have)

    java -jar /usr/local/bin/selenium-server-standalone-2.47.1.jar

    # Run Tests

    phpunit tests/acceptance
