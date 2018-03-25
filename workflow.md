How to import
=============

## Getting started

### Creating an import account

 * OSM best practices require that you [do not use your normal OSM account for the imports](http://wiki.openstreetmap.org/wiki/Import/Guidelines#Use_a_dedicated_user_account). Create a new account for this purpose. 
 Usually, it's your existing OSM username followed by `_imports` (e.g. `tekim_imports or tekim_drcog)`.
 Post your import account username in this [ticket](https://github.com/geochasm/DRCOG_Buildings/issues/1).

### Getting familiar with JOSM

To contribute to this project, you need to use the JOSM editor.  Here are some resources to get you started:
 * LearnOSM - http://learnosm.org/en/josm/
 * Mapbox Mapping wiki - https://www.mapbox.com/blog/making-the-most-josm/

### Check out a task on the tasking manager

 * Tasks will be available on **[http://tasking-manager.mapsarecool.com/project/2](http://tasking-manager.mapsarecool.com/project/2)**.
 * Priority: Pending review of import tasks by DRCOG import team.

## Import workflow

### Selecting a task in the Tasking Manager

 * Choose which area you want to work on from **[http://tasking-manager.mapsarecool.com/project/2](http://tasking-manager.mapsarecool.com/project/2)** Navigate to the **Contribute** tab and click **Start Mapping**.
 
![download_osm](https://github.com/geochasm/DRCOG_Buildings/blob/master/images/osmtm_proj_pg.PNG)
 
 * It is recommended that you enable remote control in JOSM and use the **Edit with JOSM** button in the tasking manager.

 * This should automatically load JOSM with:
   * The task boundary: if this doesn't load you can download the .gpx file from the task screen that can be loaded into JOSM, this is not necessary as the DRCOG building data should be trimmed to the task, but may make navigating the OSM data easier.
   * The DRCOG imagery: please use this imagery for checking alignment of data. If the imagery does not automatically load; add *(this/tbd)* TMS link to JOSM.
   * The OpenStreetMap data layer: this is the layer you will need to compare with and merge DRCOG data into. If the data layer does not automatically download, or you want to bring in a bit more buffer around your task use the manual download function in JOSM.
   * The OSM Changeset Comment: You won't notice this until you go to Save/Upload the data to OpenStreetMap. However, make sure your changeset/save comment has some text in this format: "DRCOG Planimetrics Import #DRCOGPlanimetrics #[City or County][Feature] https://wiki.openstreetmap.org/wiki/Denver_Planimetrics_Import" so we can track progress and reach out if something goes wrong. Not the Tasking Manager comment, but in JOSM when you save.
 
### Getting the DRCOG Building Data for your Task

 * Get the `.osm` file you will import by clicking the link in the **Extra Instructions**.  This will download an OSM data file for the task in your browser's 'Downloads' directory.
 Open this .osm data file in JOSM
 
 * At this point at least three (maybe 4) layers should be in JOSM:
   * one with the imported data (`buildings-addresses####.osm`)
   * one with current OSM data (`Data Layer 1`)
   * you hopefully also have the imagery and (optional) task boundary 
   * if you are missing any of these layers, please go back a step

 ![download_import](https://cloud.githubusercontent.com/assets/353700/14101326/6f64d14e-f5b1-11e5-9748-8c56995a256d.gif)

### Reviewing the data before uploading

 * Review both data layers for possible conflicts.
 * Examine tags in both data sets to see if there are any conflicts.
 * If there are any problems you don't know how to deal with, do not proceed. Instead, flag the `.osm` file for a more advanced user to look at. 
 (Use github [issues](https://github.com/geochasm/DRCOG_Buildings/issues) to flag concerns). Then unlock your task on the tasking manager and pick a new area to work on, leaving a comment there as well so the next mapper is aware.

* Preserve the work of previous mappers wherever possible.  If existing buildings in OSM are of higher quality:
  * Copy the tags from the import layer version.
  * Switch to the OSM layer.
  * Select the building, paste the tags.
  * Delete the building from the import layer.

* If the imported data are of higher quality:
  * Select both buildings and use the **Replace geometry** tool
  * Delete the building from the import layer. 
 
 ![replace](https://cloud.githubusercontent.com/assets/353700/12942518/ddba87a4-d001-11e5-9441-2561f67b45bc.gif) 

 * Once you have only those DRCOG buildings that need to be added to OSM left in the import layer; merge the import layer into the OSM Data Layer. 

* Right-click the layers and click Merge.
 ![screen shot 2016-04-02 at 3 51 12 pm](https://cloud.githubusercontent.com/assets/3673236/14229616/ad4ebafe-f8ec-11e5-9ae0-444dcf540264.png)
* Merge onto the `osm data` layer.

 * Run JOSM Validator, and if there are errors, fix them. 

![validator](https://cloud.githubusercontent.com/assets/353700/12942520/ddc572f4-d001-11e5-8cf6-399511cd47fa.gif) 

### Finally, upload it

* Select the OSM Data Layer.

* Click the Upload button, the green up arrow button.

![screen shot 2016-04-02 at 3 53 02 pm](https://cloud.githubusercontent.com/assets/3673236/14229617/ad64e298-f8ec-11e5-9693-ba3f3a0e2085.png)
* If you see a "Suspicious data found" warning, double check that none need to be addressed, then click "Continue upload"

![screen shot 2016-04-02 at 3 53 11 pm](https://cloud.githubusercontent.com/assets/3673236/14229619/ad72b6c0-f8ec-11e5-97b6-66b43f1c2937.png)

* As discussed above, use a **changeset comment** such as (hopefully preloaded via the tasking manager): `DRCOG Planimetrics Import #DRCOGPlanimetrics #[City or County][Feature] https://wiki.openstreetmap.org/wiki/Denver_Planimetrics_Import ` 
 and **source**: `Denver Regional Council of Governments https://data.drcog.org/dataset/building-roofprints-2014`.

![screen shot 2016-04-02 at 3 53 17 pm](https://cloud.githubusercontent.com/assets/3673236/14229620/ad73128c-f8ec-11e5-9e2f-44d272bd6403.png)

If you see an Authorization window asking you to log in to OpenStreetMap, log in and remember to use your `_import` username.

* Go back to the Tasking Manager and click **Mark task as done**. If necessary, leave a comment so if another mapper validates your edits they are aware (i.e. one building from satellite imagery not in import data; left alone).

## What to watch out for

### Validate the import with your eyes before uploading!

 * Run the [JOSM validator](http://wiki.openstreetmap.org/wiki/JOSM/Validator). Check for any errors it detects.
 * Check for small building parts that should be joined to the main building. We've already found a few examples of these in the data (see [issue #19](https://github.com/osmlab/labuildings/issues/19)), so make sure you keep an eye out for these.  To join small parts, select both polygons and select **Tools > Join overlapping Area**.
 
 ![screen shot 2016-04-04 at 2 38 36 pm](https://cloud.githubusercontent.com/assets/695934/14264162/74ab59f4-fa73-11e5-8c4e-896c7fa2c2e4.png)

If it's a small sliver, it makes sense that the "proper" data is on the larger object. Delete all the tags on the sliver and join the two objects.

If it's larger, like a strip mall split into pieces, then do:

- `lacounty:ain` -> ALL
- `lacount:bld_id` -> ALL
- `start_date` -> None if multiple or the one option if there's only one
- `height` -> largest number
- `ele` -> largest number 
- `building:units` -> none if different

![screen shot 2016-04-04 at 2 38 44 pm](https://cloud.githubusercontent.com/assets/695934/14264157/6c9f23ee-fa73-11e5-8744-e49d7e179003.png)

 * Inspect everything else with a critical eye! Don't trust that the validator or FIXME tags will catch everything. There may be other bugs that only you can detect. Use your human smarts!
 
### Conflating with existing data
 * Look for any overlaps with existing buildings. Existing buildings in OSM are probably _more_ up-to-date than our imported data. Do not assume the imported data is better, mostly likely it is worse! 
 * Carefully combine the import data with the existing OSM data. If you aren't sure about some tags, ask someone! Especially ask the original mapper! 
 
### How to ground-truth the data
 * Up-to-date aerial imagery... try several sources.
 * See if the street is on [Mapillary](http://www.mapillary.com/map/search).
 * Go out and check it out yourself! Take a field trip!
 * **DO NOT USE GOOGLE MAPS OR GOOGLE STREET VIEW**.

### Identifying new buildings with imported and existing data
* The imagery was purchased by DRCOG. This is the same imagery used as a reference for tracing the imported data. In some areas, the default imagery sources are more updated than the imported data and we can use it to identify newer buildings not found in the imported and/or existing data.
* Newer building should be identified and flagged. Tag the building with `fixme` and add a note: `Appears in satelite imagery.`
![screen shot 2016-04-02 at 3 19 31 pm](https://cloud.githubusercontent.com/assets/3673236/14229396/ab9f392c-f8e7-11e5-80ca-635b97332bd8.png) We can verify this with more recent planimetric data.
* Likewise, buildings maybe demolished and does not exist anymore, delete them.
 
## Communicate communicate communicate!

### How to ask for help

 * Create [issues](http://github.com/osmlab/labuildings/issues) on this github repo.
 * Ask questions on the OSM #Colorado [Slack Channel](https://osmus-slack.herokuapp.com/).
 * Contact [DRCOG](https://drcog.org/) or [OSM-Colorado](https://www.meetup.com/OSM-Colorado/).

### How to share your progress

 * Make sure you upload your changes with the recommended comment and mark your task on the tasking manager as complete. Leave a comment there as well if it would be helpful (i.e. a few buildings were difficult to tell which dataset was more accurate, etc.).

### How to communicate with other mappers

 * JOSM [GeoChat](http://wiki.openstreetmap.org/wiki/JOSM/Plugins/GeoChat) feature.
 * Come to one of the next OSM related [meetup groups](https://www.meetup.com/OSM-Colorado/pages/24662291/Colorado_Groups/) in Colorado.
 * Befriend other mappers on openstreetmap.org
 
### Thanks to the LA Buildings Import
* This import workflow guide is based on the guide published by the Los Angeles building import at **[https://github.com/osmlab/labuildings/blob/master/IMPORTING.md](https://github.com/osmlab/labuildings/blob/master/IMPORTING.md)**.
 
