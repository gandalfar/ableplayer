Able Player
==========

*Able Player* is a fully accessible cross-browser media player. It uses
the HTML5 \<audio\> or \<video\> element for browsers that support them,
and (optionally) the JW Player as a fallback for those that don’t.

To see the player in action check our [Able Player Examples][examples] page.

Features
--------

-   Supports both audio and video.
-   Supports either a single audio track or an entire playlist.
-   A full set of player controls that are keyboard-accessible, properly labeled for screen reader users, and controllable by speech recognition users. 
-   Customizable keyboard shortcuts that enable the player to be operated from anywhere on the web page (unless there are multiple instances of the player on a given page; then the player must have focus for keyboard shortcuts to work).  
-   High contrast, scalable controls that remain visible in Windows High Contrast mode, plus an easy-to-see focus indicator so keyboard users can easily tell which control currently has focus. 
-   Support for closed captions and subtitles in Web Video Timed Text (WebVTT) format, the standard format recommended by the HTML5 specification.   
-   Support for chapters, also using WebVTT. Chapters are specific landing points in the video, allowing video content to have structure and be more easily navigated. 
-   Support for text-based audio description, also using WebVTT. At designated times, the description text is read aloud by screen readers.  Users can optionally set their player to pause when audio description starts in order to avoid conflicts between the description and program audio. 
-   Support for audio description as a separate video. When two videos are available (one with description and one without), both can be delivered together using the same player and users can toggle between the versions. 
-   Support for adjustable playback rate. Users who need to slow down the video in order to better process and understand its content can do so; and users who need to speed up the video in order to maintain better focus can do so. 
-   An interactive transcript feature, built from the WebVTT caption and description files as the page is loaded. Users can click anywhere in the transcript to start playing the video (or audio) at that point.  Keyboard users can also choose to keyboard-enable the transcript, so they can tab through its content one caption at a time and press enter to play the media at the desired point. 
-   Automatic text highlighting within the transcript as the media plays. This feature is enabled by default but can be turned off if users find it distracting. 
-   Support for playing YouTube videos within the Able Player chrome.  
-   Optional seamless integrated support for JW Player as a fallback player for users whose browsers don't support HTML5 media. The fallback player uses the same custom interface and provides a nearly identical experience.
-   Extensive customization. Many of the features described above are controlled by user preferences. This is based on the belief that every user has different needs and there are no one-size-fits-all solutions. This is the heart of universal design. 
    

Compatibility
-------------

*Able Player* has been tested with the following browsers and assistive
technologies.

-   Firefox 3.x and higher
-   Internet Explorer 10 and higher without fallback 
-   Internet Explorer 8 and 9, dependent on JW Player as fallback. 
-   Google Chrome 7.0 and higher
-   Opera 10.63 and higher
-   Safari 5.0 on Mac OS X
-   Safari on IOS 3.2.2 and higher (audio only, video plays in default IOS player)
-   Chrome on Android 4.2 and higher

Note that mobile browsers have limitations (e.g., volume control and autostart are not supported) 

Dependencies
------------

*Able Player* has a few dependencies, but most are either provided with
*Able Player* or available through Google’s hosted libraries. The one
exception is the fallback player—see the *Fallback* section below for
details.

-   *Able Player* uses [jQuery][]. The example code
    below uses Google’s hosted libraries; no download required.
-   *Able Player* uses [Modernizr][] to enable styling of HTML5 elements
    in Internet Explorer 6 through 8. A Modernizr 2.6.2 Custom Build is
    distributed with *Able Player*, and is all that *Able Player* needs.
-   *Able Player* uses [jquery.cookie][] to store and retrieve user
    preferences in cookies. This script is distributed with *Able
    Player*.

Fallback
--------

For older browsers that don’t support HTML5 media elements, you need a
fallback solution. *Able Player* was developed to work seamlessly with
[JW Player][], specifically **JW Player 6** (successfully tested with  
versions 6.0 and 6.11). JW Player is free for non-commercial use but 
is licensed separately and is not distributed with *Able Player*. 
After licensing and downloading JW PLayer, copy *jwplayer.js*, *jwplayer.html5.js*, 
and *jwplayer.flash.swf* into the
*Able Player* */thirdparty* directory.

If you choose to use JW Player as your fallback player, 
users with some older browsers will have a similar experience with 
*Able Player* as users with newer browsers. 

