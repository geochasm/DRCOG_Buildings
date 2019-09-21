How to import
=============

## Getting started

### Creating an import account

 * OSM best practices require that you [do not use your normal OSM account for the imports](http://wiki.openstreetmap.org/wiki/Import/Guidelines#Use_a_dedicated_user_account). Create a new account for this purpose. 
 Usually, it's your existing OSM username followed by `_imports` (e.g. `tekim_imports`).
 Post your import account username in this [ticket](https://github.com/geochasm/DRCOG_Buildings/issues/1).
 * **Remember** you should log into the OSM Tasking Manager (see below) with your 'imports' username but you will also need to use that same username from any data upload from JOSM.

### Getting familiar with JOSM

To contribute to this project, you need to use the JOSM editor.  Here are some resources to get you started:
 * JOSM Website - https://josm.openstreetmap.de/
 * LearnOSM - http://learnosm.org/en/josm/
 * Mapbox Mapping wiki - https://www.mapbox.com/blog/making-the-most-josm/
 
### Tools for the import

1. OpenStreetMap account with the `_imports` suffix.
1. Working [JOSM](https://josm.openstreetmap.de/) installation, with the [Conflation](https://wiki.openstreetmap.org/wiki/JOSM/Plugins/Conflation) plugin installed from Preferences > Plugins.
1. *(Optional)* Text editor with advanced find/replace functionality, such as [BBEdit](https://www.barebones.com/products/bbedit/), [Notepad++](https://notepad-plus-plus.org/), or [Atom](https://atom.io/).

## Import workflow

### Selecting a task in the Tasking Manager

 * Go to [http://tasking-manager.mapsarecool.com](http://tasking-manager.mapsarecool.com) - Select a project, typically the one on top/highest priority unless told otherwise (i.e. at an importathon).

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

### Pre-checking the data before merging

The overall workflow is to "merge" the DRCOG data into your OSM Data Layer, while reviewing both data layers for possible conflicts. Some quality checks before merging will make things easier.

1. With the .osm file layer activated (no other OSM map data visible), run the **JOSM Validator** (SHIFT+V) to look for errors. Common errors at this stage can include multiple buildings with the same address (usually an error where a house and a garage or shed have been given the same address tags). Refer to the section below on **fixing common errors** for solutions and guidelines.
1. While still in the new .osm file layer, **Select All** (CTRL+A) to select all objects, and then **Deselect Nodes** (SHIFT+U) to select all of the buildings. In the Selection window on the right side of the screen, scroll through the list of selected buildings to look for malformed street names. Examples of bad street names include:
   * unexpanded abbreviations (Ct instead of Court, or Ln instead of Lane)
   * use of the directional prefix "North" (not used in City and County of Denver)
   * occasional errors in the automatic import, such as the street name *Steele Street* being expanded to *Streeteele Street*
1. Do not upload bad data to OSM, fix it before importing, or flag the task as having problems:
   * Use github [issues](https://github.com/geochasm/DRCOG_Buildings/issues) to flag concerns, make sure you indicate the task number in your issue.
			* Leave comments in the tasking manager.
1. Remove multi-part buildings from the .osm file layer before importing (buildings with multiple polygons side-by-side), these require special handling and are not being imported at this time. If you are already well trained in multi-part buildings and 3D building tags you may proceed with caution.

### Reviewing the data before uploading

 * Make sure you have the DRCOG dataset active, select a building and use **Merge selection** under the Edit menu (CTRL+SHIFT+M).
 * Merge the building into the OSM Data Layer as shown in image below.

 ![Merge_Building](https://github.com/russdeffner/DRCOG_Buildings/blob/master/images/merge.PNG)
 
 * Now switch to the OSM Data Layer (right click on "Data Layer 1" and select "Activate"), there will be 3 scenarios:
 
1. If there is no existing OSM data for the building, examine tags to make sure there are no obvious mistakes like incomplete addresses, impossible heights, building type make sense for the area/imagery.
   1. Then delete the building from the DRCOG layer (i.e. once it's merged into your OSM layer, it can safely be deleted from the import layer and once all buildings are gone from the import layer, you're done).

If there is an existing building in OSM then you must decide how to conflate the two datasets (**NOTE:** Preserve the work of previous mappers wherever possible).

2. If existing buildings in OSM are of higher quality:
   1. Copy the tags from the imported building as necessary.
   1. Delete the imported building from both layers (i.e we're only saving tags from DRCOG).

3. If the imported data are of higher quality:
    1. Select both buildings and use the **Replace geometry** tool (CTRL+SHIFT+G) under Additional Tools menu.
    1. Conflate the tagging by selecting which to use if there are conflicts (example: building type).
    1. Delete the building from the import layer (the original and DRCOG should now be one geometry on your OSM Layer). 
				
![replace](https://cloud.githubusercontent.com/assets/353700/12942518/ddba87a4-d001-11e5-9441-2561f67b45bc.gif)

* Do not worry about editing any other nodes such as points of interest contained within the building shape.
* If there are any problems you don't know how to deal with, *do not proceed*. Instead, flag the task in the tasking manager for a more advanced user to look at. 
  * Use github [issues](https://github.com/geochasm/DRCOG_Buildings/issues) to flag concerns; include the task number in your issue.
  * Then unlock your task on the tasking manager and pick a new area to work on, leaving a comment there as well so the next mapper is aware.

 * Once you have merged the DRCOG buildings that need to be added to OSM and copied tags or replaced geometry to existing OSM data; you can prepare to upload. If following the workflow you should know your area is finished when you've deleted (merged) all the data from the DRCOG dataset.
 
 * Delete the DRCOG dataset (layer) from JOSM: right-click the "drcog...osm" layer from the layers menu and select **Delete** - if you get a warning, make sure you did not miss any buildings (i.e. this layer should be completely empty if you have followed the workflow).

* Now before uploading your OSM Data Layer, do one more check - Run **JOSM Validator** (SHIFT+V), and if there are errors, fix them. 
![validator](https://cloud.githubusercontent.com/assets/353700/12942520/ddc572f4-d001-11e5-8cf6-399511cd47fa.gif) 

### Finally, upload your data

* Select the OSM Data Layer.
* Click the Upload button, the green up arrow button.

![screen shot 2016-04-02 at 3 53 02 pm](https://cloud.githubusercontent.com/assets/3673236/14229617/ad64e298-f8ec-11e5-9693-ba3f3a0e2085.png)

* If you see a "Suspicious data found" warning, double check that none need to be addressed, then click "Continue upload".

![screen shot 2016-04-02 at 3 53 11 pm](https://cloud.githubusercontent.com/assets/3673236/14229619/ad72b6c0-f8ec-11e5-97b6-66b43f1c2937.png)

* Use a **changeset comment** (will be preloaded via the tasking manager): `DRCOG Planimetrics Import #DRCOGPlanimetrics #[City or County][Feature] https://wiki.openstreetmap.org/wiki/Denver_Planimetrics_Import ` 
 and **source**: `Denver Regional Council of Governments https://data.drcog.org/dataset/building-roofprints-2014`.
	
![screen shot 2016-04-02 at 3 53 17 pm](https://cloud.githubusercontent.com/assets/3673236/14229620/ad73128c-f8ec-11e5-9e2f-44d272bd6403.png)

* If you see an Authorization window asking you to log in to OpenStreetMap, log in and remember to use your `_imports` username.

* Go back to the Tasking Manager and click **Mark task as done**. If necessary, leave a comment so if another mapper validates your edits they are aware (i.e. one building from satellite imagery not in import data; left alone).

## Fixing common problems

### Building "slivers"

* Check for small building parts that should be joined to the main building. We've already found a few examples of these in the data (see [LA Building Import - issue #19](https://github.com/osmlab/labuildings/issues/19)), so make sure you keep an eye out for these.  To join small parts, select both polygons and select **Tools > Join overlapping Area**.

 ![screen shot 2016-04-04 at 2 38 36 pm](https://cloud.githubusercontent.com/assets/695934/14264162/74ab59f4-fa73-11e5-8c4e-896c7fa2c2e4.png)

 * If it's a small sliver, it makes sense that the "proper" data is on the larger object. Delete all the tags on the sliver and join the two objects.
 * If it's larger, like a strip mall split into pieces, then do:
   * `start_date` -> None if multiple or the one option if there's only one
   * `height` -> largest number
   * `ele` -> largest number 
   * `building:units` -> none if different
			
![screen shot 2016-04-04 at 2 38 44 pm](https://cloud.githubusercontent.com/assets/695934/14264157/6c9f23ee-fa73-11e5-8744-e49d7e179003.png)

### Bad addresses (Advanced Repair)

If during your initial review of the .osm file in JOSM you find that there is a consistently mis-named street, it can be helpful to repair it in the .osm file before importing. Example: All of the buildings on Elm Street are labeled "Elm St".

1. Close the .osm file by right clicking on it and selecting **Delete**. If you are partway through the import and have already made changes to the .osm file, you should save before closing.
2. Open the .osm file in an advanced text editor such as [BBEdit](https://www.barebones.com/products/bbedit/), [Notepad++](https://notepad-plus-plus.org/), or [Atom](https://atom.io/).
3. Use the editors find and replace functionality to find all instances of the error and replace with the correct text.

**Example:** You see the following way in the .osm file (with a bad street name):

```xml
  <way id='-162872'>
    <nd ref='-155297' />
    <nd ref='-155299' />
    <nd ref='-155301' />
    <nd ref='-155303' />
    <nd ref='-155297' />
    <tag k='addr:city' v='Denver' />
    <tag k='addr:housenumber' v='66' />
    <tag k='addr:postcode' v='80203' />
    <tag k='addr:state' v='CO' />
    <tag k='addr:street' v='Logan St' />
    <tag k='building' v='residential' />
    <tag k='height' v='8' />
    <tag k='source' v='DRCOG PLANIMETRICS DATA' />
  </way>
```
Then in your text editor you could search for the text `v='Logan St'`, and replace with the text `v='Logan Street'` to repair all instances of the error in the .osm file.

**Tip:** This can be used to repair many small problems in the .osm file, such as unexpanded street suffixes, incorrect "North" streets (City and County of Denver does not currently use the "North" prefix anywhere, or even strange import errors, such as `Steele Street` being expanded to `Streeteele Street` (real example).

## What to watch out for

### Validate the import with your eyes before uploading!

 * Run the [JOSM validator](http://wiki.openstreetmap.org/wiki/JOSM/Validator). Check for any errors it detects.
 
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
 * Look on the [wiki](https://github.com/geochasm/DRCOG_Buildings/wiki); if you can't find an answer, create [issues](https://github.com/geochasm/DRCOG_Buildings/issues) on this github repo.
 * Or ask questions on the OSM #Colorado [Slack Channel](https://osmus-slack.herokuapp.com/).
 * Contact [DRCOG](https://drcog.org/) or [OSM-Colorado](https://www.meetup.com/OSM-Colorado/).

### How to share your progress

 * Make sure you upload your changes with the recommended comment and mark your task on the tasking manager as complete. Leave a comment there as well if it would be helpful (i.e. a few buildings were difficult to tell which dataset was more accurate, etc.).

### How to communicate with other mappers

 * JOSM [GeoChat](http://wiki.openstreetmap.org/wiki/JOSM/Plugins/GeoChat) feature.
 * Come to one of the next OSM related [meetup groups](https://www.meetup.com/OSM-Colorado/pages/24662291/Colorado_Groups/) in Colorado.
 * Befriend other mappers on openstreetmap.org!
 
### Thanks to the LA Buildings Import
* This import workflow guide is based on the guide published by the Los Angeles building import at **[https://github.com/osmlab/labuildings/blob/master/IMPORTING.md](https://github.com/osmlab/labuildings/blob/master/IMPORTING.md)**. 
