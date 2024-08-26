# Diffusion Toolkit

Are you tired of dragging your images into PNG-Info to see the metadata?  Annoyed at how slow navigating through Explorer is to view your images? Want to organize your images into albums? Wish you could search for your images by prompt? 

Diffusion Toolkit (https://github.com/RupertAvery/DiffusionToolkit) is an image metadata-indexer and viewer for AI-generated images. It aims to help you organize, search and sort your ever-growing collection.

[![Organize your AI Images](https://img.youtube.com/vi/r7J3n1LjojE/hqdefault.jpg)](https://www.youtube.com/watch?v=r7J3n1LjojE&ab_channel=BillMeeks)

# Installation

* Currently runs on Windows only 
* [Download](https://github.com/RupertAvery/DiffusionToolkit/releases/latest
) the latest release 
    * Look for **> Assets** under the latest release, expand it, then grab the zip file **Diffusion.Toolkit.v1.x.zip**.
* Unzip all the files to a folder
* You may need to install the [.NET 6 Desktop Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/6.0) if you haven't already

# Features

* Support for many image generators
   * AUTOMATIC1111 and A1111-compatible metadata such as
      * Tensor.Art
      * SDNext
      * ComfyUI with [SD Prompt Saver Node](https://github.com/receyuki/comfyui-prompt-reader-node)
   * InvokeAI (Dream/sd-metadata/invokeai_metadata)
   * NovelAI
   * Stable Diffusion
   * EasyDiffusion
   * RuinedFooocus
   * Fooocus
   * FooocusMRE
   * Stable Swarm
* Scans and indexes your images in a database for lightning-fast search
* Search images by metadata (Prompt, seed, model, etc...)
* Custom metadata (stored in database, not in image) 
    * Favorite
    * Rating (1-10)
    * NSFW
* Organize your images 
    * Albums
    * Folder View
* Drag and Drop from Diffusion Toolkit to another app
* Translations - Diffusion Toolkit is localized

# What's New in v1.6.2

After several months without any updates, here's a few that include some features users have suggested or requested. 

Please make sure to check each one below to make sure you don't miss out on anything, there are a lot of changes and some might be what you are looking for.

One nice feature you might gloss over is added filters for excluding terms in the Prompt / Negative Prompt. Now you can properly search for "cape", and exclude "landscape", or "superhero" from the search results.

Thanks to Terence for a whole bunch of bug fixes and enhancements!

## Enhancements

* Added VERY basic ComfyUI support
  * Gets the Prompt from the first **CLIPTextEncoder** node
  * Use **Rebuild metadata** to scan in the Prompt for existing images to make them searchable
  * Future plan is to allow user to custom map node values to fields using the metadata viewer
  * Workflow "fingerprints" are tracked, so in the future, if you update the mapping, you will be able to re-run a metadata scan on only those images with the same workflow
* Added a simple **ComfyUI** metadata viewer in the Metadata pane
  * Click the **Workflow** tab next to the **Metadata** tab anywhere the Metadata pane is visible (overlay/preview overlay/metadata pane under preview)
* Refresh search results behavior has changed
   * Press F5 or click the search button in the search bar to **refresh the current page**
   * Makes it easier to reload the current page after marking for deletion, and Hide images for deletion is enabled
   * Hold CTRL and press F5 or click the the search button to **refresh and return to the first page**
* New **Unavailable** tag added
   * This is an internally managed tag that is updated:
      * when the metadata scanner checks existing files on startup
      * when a rescan is performed (click Scan folders for new images or CTRL-R)
      * when manually checked through **Tools > Scan for Unavailable images**
   * Available images will be restored when any of the above is performed
   * The tag can be filtered on (see Added filters below)
* You can now hide images tagged **For Deletion** from search results 
* You can also hide images tagged **Unavailable** from search results (See View menuitem)
* **Auto-advance on tag** option added
   * When enabled, after tagging with a Rating, Favorite, NSFW or Delete, the next image will be selected 
   * Affects Thumbnail View and Popout Preview
   * Go to **View > Auto Advance on Tag** to toggle or CTRL+Shift+T in the Thumbnail View or Popout Preview
* More prominent display of tagged For Deletion status
* **Mouse wheel navigation** added to Preview
   * When enabled, the scrolling mouse wheel will allow you to move between previous/next images
   * When enabled, holding CTRL will perform a zoom
   * Affects Preview and Popout Preview
   * Go to **Settings > Image > Use mouse wheel...** to toggle
* Double-click the preview pane to open the image in your selected viewer (i.e. the Popout preview, or whatever you have configured)
* Added a **Slideshow** function in the Popout Preview window. 
   * Press **Space** to start/stop the slideshow
   * Go to **Settings > Image > Slide show delay** to adjust the time between image changes
* Improved thumbnail loading efficiency  
   * Only thumbnails in current view are loaded
   * Should have slightly better responsiveness when scrolling quickly / scrolling to bottom
* Add **Actual Size** option in Preview
   * Press CTRL+Shift+A to toggle
* Added filters: (Click the Filter button or press CTRL-F)    
   * **Exclude Prompt / Negative** - show images that do not include the specified prompt / negative terms 
   * **Aesthetic Score - No Score** - show images without an Aesthetic Score
   * **In Album** - show images are have been added to an album or not
   * **Unavailable** - show images that have been tagges as Unavailable
* Add support for **Stable Swarm** metadata
* Add support for **Fooocus** metadata
* Albums
   * All albums will be shown on right-click > Add to Albums (not just last 10)


## Bugfixes

* Additional indexes to fix query slowdowns
* Fixed bug where Preview Pane loses focus when changing pages
* Move txt files when moving images #239
* Fix issue with unsetting rating of selected images in thumbnail view #237
* Fixed some startup crashes
* Several bug fixes