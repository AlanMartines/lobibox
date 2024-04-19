# Lobibox
Responsive jQuery notification plugin written from scratch.

[View Demo](http://lobianijs.com/site/lobibox-responsive-jquery-messagebox-and-notification-plugin-available-for-commercial-and-non-commercial-usages.html)

### Description

##### Lobibox is divided into two parts

- Messageboxes
- Notifications

#### Messageboxes

*   Lobibox messagesboxes can be modal and not modal
*   Possibility to show multiple messages
*   Use any available animation class for showing and hiding messageboxes
*   Every message can be draggable (On small screens dragging is disabled)
*   You can show
    *   **messagesboxes in different colors and icons**
    *   **confirm message**
    *   **one line prompt** (Any HTML5 input type can be used in prompt window. Such as: text, color, date, datetime, email, number, range etc)
    *   **multiline prompt**
    *   **Progress messagebox**. Lobibox comes with default progress style but you can use bootstrap or any other style progress bar.
    *   **custom content window with ajax support with custom action buttons**
*   Every message is an instance of plugin. You can easily grab the instance and attach events or call methods directly on the instance.

#### Notifications

*   Different color support
*   Possibility to show in any corners of the screen
*   Delay
*   Show delay indicator
*   Show with image
*   Sound support
*   Size support. You can show notifications of different size

### Installation and dependecies

Lobibox is only depended on jQuery. But for best visual result and icons it's highly recommended to include bootstrap.css 

### 1. Include necessary css/js files

```html
<!DOCTYPE html>
<html>
   <head>
      <!--Include this css file in the <head> tag -->
      <link rel="stylesheet" href="bootstrap/dist/css/bootstrap.min.css"/>
      <link rel="stylesheet" href="dist/css/Lobibox.min.css"/>
   </head>
   
   <body>
      ...
      <!--Include these script files in the <head> or <body> tag-->
      <script src="lib/jquery.1.11.min.js"></script>
      <script src="dist/js/Lobibox.min.js"></script>
      <!-- If you do not need both (messageboxes and notifications) you can inclue only one of them -->
      <!-- <script src="dist/js/messageboxes.min.js"></script> -->
      <!-- <script src="dist/js/notifications.min.js"></script> -->
   </body>
</html>
```

### 2. Call plugin method to show messageboxes or notifications

### Messageboxes

#### Confirm

    Lobibox.confirm({
    ... //Options
    });
    

#### Alert

    Lobibox.alert(
    'error|success|warning|info', // Any of the following
    {
        ... //Options
    }
    );
    

#### Prompt

    Lobibox.prompt(
    '', // Any HTML5 input type is valid
    {
        ... //Options
    }
    );
    

#### Progress

    Lobibox.progress({
    ... //Options
    });
    

#### Window

    Lobibox.window({
    ... //Options
    });
    

### Options

#### Default options for all messageboxes

    horizontalOffset: 5,                //If the messagebox is larger (in width) than window's width. The messagebox's width is reduced to window width - 2 * horizontalOffset
    verticalOffset: 5,                  //If the messagebox is larger (in height) than window's height. The messagebox's height is reduced to window height - 2 * verticalOffset
    width: 600,
    height: 'auto',                     // Height is automatically calculated by width
    closeButton: true,                  // Show close button or not
    draggable: false,                   // Make messagebox draggable
    customBtnClass: 'lobibox-btn lobibox-btn-default', // Class for custom buttons
    modal: true,
    debug: false,
    buttonsAlign: 'center',             // Position where buttons should be aligned
    closeOnEsc: true,                   // Close messagebox on Esc press
    delayToRemove: 200,                 // Time after which lobibox will be removed after remove call. (This option is for hide animation to finish)
    delay: false,                       // Time to remove lobibox after shown
    baseClass: 'animated-super-fast',   // Base class to add all messageboxes
    showClass: 'zoomIn',                // Show animation class
    hideClass: 'zoomOut',               // Hide animation class
    iconSource: 'bootstrap',            // "bootstrap" or "fontAwesome" the library which will be used for icons
    
    //Overriding default options
    Lobibox.base.DEFAULTS = $.extend({}, Lobibox.base.DEFAULTS, {
    ... //override any options from default options
    });

\-->

#### Available options for all messageboxes

    Lobibox.base.OPTIONS = {
    //DO NOT change this value. Lobibox depended on it
    bodyClass       : 'lobibox-open',
    //DO NOT change this object. Lobibox is depended on it
    modalClasses : {
        'error'     : 'lobibox-error',
        'success'   : 'lobibox-success',
        'info'      : 'lobibox-info',
        'warning'   : 'lobibox-warning',
        'confirm'   : 'lobibox-confirm',
        'progress'  : 'lobibox-progress',
        'prompt'    : 'lobibox-prompt',
        'default'   : 'lobibox-default',
        'window'    : 'lobibox-window'
    },
    //This is option how buttons can be shown. What are buttonsAlign option available values
    buttonsAlign: ['left', 'center', 'right'],
    //You can change the title or class of buttons from here or use the same structure object for button when creating messagebox
    //closeOnClick : true will close the messagebox when clicking this type of button. Set it to false not to close messagebox when clicking on it
    buttons: {
        ok: {
            'class': 'lobibox-btn lobibox-btn-default',
            text: 'OK',
            closeOnClick: true
        },
        cancel: {
            'class': 'lobibox-btn lobibox-btn-cancel',
            text: 'Cancel',
            closeOnClick: true
        },
        yes: {
            'class': 'lobibox-btn lobibox-btn-yes',
            text: 'Yes',
            closeOnClick: true
        },
        no: {
            'class': 'lobibox-btn lobibox-btn-no',
            text: 'No',
            closeOnClick: true
        }
    },
    icons: {
        bootstrap: {
            confirm: 'glyphicon glyphicon-question-sign',
            success: 'glyphicon glyphicon-ok-sign',
            error: 'glyphicon glyphicon-remove-sign',
            warning: 'glyphicon glyphicon-exclamation-sign',
            info: 'glyphicon glyphicon-info-sign'
        },
        fontAwesome: {
            confirm: 'fa fa-question-circle',
            success: 'fa fa-check-circle',
            error: 'fa fa-times-circle',
            warning: 'fa fa-exclamation-circle',
            info: 'fa fa-info-circle'
        }
    }
    };
    
    
    //Overriding default options
    Lobibox.base.OPTIONS = $.extend({}, Lobibox.base.OPTIONS, {
    ... //override any options except those above which is written "DO NOT change"
    });
    
    

#### Default options for confirm

    title           : 'Question',
    width           : 500,
    
    //Overriding default options
    Lobibox.confirm.DEFAULTS = $.extend({}, Lobibox.confirm.DEFAULTS, {
    ... //override any options from default options
    });
    

#### Default options for prompt

    width: 400,
    attrs : {},         // Plain object of any valid attribute of input field
    value: '',          // Value which is given to textfield when messagebox is created
    multiline: false,   // Set this true for multiline prompt
    lines: 3,           // This works only for multiline prompt. Number of lines
    type: 'text',       // Prompt type. Available types (text|number|color)
    label: ''           // Set some text which will be shown exactly on top of textfield
    required: true,
    errorMessage: 'The field is required'
    
    //Overriding default options
    Lobibox.prompt.DEFAULTS = $.extend({}, Lobibox.prompt.DEFAULTS, {
    ... //override any options from default options
    });
    

#### Default options for alert

    
    Lobibox.alert.DEFAULTS = {
    warning: {
        title: 'Warning'
    },
    info:{
        title: 'Information'
    },
    success: {
        title: 'Success'
    },
    error: {
        title: 'Error'
    }
    };
    
    //Overriding default options
    Lobibox.alert.DEFAULTS = $.extend({}, Lobibox.alert.DEFAULTS, {
    ... //override any options from default options
    });
    

#### Default options for progress

    width               : 500,
    showProgressLabel   : true,     // Show percentage of progress
    label               : '',       // Show progress label
    progressTpl         : false,    //Template of progress bar

#### Default options for window

    width           : 480,
    height          : 600,
    content         : '',       // HTML Content of window
    url             : '',       // URL which will be used to load content
    draggable       : true,     // Override default option
    autoload        : true,     // Auto load from given url when window is created
    loadMethod      : 'GET',    // Ajax method to load content
    showAfterLoad   : true,     // Show window after content is loaded or show and then load content
    params          : {}        // Parameters which will be send by ajax for loading content
    
    //Overriding default options
    Lobibox.window.DEFAULTS = $.extend({}, Lobibox.window.DEFAULTS, {
    ... //override any options from default options
    });
    

### Methods

In order to call methods, first you must get the instance of the messagebox.

There are two ways to get the instance of the messagebox

    // 1. Save the instance in variable when showing messagebox
    var lobibox = Lobibox.confirm({
    msg         : "Are you sure you want to delete this user?"
    });
    // 2. Or you can select the lobibox message element and get instance by data attribute
    var lobibox = $('.lobibox-confirm').data('lobibox');
    
    // And you can call any avaiable method
    lobibox.hide();
    lobibox.show();
    lobibox.setWidth(600);
    lobibox.setPosition(200, 400);
    lobibox.setTitle('New title');
    

#### [](#methods-for-all-messageboxes)Methods for all messageboxes

Name

Parameters

Return type

Description

hide \- Return `Instance`

Parameters `none`

`Instance`

Hide the messagebox

destroy \- Return `Instance`

Parameters `none`

`Instance`

Removes the messagebox from document

setWidth(width) \- Return `Instance`

Parameters

_width_ - `Integer`, `REQUIRED` new width of messagebox

`Instance`

Set the width of messagebox

setHeight(height) \- Return `Instance`

Parameters

_height_ - `Integer`, `REQUIRED` new height of messagebox

`Instance`

Set the height of messagebox

setSize(width, height) \- Return `Instance`

Parameters

_width_ - `Integer`, `REQUIRED` new width of messagebox

_height_ - `Integer`, `REQUIRED` new height of messagebox

`Instance`

Set the width and height of messagebox

setPosition(left, top) \- Return `Instance`

Parameters

_left_ - `(Integer|String)`, `REQUIRED` left coordinate of messsagebox or string representaing position. Available: `('top', 'center', 'bottom')`

_top_ - `Integer`, `OPTIONAL` Top coordinate of messagebox

`Instance`

Set position of messagebox

setTitle(title) \- Return `Instance`

Parameters

_title_ - `String`, `REQUIRED` new title of messagebox

`Instance`

Set the title of messagebox

getTitle \- Return `String`

Parameters `none`

`String`

Get the title of messagebox

show \- Return `Instance`

Parameters `none`

`Instance`

Show messagebox

\-->

#### [](#methods-for-prompt)Methods for prompt

Name

Parameters

Return type

Description

setValue(val) \- Return `Instance`

Parameters

_val_ - `String`, `REQUIRED` value of input

`Instance`

Set value of input

getVaue \- Return `String`

Parameters `none`

`String`

Get value of input

#### [](#methods-for-progress)Methods for progress

Name

Parameters

Return type

Description

setProgress(progress) \- Return `Instance`

Parameters

_progress_ - `Integer`, `REQUIRED` progress value

`Instance`

Set progress value

getProgress \- Return `Integer`

Parameters `none`

`Integer`

Get progress value

#### [](#methods-for-window)Methods for window

Name

Parameters

Return type

Description

setParams(params) \- Return `Instance`

Parameters

_params_ - `Object`, `REQUIRED` new params

`Instance`

Setter method for `params` option

getParams \- Return `Object`

Parameters `none`

`Object`

Getter method for `params`

setLoadMethod(method) \- Return `Instance`

Parameters

_method_ - `String`, `REQUIRED` new method

`Instance`

Setter method of `loadMethod` option

getLoadMethod \- Return `String`

Parameters `none`

`String`

Getter method for `loadMethod` option

setContent(content) \- Return `Instance`

Parameters

_content_ - `String`, `REQUIRED` new content

`Instance`

Setter method of `content` option. Change the content of window

getContent \- Return `String`

Parameters `none`

`String`

Getter method of `content` option

setUrl(url) \- Return `Instance`

Parameters

_url_ - `String`, `REQUIRED` new url

`Instance`

Setter method of `url` option

getUrl \- Return `String`

Parameters `none`

`String`

Getter method of `url` option

load(callback) \- Return `Instance`

Parameters

_callback_ - `Function`, `OPTIONAL` callback function

`Instance`

Loads content to window by ajax from specific url

### Events

#### Using events

    Lobibox.alert('info', {
    onShow: function(lobibox){
    
    }
    });
    

#### [](#events-for-all-messageboxes)Common events for all types messagebox

Name

Parameters

Description

onShow

Parameters:

`Lobibox` - instance of plugin

Before messagebox is shown

shown

Parameters:

`Lobibox` - instance of plugin

After messagebox is shown

beforeClose

Parameters:

`Lobibox` - instance of plugin

Before messagebox is closed

hidden

Parameters:

`Lobibox` - instance of plugin

After messagebox is closed

#### [](#events-for-progress)Progress messagebox event

Name

Parameters

Description

progressUpdated

Parameters:

`Lobibox` - instance of plugin

When progressbar progress is changed

progressCompleted

Parameters:

`Lobibox` - instance of plugin

When progressbar progress is completed

### Examples

Confirm

    Lobibox.confirm({
    msg: "Are you sure you want to delete this user?",
    });
    

Show Error Show Success Show info Show Warning

    Lobibox.alert(type, //AVAILABLE TYPES: "error", "info", "success", "warning"
    {
    msg: "Lorem ipsum dolor sit amet byron frown tumult minstrel wicked clouded bows columbine full"
    });
    

Prompt

    Lobibox.prompt('text', //Any input type will be valid
    {
    title: 'Please enter username',
    //Attributes of <input>
    attrs: {
        placeholder: "Username"
    }
    });
    

Progress

    Lobibox.progress({
    title: 'Please wait',
    label: 'Uploading files...',
    onShow: function ($this) {
        var i = 0;
        var inter = setInterval(function () {
            window.console.log(i);
            if (i > 100) {
                inter = clearInterval(inter);
            }
            i = i + 0.1;
            $this.setProgress(i);
        }, 10);
    }
    });
    

Bootstrap progress

    Lobibox.progress({
    title: 'Please wait',
    label: 'Uploading files...',
    progressTpl : '<div; class="progress lobibox-progress-outer">\n\
                <div class="progress-bar progress-bar-danger progress-bar-striped lobibox-progress-element" data-role="progress-text" role="progressbar"></div>\n\
                </div>',
    onShow: function ($this) {
        var i = 0;
        var inter = setInterval(function () {
            window.console.log(i);
            if (i > 100) {
                inter = clearInterval(inter);
            }
            i = i + 0.1;
            $this.setProgress(i);
        }, 10);
    }
    });
    

Window

    Lobibox.window({
    title: 'Window title',
    content: '...'
    });
    

### Custom buttons

Error

\-->

     Lobibox.alert('error', {
    msg: 'This is an error message',
    //buttons: ['ok', 'cancel', 'yes', 'no'],
    //Or more powerfull way
    buttons: {
        ok: {
            'class': 'btn btn-info',
            closeOnClick: false
        },
        cancel: {
            'class': 'btn btn-danger',
            closeOnClick: false
        },
        yes: {
            'class': 'btn btn-success',
            closeOnClick: false
        },
        no: {
            'class': 'btn btn-warning',
            closeOnClick: false
        },
        custom: {
            'class': 'btn btn-default',
            text: 'Custom'
        }
    },
    callback: function(lobibox, type){
        var btnType;
        if (type === 'no'){
            btnType = 'warning';
        }else if (type === 'yes'){
            btnType = 'success';
        }else if (type === 'ok'){
            btnType = 'info';
        }else if (type === 'cancel'){
            btnType = 'error';
        }
        Lobibox.notify(btnType, {
            size: 'mini',
            msg: 'This is ' + btnType +' message'
        });
    }
    });
    

### Disable icon

Button

    Lobibox.confirm({
    iconClass: false,
    msg: 'Are you sure?'
    });
    

### Advanced usage of Lobibox.window

Window

    Lobibox.window({
    title: 'Window title',
    //Available types: string, jquery object, function
    content: function(){
        return $('.container');
    },
    url: 'https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.css',
    autoload: false,
    loadMethod: 'GET',
    //Load parameters
    params: {
        param1: 'Lorem',
        param2: 'Ipsum'
    },
    buttons: {
        load: {
            text: 'Load from url'
        },
        close: {
            text: 'Close',
            closeOnClick: true
        }
    },
    callback: function($this, type, ev){
        if (type === 'load'){
            $this.load(function(){
                //Do something when content is loaded
            });
        }
    }
    });
    

### Callbacks

All popup boxes have `callback` option

Confirm

    Lobibox.confirm({
    msg: "Are you sure you want to delete this user?",
    callback: function ($this, type, ev) {
        //Your code goes here
    }
    });
    

Popup type Confirm Alert Prompt Progress

#### [Common parameters](#common-fieldset-wrapper)

title 

Base class (default)

Show class

Hide class

Message

Width

Height

 Close button

 Draggable

 Modal

 Close on escape

#### [Confirm options](#confirm-options)

Icon Class 

#### [Alert options](#alert-options)

Alert type Success Error Info Warning

Icon Class 

#### [Prompt options](#prompt-options)

Type 

Placeholder 

Value 

Label 

 Multiline

Lines (For multiline) 

#### [Progress options](#progress-options)

Progress does not update itself.

But you can implement it easily when uploading or waiting something

Label

 Progress label

Create popup

Notifications
-------------

### Basic usage

    Lobibox.notify(
    'warning',  // Available types 'warning', 'info', 'success', 'error'
    {
        ...
    }
    );
    

### Options

#### Default options for lobibox notifications

    title: true,                // Title of notification. Do not include it for default title or set custom string. Set this false to disable title
    size: 'normal',             // normal, mini, large
    soundPath: 'src/sounds/',   // The folder path where sounds are located
    soundExt: '.ogg',           // Default extension for all sounds
    showClass: 'zoomIn',        // Show animation class.
    hideClass: 'zoomOut',       // Hide animation class.
    icon: true,                 // Icon of notification. Leave as is for default icon or set custom string
    msg: '',                    // Message of notification
    img: null,                  // Image source string
    closable: true,             // Make notifications closable
    delay: 5000,                // Hide notification after this time (in miliseconds)
    delayIndicator: true,       // Show timer indicator
    closeOnClick: true,         // Close notifications by clicking on them
    width: 400,                 // Width of notification box
    sound: true,                // Sound of notification. Set this false to disable sound. Leave as is for default sound or set custom soud path
    position: "bottom right"    // Place to show notification. Available options: "top left", "top right", "bottom left", "bottom right"
    iconSource: "bootstrap"     // "bootstrap" or "fontAwesome" the library which will be used for icons
    rounded: false,             // Whether to make notification corners rounded
    messageHeight: 60,          // Notification message maximum height. This is not for notification itself, this is for .lobibox-notify-msg
    pauseDelayOnHover: true,    // When you mouse over on notification, delay will be paused, only if continueDelayOnInactiveTab is false.
    onClickUrl: null,           // The url which will be opened when notification is clicked
    showAfterPrevious: false,   // Set this to true if you want notification not to be shown until previous notification is closed. This is useful for notification queues
    continueDelayOnInactiveTab: true, // Continue delay when browser tab is inactive
    
    //Overriding default options
    Lobibox.notify.DEFAULTS = $.extend({}, Lobibox.notify.DEFAULTS, {
    ... //override any options from default options
    });
    
    

#### Available options for lobibox notifications

    Lobibox.notify.OPTIONS = {
    'class': 'animated-fast',
    //You can override options for large notifications from here
    large: {
        width: 500,
        messageHeight: 96
    },
    //You can override options for small notifications from here
    mini: {
        'class': 'notify-mini',
        messageHeight: 32
    },
    //Default options of different style notifications
    default: {
        'class': 'lobibox-notify-default',
        'title': 'Default',
        sound: false
    },
    success: {
        'title': 'Success',
        'icon': 'glyphicon glyphicon-ok-sign',
        sound: 'sound2.mp3'
    },
    error: {
        'class': 'lobibox-notify-error',
        'title': 'Error',
        sound: 'sound4.mp3'
    },
    warning: {
        'class': 'lobibox-notify-warning',
        'title': 'Warning',
        sound: 'sound5.mp3'
    },
    info: {
        'class': 'lobibox-notify-info',
        'title': 'Information',
        sound: 'sound6.mp3'
    }
    };
    
    //Overriding default options
    Lobibox.notify.OPTIONS = $.extend({}, Lobibox.notify.OPTIONS, {
    ... //override any options from default options
    });
    

### Methods

Name

Parameters

Return type

Description

remove \- Return `Instance`

Parameters `none`

`Instance`

Delete the notification

### Events

#### Using events

    Lobibox.notify('info', {
        onClick: function(){
            // your code goes here
        }
    });
    

Name

Parameters

Description

onClick new

Parameters:

`jQuery.Event` - jquery event

When you click on notification

### Examples

#### [](#notification-pauseDelayOnHover)Pause delay of notification mouse over new

Default

    Lobibox.notify('default', {
        pauseDelayOnHover: true,
        continueDelayOnInactiveTab: false,
        msg: 'Lorem ipsum dolor sit amet hears farmer indemnity inherent.'
    });

#### [](#notification-examples-onClickUrl)Open url on notification click new

Default

    Lobibox.notify('default', {
        onClickUrl: 'http://google.com',
        msg: 'Lorem ipsum dolor sit amet hears farmer indemnity inherent.'
    });

#### [](#notification-examples-onClickUrl)Show notification after previous is closed new

Default

    Lobibox.notify('default', {
        showAfterPrevious: true,
        msg: 'Lorem ipsum dolor sit amet hears farmer indemnity inherent.'
    });

#### [](#notification-examples-onClickUrl)Continue delay even when browser tab is not active new

Default

    Lobibox.notify('default', {
        continueDelayOnInactiveTab: true,
        msg: 'Lorem ipsum dolor sit amet hears farmer indemnity inherent.'
    });

#### [](#notification-examples-rounded-corners)Rounded corners

Default Info Warning Error Success

    Lobibox.notify(type, {
        ...
        size: 'mini',
        rounded: true,
        delayIndicator: false,
        msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

#### [](#notification-examples-position-center)Position center

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    rounded: true,
    delay: false,
    position: 'center top', //or 'center bottom'
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

#### [](#notification-examples-different-position)Different position

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    rounded: true,
    delay: false,
    position: {
        left: number, top: number
    },
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

#### [](#notification-examples-basic)Basic notifications Can be closed by clicking on it

Default Info Warning Error Success

    Lobibox.notify(type, {
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes. Slight fallen one opportunity dyspepsia, puzzled quickening throbbing row worm numerous sagittis wreaths.'
    });
    

#### [](#notification-examples-with-image)With image

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    img: '...', //path to image
    });
    

#### [](#notification-examples-disable-sound)Disable sound

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    sound: false,
    });
    

