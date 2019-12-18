# **Package and submit your map**

*The following guide was authored on the [docs.oc.tc website](http://docs.oc.tc/guides/packaging/compiling_releasing), and we've simply reused the guide and made a few minor tweaks.*

Your build is now complete, the world is pruned, the XML is coded, and the map has received its fair share of tender, love and care — it is now ready to be submitted to our Map team for reviewal.

Before we can submit the map, we'll need to package it up in a format that our volunteers can easily understand and work with.

### **Assemble your files into a folder**

Start by getting rid of any [unneeded files](http://docs.oc.tc/guides/packaging/cleaning_files).  Be careful here, you wouldn't want to accidentally delete your map save.  If you're concerned, create a duplicate of your map folder before you start deleting anything.

Next, create a new folder that we'll be using to submit your materials. Title it according to the title you decided to give to you map.  Here is an image of what your map folder should look like:

![folder_layout.png](http://docs.oc.tc/img/folder_layout.png)

### **Double-check your XML**

The `map.xml` file is the XML you coded for your map. This file is essential when it comes to having your map loaded and tested. While you may submit maps without this file, it means someone else will have to code all the gameplay for your map. This makes your map less likely to be tested or used at all.

Also, take note of the following coding guidelines when creating your `map.xml` file:

- Verify there are **no tabs in the XML** – 4 spaces only
- Verify the main map element and its main elements are not indented
- Follow [Semantic Versioning](http://semver.org/) when deciding the map version
- Bump the map version if the gameplay has changed (if this isn't the first iteration of the map)
- [Validate the XML](https://www.w3schools.com/xml/xml_validator.asp) to make sure it does not have any syntax errors

### **The Map Image**

The `map.png` file displays the image of your map on the website. The standard resolution for these pictures is `290x246`. This image should contain a general overview of the map’s playing area.  A couple examples:

![BlockRage_map.png](http://docs.oc.tc/img/BlockRage_map.png)

![RageQuit_map.png](http://docs.oc.tc/img/Rage%20Quit_map.png)

### **Compressing the folder to a ZIP file**

Before you upload and submit the map, you must compress your submission folder to a `.zip` format. Do not compress to a `.rar` or any other format.

To compress a folder:

- Windows: Right Click > Send To > Compressed Zip
- Mac: Right Click > Compress

### **Submitting your map**

Please visit the [Map Submissions Google Form](https://forms.gle/1bLjskfuydmfeSh57) to upload and submit your map!