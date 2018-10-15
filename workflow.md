How to import
=============

## Getting started

### Creating an import account

 * OSM best practices require that you [do not use your normal OSM account for the imports](http://wiki.openstreetmap.org/wiki/Import/Guidelines#Use_a_dedicated_user_account). Create a new account for this purpose. 
 Usually, it's your existing OSM username followed by `_imports` (e.g. `tekim_imports or tekim_drcog)`.
 Post your import account username in this [ticket](https://github.com/geochasm/DRCOG_Buildings/issues/1).
 * **Remember** you should log into the OSM Tasking Manager (see below) with your 'imports' username but you will also need to use that same username from any data uploade from JOSM

### Getting familiar with JOSM

To contribute to this project, you need to use the JOSM editor.  Here are some resources to get you started:
 * LearnOSM - http://learnosm.org/en/josm/
 * Mapbox Mapping wiki - https://www.mapbox.com/blog/making-the-most-josm/

### Check out a task on the tasking manager

 * Tasks will be available on **[http://tasking-manager.mapsarecool.com](http://tasking-manager.mapsarecool.com)**.
 * Priority: Pending review of import tasks by DRCOG import team.

## Import workflow

### Selecting a task in the Tasking Manager

 * Go to [http://tasking-manager.mapsarecool.com](http://tasking-manager.mapsarecool.com)

 * You will see the main project screen shown below. This example is for the Idaho Springs area pilot project
 * You can review the general instructions by clicking the **Instructions** tab
 * If you are ready to start mapping click on the **Start contributing** button from the Instructions tab or click the **Contribute** tab.
 ![download_osm](https://github.com/geochasm/DRCOG_Buildings/blob/master/images/proj_descr_screen.png)
 
 * On the **Contribute** tab select a specific task from the map or click the **Take a task at random** button or click a task on the mapview.
 * Make sure your JOSM is running with Remote Control Enabled, and Choose **Edit with JOSM**
 ![task_lock](https://github.com/russdeffner/DRCOG_Buildings/blob/master/images/TaskLock.PNG)
 
 * This will populate your JOSM with the OSM data in your task area.
 
### Getting the DRCOG Building Data for your Task

 * Each task has a pregenerated osm-format map data file associated with it
 * This pregenerated file contains the building shapes as well as attributes about each building such as address and height
 * Your job is to review the pre-generated OSM file in JOSM and make some adjustments prior to uploading the file to the OpenStreetMap database
![data_save](https://github.com/russdeffner/DRCOG_Buildings/blob/master/images/SaveData.PNG)

 * You can just open, but we suggest saving, the DRCOG `.osm` file by clicking the link in the **Extra Instructions** section shown in the image above.
 * You can ignore the Tip about downloading the .gpx file in order to see the current task boundary. The pregenerated OSM data file for the task will only contain buildings within the task boundary
 * Open the DRCOG .osm data file in JOSM; depending on your JOSM install method you may simply be able to click on the JOSM file in your Downloads directory
 * **CAUTION** If you have worked on multiple tasks for this project you may have multiple .osm files in your 'Downloads' directory; be sure to open the correct file for your current task

 * Once you have opened the .osm file you should see something like the below image; this is for the the task #11 from the Idaho Springs pilot project
 ![download_osm](https://github.com/russdeffner/DRCOG_Buildings/blob/master/images/2DataLayers.PNG)
 
* If you don't see both data sources (drcog...osm & Data Layer x), make sure your JOSM remote control is enabled, restart JOSM and try again from the selecting **Edit in JOSM** from the Tasking Manager step above. 
* You may also have an imagery layer as some projects may have a preferred imagery to use for comparison that will automatically load. If not, bring in Bing and any others you prefer; most likely existing data will be mapped/aligned to Bing. Ideally align to available GPS traces; where there is none or still is questionable, align imagery and DRCOG data to existing mapping or Bing where there is little to no existing data.

### Reviewing the data before uploading

 * The overall workflow is to "merge" the DRCOG data into your OSM Data Layer, while reviewing both data layers for possible conflicts.
 * Make sure you have the DRCOG dataset active, select a building and use **Merge selection** under the Edit menu (CTRL+SHIFT+M).
 * Merge the building into the OSM Data Layer as shown in image below.
 ![Merge_Building](https://github.com/russdeffner/DRCOG_Buildings/blob/master/images/merge.PNG)
 
 * Now switch to the OSM Data Layer, there will be 3 scenarios:
  * 1) If there is no existing OSM data, examine tags to make sure there are no obvious mistakes like incomplete addresses, impossible heights, building type make sense for the area/imagery.
    * Then delete the building from the DRCOG layer (i.e. once it's merged into your OSM layer, it can safely be deleted from the import layer and once all buildings are gone from the import layer, you're done).
 * If there is an existing building in OSM then you must decide how to conflate the two datasets:
 *(**NOTE:** Preserve the work of previous mappers wherever possible.)*
  * 2) If existing buildings in OSM are of higher quality:
    * Copy the tags from the imported building as necessary.
    * Delete the imported building from both layers (i.e we're only saving tags from DRCOG).
  * 3) If the imported data are of higher quality:
    * Select both buildings and use the **Replace geometry** tool (CTRL+SHIFT+G) under Additional Tools menu.
    * Conflate the tagging by selecting which to use if there are conflicts (example: building type).
    * Delete the building from the import layer (the original and DRCOG should now be one geometry on your OSM Layer). 
![replace](https://cloud.githubusercontent.com/assets/353700/12942518/ddba87a4-d001-11e5-9441-2561f67b45bc.gif)

* Do not worry about editing any osm nodes such as points of interest contained within the building shape.
* If there are any problems you don't know how to deal with, do not proceed. Instead, flag the `.osm` file for a more advanced user to look at. 
  * Use github [issues](https://github.com/geochasm/DRCOG_Buildings/issues) to flag concerns; include the task number in your issue.
  * Then unlock your task on the tasking manager and pick a new area to work on, leaving a comment there as well so the next mapper is aware.

 * Once you have merged the DRCOG buildings that need to be added to OSM and copied tags or replaced geometry to existing OSM  data; you can prepare to upload. If following the workflow you should know your area is finished when you've deleted (merged) all the data from the DRCOG dataset.

* Before uploading though, do one more check - Run JOSM Validator, and if there are errors, fix them. 
![validator](https://cloud.githubusercontent.com/assets/353700/12942520/ddc572f4-d001-11e5-8cf6-399511cd47fa.gif) 

### Finally, upload it

* Select the OSM Data Layer.

* Click the Upload button, the green up arrow button.
![screen shot 2016-04-02 at 3 53 02 pm](https://cloud.githubusercontent.com/assets/3673236/14229617/ad64e298-f8ec-11e5-9693-ba3f3a0e2085.png)

* If you see a "Suspicious data found" warning, double check that none need to be addressed, then click "Continue upload".
![screen shot 2016-04-02 at 3 53 11 pm](https://cloud.githubusercontent.com/assets/3673236/14229619/ad72b6c0-f8ec-11e5-97b6-66b43f1c2937.png)

* As discussed above, use a **changeset comment** such as (hopefully preloaded via the tasking manager): `DRCOG Planimetrics Import #DRCOGPlanimetrics #[City or County][Feature] https://wiki.openstreetmap.org/wiki/Denver_Planimetrics_Import ` 
 and **source**: `Denver Regional Council of Governments https://data.drcog.org/dataset/building-roofprints-2014`.
![screen shot 2016-04-02 at 3 53 17 pm](https://cloud.githubusercontent.com/assets/3673236/14229620/ad73128c-f8ec-11e5-9e2f-44d272bd6403.png)

* If you see an Authorization window asking you to log in to OpenStreetMap, log in and remember to use your `_import` username.

* Go back to the Tasking Manager and click **Mark task as done**. If necessary, leave a comment so if another mapper validates your edits they are aware (i.e. one building from satellite imagery not in import data; left alone).

## What to watch out for

### Validate the import with your eyes before uploading!

 * Run the [JOSM validator](http://wiki.openstreetmap.org/wiki/JOSM/Validator). Check for any errors it detects.
 * Check for small building parts that should be joined to the main building. We've already found a few examples of these in the data (see [LA Building Import - issue #19](https://github.com/osmlab/labuildings/issues/19)), so make sure you keep an eye out for these.  To join small parts, select both polygons and select **Tools > Join overlapping Area**.
 ![screen shot 2016-04-04 at 2 38 36 pm](https://cloud.githubusercontent.com/assets/695934/14264162/74ab59f4-fa73-11e5-8c4e-896c7fa2c2e4.png)

 * If it's a small sliver, it makes sense that the "proper" data is on the larger object. Delete all the tags on the sliver and join the two objects.
 * If it's larger, like a strip mall split into pieces, then do:
   * `start_date` -> None if multiple or the one option if there's only one
   * `height` -> largest number
   * `ele` -> largest number 
   * `building:units` -> none if different
![screen shot 2016-04-04 at 2 38 44 pm](https://cloud.githubusercontent.com/assets/695934/14264157/6c9f23ee-fa73-11e5-8744-e49d7e179003.png)

 * Inspect everything else with a critical eye! Don't trust that the validator or FIXME tags will catch everything. There may be other bugs that only you can detect. Use your human smarts!
 
### Conflating with existing data
 * Look for any overlaps with existing buildings. Existing buildings in OSM are probably _more_ up-to-date than our imported data. Do not assume the imported data is better, mostly likely it is worse! 
 * Carefully combine the import data with the existing OSM data. If you aren't sure about some tags, ask someone! Especially ask the original mapper! 
 
### How to validate the data
 * We are working to get more up-to-date aerial imagery... for now, try several of the default sources.
 * See if the street is on Mapillary or OpenStreetCam; there's JOSM plugins for that!
 * Contact mappers that have added information like POIs in the area - maybe they know or can look?
 * Go out and check it out yourself! Take a field trip!
 * **DO NOT USE GOOGLE MAPS OR GOOGLE STREET VIEW**.

### Identifying new buildings with imported and existing data
* The imagery was purchased by DRCOG. This is the same imagery used as a reference for tracing the imported data. In some areas, the default imagery sources are more updated than the imported data and we can use it to identify newer buildings not found in the imported and/or existing data.
* Newer building should be identified and flagged. Tag the building with `fixme` and add a note: `Appears in satelite imagery.`
![screen shot 2016-04-02 at 3 19 31 pm](https://cloud.githubusercontent.com/assets/3673236/14229396/ab9f392c-f8e7-11e5-80ca-635b97332bd8.png) We can verify this with more recent planimetric data.
* Likewise, buildings maybe demolished and does not exist anymore, delete them.
 
## Communicate communicate communicate!

### How to ask for help

 * Search the Training Material in the [DRCOG Import Drive](https://drive.google.com/open?id=1QsBDjI15l68WhTTRg8r-RWoY5biUiPfb).
 * Create [issues](https://github.com/geochasm/DRCOG_Buildings/issues) on this github repo.
 * Ask questions on the OSM #Colorado [Slack Channel](https://osmus-slack.herokuapp.com/).
 * Contact [DRCOG](https://drcog.org/) or [OSM-Colorado](https://www.meetup.com/OSM-Colorado/).

### How to share your progress

 * Make sure you upload your changes with the recommended comment and mark your task on the tasking manager as complete. Leave a comment there as well if it would be helpful (i.e. a few buildings were difficult to tell which dataset was more accurate, etc.).

### How to communicate with other mappers

 * JOSM [GeoChat](http://wiki.openstreetmap.org/wiki/JOSM/Plugins/GeoChat) feature.
 * Come to one of the next OSM related [meetup groups](https://www.meetup.com/OSM-Colorado/pages/24662291/Colorado_Groups/) in Colorado.
 * Befriend other mappers on openstreetmap.org!
 
### Thanks to the LA Buildings Import
* This import workflow guide is based on the guide published by the Los Angeles building import at **[https://github.com/osmlab/labuildings/blob/master/IMPORTING.md](https://github.com/osmlab/labuildings/blob/master/IMPORTING.md)**. 