#### [](#notification-examples-custom)Custom title

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    title: 'Custom title',
    });
    

#### [](#notification-examples-without-icon-image)Without icon and image

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    icon: false,
    });
    

#### [](#notification-examples-increase-delay)Increase delay time

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    delay: 15000,  //In milliseconds
    });
    

#### [](#notification-examples-sticky)Sticky (without delay)

Default Info Warning Error Success

(adsbygoogle = window.adsbygoogle || \[\]).push({});

    Lobibox.notify(type, {
    ...
    delay: false,
    });
    

#### [](#notification-examples-alternative-position)Alternative position

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    position: 'bottom right' //AVAILABLE OPTIONS: 'top left', 'top right', 'bottom left', 'bottom right'
    });
    

#### [](#notification-examples-change-width)Change width

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    width: 400 //Any Integer
    });
    

#### [](#notification-examples-change-animation)Change Animation

For animation Lobibox is depended on [animate.css](https://web.archive.org/web/20160930070629/https://daneden.github.io/animate.css/). You can use any animate.css classes

By default `.animated` class is added

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    showClass: 'fadeInDown',
    hideClass: 'fadeUpDown',
    width: 400 //Any Integer
    });
    

Large Notifications
-------------------

Large notifications

*   are sticky (they will not be closed automatically)
*   can be closed only by clicking close button
*   does not have delay
*   are larger in width

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'large',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