Note that *most* browsers in use today support HTML5 media elements.
Here’s a breakdown:
-   Chrome since 3.0
-   Firefox since 3.5
-   Safari since 3.1
-   Opera since 10.5
-   Internet Explorer since 9.0 (video was buggy in 9; better in 10)

Note the following limitations in Internet Explorer (IE): 
- IE10 and higher work fine without a fallback player 
- IE9 was the first version of IE to support HTML5 media elements. However, its support for video was buggy so Able Player uses the fallback if it's available
- IE8 works fine with JW Player as fallback 
- IE6 and 7 are not supported   

At some point we may decide that it’s reasonable to stop supporting a
fallback player. However, according to [WebAIM’s 2014 Screen Reader User
Survey][] 19.8% of screen reader users are still using Internet Explorer 8, 7, or 6. Until these users catch up, we think we have to provide a
working fallback.

As an alternative fallback, you could link to the media file so users
can download it and play it on their player of choice, and/or provide a
transcript.

Setup Step 1: Use HTML5 Doctype
-------------------------------

*Able Player* is built on the HTML5 media elements, so at the top of
your web page be sure you have the HTML5 doctype:

```HTML
<!DOCTYPE html>
```

Setup Step 2: Add JavaScript and CSS
------------------------------------

Copy and paste the following code into your web page. This code applies
to all use cases, both audio and video.

```HTML
<!-- Dependencies -->
<script src="thirdparty/modernizr.custom.js"></script>
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.8.2/jquery.min.js"></script>
<script src="thirdparty/jquery.cookie.js"></script>
 
<!-- CSS --> 
<link rel="stylesheet" href="styles/ableplayer.css" type="text/css"/>
 
<!-- JavaScript -->
<script src="build/ableplayer.js"></script>
```

Setup Step 3: Add HTML
----------------------

Add an HTML5 \<audio\> or \<video\> element to your web page, as
follows.

### Audio

Copy and paste the following code into your web page, replacing the
source files with the path to your own media files. Use both OGG and MP3
to ensure cross-browser compatibility, since some browsers don’t support
MP3.

```HTML
<audio id="audio1" data-able-player preload="auto">
  <source type="audio/ogg" src="path_to_audio_file.ogg"/>
  <source type="audio/mpeg" src="path_to_audio_file.mp3"/>
</audio>
```

### Video

Copy and paste the following code into your web page, replacing the
source files with the path to your own media files. Use both WebM and MP4
to ensure cross-browser compatibility, since some browsers don’t support
MP4.

```HTML
<video id="video1" data-able-player preload="auto" width="480" height="360" poster="path_to_image.jpg">
  <source type="video/webm" src="path_to_video.webm" data-desc-src="path_to_described_video.webm"/>
  <source type="video/mp4" src="path_to_video.mp4" data-desc-src="path_to_described_video.mp4"/>
  <track kind="captions" src="path_to_captions.vtt"/>
  <track kind="descriptions" src="path_to_descriptions.vtt"/>
</video>
```


### Supported Attributes 

The following attributes are supported on both the \<audio\> and \<video\> elements:

-   **id** - required; any unique ID
-   **data-able-player** - required 
-   **width** - width of the media player in pixels. For video, this value should reflect the target width of the media itself. If not provided will default to 480.
-   **data-start-time** - optional; time at which you want the audio to start playing (in seconds)
-   **autoplay** - optional; play media automatically when page loads. For accessibility reasons, this is *not* recommended unless user is sure to *expect* media to automatically start. For example, autoplay could reasonably be used in conjunction with data-start-time in a media search application.   
-   **data-transcript-div** - optional; id of an external div in which to display the interactive transcript. 
    The transcript is generated automatically if captions and/or descriptions are available. 
    If this attribute is not provided the transcript will be displayed in its default container  
    adjacent to the player.  
