phpVMS module to extract monthly flight statistics for individual pilots from your phpVMS based virtual airline.

This module was orginaly created by:
simpilot - David Clark
www.simpilotgroup.com
www.david-clark.net

And modified by:
Infinite Airlines - Artem Frolov
www.infinite-airlines.org
www.artemfrolov.co.uk
af@maksis.by

-----
Install:
-----
-Download the attached package.
-unzip the package and place the files as structured in your root phpVMS install.

-your structure should be:
root
  core
    common
      TopPilotData.class.php
    modules
      TopPilot
        TopPilot.php
    templates
      tp_index.tpl
      tp_previous.tpl

-use the top_flights.sql file to create the table needed in your sql database using phpmyadmin or similar.
-after the initial install point your browser to yoursite/index.php/TopPilot/refresh_pilot_stats one time. This will populate the database table with any data available.
-to view the main TopPilot index create a link yoursite/index.php/TopPilot
-everytime a pirep is filed the module will recalculate the pilot stats and update the database

There are three main display functions within the TopPilotData class that you can configure to use in various parts of your site.

Flights flown - TopPilotData::top_pilot_flights($month, $year, 5)
Hours flown -  TopPilotData::top_pilot_hours($month, $year, 5)
Miles flown - TopPilotData::top_pilot_miles($month, $year, 5)

$month should be the two digit month id of the month you want data from, ie 06 = June
$year is the four digit year you are pulling - ie 2010
5 can be changed to how many records you want returned.

Excluding PIREPS that are not accepted yet.

TopPilot.php line 52.

Uncomment the trailing section and the module will not include unapproved PIREPS. Doing this will cause the module not to display any newly accepted PIREPS in the TopPilot data listings until after another PIREP is filed  although you can refresh the stats at anytime using /index.php/TopPilot/refresh_pilot_stats

-----
Also, if the database prefix that you are using is not "phpvms_", then change in toppilot.sql first line to 
CREATE TABLE IF NOT EXISTS `phpvms_top_flights` (
-----

Although this script carries no limits of use a link back to www.simpilotgroup.com and www.infinite-airlines.org would be greatly appreciated!