### [](#notification-large-with-image)With Image

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    img: '...',
    size: 'large',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

[](#notification-large-alternative-position)Alternative position

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'large',
    position: 'bottom left',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

[](#notification-large-change-animation)Change animation \-->

Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'large',
    showClass: 'fadeInDown',
    hideClass: 'fadeUpDown',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

Mini notifications
------------------

For mini notifications icon and image is shown on small size and title is disabled by default. Although you can enable it by giving `title` parameter when initializing.

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

### [](#notification-mini-with-image)With image

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    img: '...',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

### [](#notification-mini-without-icon)Without icon

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    icon: false,
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

### [](#notification-mini-with-title)With title

Default Info Warning Error Success

    Lobibox.notify(type, {
    ...
    size: 'mini',
    title: 'Lorem ipsum',
    msg: 'Lorem ipsum dolor sit amet against apennine any created, spend loveliest, building stripes.'
    });
    

### Release Notes

*   [](#release-notes-version-1-2-4)v1.2.4
*   \[new\] Added `pauseDelayOnHover` option. When you mouse over on notification, delay will be paused, only if `continueDelayOnInactiveTab` is false.
*   \[new\] Added `continueDelayOnInactiveTab` option. Continue delay when browser tab is inactive.
*   \[new\] Added `onClickUrl` option. The url which will be opened when notification is clicked.
*   \[new\] Added `showAfterPrevious` option. Set this to true if you want notification not to be shown until previous notification is closed. This is useful for notification queues.
*   \[new\] Added `continueDelayOnInactiveTab` option. Continue delay when browser tab is inactive.

*   [](#release-notes-version-1-2-3)v1.2.3
*   Bower support added
*   Added default (dark) style notification
*   New (`rounded`) parameter in notifications to make notification corners rounded
*   Changed default show animation in notifications
*   Align icon/image always vertically center
*   New (`messageHeight`) property to restrict notification message not to increase too much in height
*   Option notification to be closable but hide close button. Thus notification will be closed by clicking on it
*   Method `Lobibox.notify.closeAll()` to close all notifications
*   Option to show notification in top center and bottom center
*   Option to position notification at any place by `left` and `top` coordinates
*   New (`delay`) option to close messagebox automatically
*   Fixed `shown` event bug. Now it is triggered at correct time
*   Validate prompt and show error message if it is empty
*   Non draggable messageboxes are always in center of window and their size (width, height) is always <= to window size (width, height)

Disqus seems to be taking longer than usual. [Reload](#)?

### For documentation and examples visit the plugin's [home page](http://lobianijs.com/site/lobibox-responsive-jquery-messagebox-and-notification-plugin-available-for-commercial-and-non-commercial-usages.html)