-   **data-use-transcript-button** - optional; set to "false" to exclude transcript button from controller. If using the data-transcript-div attribute to write the transcript to an external container (e.g., on a dedicated transcript page), you might not want users to be able to toggle the transcript off. 
-   **data-transcript-title** - optional; override default transcript title (default is "Transcript", or "Lyrics" if the data-lyrics-mode attribute is present) 
-   **data-lyrics-mode** - optional; forces a line break between and within captions in the transcript 
-   **data-debug** - optional; if present will write messages to the developer console   
-   **data-volume** - optional; set the default volume (0 to 1; default is 0.5 to avoid overpowering screen reader audio)
-   **data-icon-type** - optional; "font" or "image"; "font" is the default with automatic fallback to image if browsers don't support icon fonts. Should generally leave as is unless testing the fallback. 
-   **data-seek-interval** - optional; interval (in seconds) of forward and rewind buttons. By default, seek interval is calculated to be 1/10 of the duration of media. 
-   **data-show-now-playing** - optional; "true" or "false" to include "Selected track" section within player; only applies when a playlist is present  
-   **data-fallback** - optional; specify a fallback player. Currently the only supported option is "jw" (JW Player)
-   **data-test-fallback** - optional; force browser to user fallback player (recommended for testing only) 
-   **data-fallback-path** - optional; override default path to directory in which the fallback player files or stored   
-   **data-translation-path** - optional; override default path to translations directory (NOTE: the translations directory includes *all* languages, including English, so the player will fail if it is unable to find this directory)
-   **data-lang** - optional; specify language of the player using 2-character language code (default is "en" for English)
-   **data-force-lang** - optional; include this option to force the player to use the value of *data-lang* as the player language. Otherwise, the player language will be set as follows, in order of precedence: 1) the language of the web page or user's web browser if either is known and if there is a matching translation file; 2) the value of *data-lang* if provided; 3) English. 
-   **preload** - optional; tells the browser how much media to download
    when the page loads. If the media is the central focus of the web
    page, use **preload=“auto”**, which instructs the browser to
    download as much of the media as possible. If the media is not a
    central focus, downloading the entire media resource can consume
    valuable bandwidth, so preload=“metadata” would be a better option.
-   **data-search** - optional; search terms to search for within the caption tracks, separated by a space  
-   **data-search-div** - optional; id of external container in which to display search results

The following attributes are supported on the \<video\> element only:
    
-   **height** - height of the video in pixels. If not provided will
    default to 360.
-   **poster** - path to an image file. Will be displayed in the player
    until the video is played.
-   **data-youtube-id** - optional; 11-character YouTube ID, to play the YouTube video using *Able Player*.
-   **data-youtube-desc-id** - optional; 11-character YouTube ID of the described version of a video. See the section below on *YouTube Support* for additional information. 

The following additional features are supported by *Able Player*:

#### Multiple source files

As with audio, we recommend including two versions of each video, one in
H.264 (MP4) and another in WebM or OGG for browsers that don’t support
MP4. Browsers will play the first media source that they support.

#### Closed Captions

Captions are added using the \<track\> element with kind=“captions”.
Captions must be in Web Video Text Tracks format ([WebVTT][http://dev.w3.org/html5/webvtt/]). WebVTT
tags within captions are currently ignored.  

If captions are provided, a CC button will be added to the
*Able Player* controller.

#### Audio Description

Supplemental description of key visual content for blind users can be
added using one of two methods.

The first method is the same as closed captions, a \<track\> element, with
kind=“descriptions”. This points to a WebVTT file, which is essentially
the same as a closed caption file, but its contents are description text
rather than captions. With this method, description text is written to a
container that has ARIA role=“alert”. Supporting screen readers
automatically announce the new text as soon as it is written to the
page.

The second method is to produce a separate video with description mixed
in. If multiple video sources are already provided (e.g., an MP4 and
WebM file), then the described version must be available in both of
these formats. For each video source that has a described version
available, add a **data-desc-src** attribute to the \<source\> element for
that video. The value of this attribute is a path pointing to the
described version of the video. With this method, the described version
of the video can be played instead of the non-described version, and the
two versions can be swapped with clicking the “D” button on the
controller.

If descriptions are available using either of the above methods, a
Description toggle button appears on the controller (represented by the
universal Description symbol, the letter “D”). How descriptions are
ultimately delivered depends on which of the above methods is used, and
on user preference. If a user prefers text-based description announced
by their screen reader, that’s what they’ll get. If they prefer an
alternate video with description mixed in, that’s what they’ll get. See
the section below on *User Preferences* for additional information about
preferences.

#### Sign language

Sign language translation is supported in a separate video player, 
synchronized with the main player. Tips for filming a sign language 
interpreter are available from [Signing Books for the Deaf][]: 

* [Filming the Signer][] 
* [Editing the Signer][]

If multiple video sources are already provided (e.g., an MP4 and
WebM file), then the sign language video must be available in both of
these formats. For each video source that has a sign language version
available, add a **data-sign-src** attribute to the \<source\> element for
that video. The value of this attribute is a path pointing to the
sign language version of the video. If a sign language version is available, 
a sign language button will be added to the media controller. 
This button will toggle the display of a secondary window in which 
the sign language video will appear. 

This is an experimental feature and a work in progress. Ultimately 
the intent is for the user to have full control of the size and position 
of the sign language video.  

Setup Step 4: Review User-Defined Variables in *ableplayer.js*
--------------------------------------------------------------

The JavaScript file *initialize.js* includes a block of user-defined
variables that can be modified from their default settings, such as
volume, color of controller buttons, seek interval for rewind and
forward buttons, and others. Explanations of each variable are provided
in the comments.

If you make changes to this or any other JavaScript script files,  
the player will need to be recompiled before your changes will take effect. 
To do so, run the shell script *compile.sh*. 

Playlists
---------

An *Able Player* playlist is an HTML list of tracks. The list can be
either ordered (\<ol\>) or unordered (\<ul\>). The following attributes
are supported on the list element:

-   **class** - required; must be **able-playlist**
-   **data-player** - required; must reference the ID of the media
    player in which the playlist should be played.
-   **data-embedded** - optional; add this attribute if you want your
    playlist to be embedded into the media player. If this attribute is
    omitted, the playlist will be external to the player and will appear
    wherever you place it on the web page.

Within the playlist, each list item must include data-\* attributes
where \* is the media type and the value of the attribute is the URL
pointing to the media file of that type. For example, the following
audio playlist includes three songs, each of which is available in MP3
and OGG:

```HTML
<ul class="able-playlist" data-player="audio1" data-embedded>
  <li data-mp3="song1.mp3" data-ogg="song1.ogg">My First Song</li>
  <li data-mp3="song2.mp3" data-ogg="song2.ogg">My Second Song</li>
  <li data-mp3="song3.mp3" data-ogg="song3.ogg">My Third Song</li>
</ul>
```

**Supported data-\* audio types:**

-   mp3
-   ogg or oga
-   wav

**Supported data-\* video types:**

-   mp4
-   webm or webmv
-   ogg or ogv

When a playlist is included on a page, the \<source\> elements within
the \<audio\> or \<video\> tags are optional. If they are provided, they
should match the first item in the playlist.

If your web page includes a playlist, you should also link to the
*ableplayer-playlist.css* file, as follows:

```HTML
<link rel="stylesheet" href="styles/ableplayer-playlist.css" type="text/css"/>
```

Interactive Transcript
----------------------

*Able Player* interactive transcripts are generated automatically from 
WebVTT caption and description files. If a transcript is available, a Transcript 
button will be added to the *Able Player* controller. 

Features of the interactive transcript include the following:  

-   Clicking anywhere in the transcript starts playing the media at that
    point.
-   This same functionality is accessible to keyboard users, who can tab
    through the transcript and press Enter at any point to start playing
    the media at that point. Since this creates a lot of extra tab stops
    on the page, this might be undesirable functionality for some
    keyboard users so it’s disabled by default. It can be toggled on/off
    in the Preferences dialog.
-   Text in the transcript is highlighted as the media plays. This can
    be toggled on/off in the Preferences dialog.
-   If subtitles are available, the transcript can be displayed in any supported language. 
    Available languages can be selected from a dropdown select field.      

YouTube Support
---------------

To play a YouTube video in *Able Player*, simply include a **data-youtube-id** attribute 
on the \<video\> element. The value of this attribute must be the video's 11-character YouTube ID. 

If captions are available on the YouTube video, they will be displayed automatically for users 
who have captions turned on when watching other YouTube videos. 

If a described version is available of the video, include a **data-youtube-desc-id** attribute 
on the \<video\> element as well. The value of this attribute must be the 11-character YouTube ID
of the described version. If users have "Description on by Default" checked within their *Able Player* 
preferences, the described version of the video will automatically play by default. 

Adjustable playback rate is available for some videos, but only if the user has opted in on using 
the HTML5 player in YouTube. 
To opt in, visit the <a href="https://www.youtube.com/html5">YouTube HTML5 Video Player</a> page.   

MIME Types
----------

If your media doesn’t play, one possibility is that your web server is
attempting to serve up the media with the incorrect MIME type. On
Apache, this can be correct by adding the following commands to the
.htaccess file:

```
# Audio MIME Types
AddType audio/mpeg mp3
AddType audio/mp4 mp4 
AddType audio/mp4 mpa
AddType audio/ogg ogg
AddType audio/ogg oga
AddType audio/wav wav 

# Video MIME Types
AddType video/mp4 mp4
AddType video/ogg ogv
AddType video/webm webm
```

If you don’t have access to your server’s .htaccess file, you should be
able to view and add MIME types somewhere within your server’s control
panel.

If your site is running on a Windows server, consult the documentation
from Microsoft. For example:

-   [Configuring MIME Types in IIS 7][]
-   [How to add MIME Types with IIS7 Web.config][]

Keyboard Shortcuts
------------------

*Able Player* includes several keyboard shortcuts that enable users to control the
player from anywhere on the web page, as follows:

-   **p or spacebar** = Play/Pause
-   **s** = Stop
-   **r** = Rewind 10 seconds
-   **f** = Forward10 seconds
-   **c** = Toggle captions
-   **m** = Mute
-   **u or 1-5** = Volume Up
-   **d or 1-5** = Volume Down
-   **t** = Settings
-   **h** = Help

Note that modifier keys (Alt, Control, and Shift) can be assigned by clicking
the Preferences button on the player. If users find that shortcut keys
aren’t working as advertised, they might have better success by
selecting different combinations of modifier keys to accompany the
default shortcut keys.

By default, keyboard shortcuts must be accompanied by Alt + Control. 

User Preferences
----------------

One of *Able Player’s* accessibility features is that the player is
highly customizable by users. The controller includes a Preferences
button that allows users to change default preferences and settings.
Their changes are stored in a browser cookie and in most cases should
therefore be preserved the next time they visit the site. Specifically,
users can control the following:

-   Modifier keys: Add *Alt*, *Ctrl*, or *Shift* to the Able Player keyboard
    shortcuts to avoid conflicts with other applications.
-   Closed captions on by default
-   Description on by default
-   Use text-based description if available.
-   Automatically pause video when text-based description starts
-   If using text-based description, make it visible
-   Transcript on by default 
-   Highlight transcript as video plays
-   Keyboard-enable transcript

Building the Able Player source
-------------------------------

The source JavaScript files for Able Player are in the */scripts* directory, 
and are combined into several different files (in the */build* directory) using 
[npm][] and [Grunt][]:

```sh
npm install
grunt
```

The npm and Grunt build process is defined by the *Gruntfile.js* and *package.json*
files. (Note that the **version number** is specified in *package.json*, and must be 
updated when a new version is released).

Files created by the build process are put into the */build* directory:

- **build/ableplayer.js** - 
  the default build of *ableplayer.js*
- **build/ableplayer.dist.js** - 
  a build of *ableplayer.js* without console logging
- **build/ableplayer.min.js** - 
  a minified version of the *dist* file
- **build/ableplayer.min.css** - 
  a minified version of the *styles/ableplayer.css* file
 
 
  [examples]: http://ableplayer.github.io/ableplayer/tests/
  [jQuery]: http://jquery.com/
  [Modernizr]: http://modernizr.com/
  [jquery.cookie]: https://github.com/carhartl/jquery-cookie
  [JW Player]: http://www.jwplayer.com/
  [WebAIM’s 2014 Screen Reader User Survey]: http://webaim.org/projects/screenreadersurvey5/#browsers
  [Configuring MIME Types in IIS 7]: http://technet.microsoft.com/en-us/library/17bda1f4-8a0d-440f-986a-5aaa9d40b74c.aspx
  [How to add MIME Types with IIS7 Web.config]: http://blogs.iis.net/bills/archive/2008/03/25/how-to-add-mime-types-with-iis7-web-config.aspx
  [npm]: https://www.npmjs.com/
  [Grunt]: http://gruntjs.com/
  [Signing Books for the Deaf]: http://www.sign-lang.uni-hamburg.de/signingbooks/
  [Filming the Signer]: http://www.sign-lang.uni-hamburg.de/signingbooks/sbrc/grid/d71/guide12.htm
  [Editing the Signer]: http://www.sign-lang.uni-hamburg.de/signingbooks/sbrc/grid/d71/guide13.htm

