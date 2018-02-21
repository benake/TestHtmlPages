[Skip to content](#start-of-content)

[](https://git.corp.adobe.com/)

Enterprise

[This
repository](/world-readiness/globalization-shared/blob/master/guidelines/android_world_readiness_guidelines.html)

-   [Pull requests](/pulls)
-   [Issues](/issues)
-   [Gist](https://git.corp.adobe.com/gist)

-   [](/notifications)
-   [](/new)
-   [![@benake](https://git.corp.adobe.com/avatars/u/5584?s=40)](/benake)
    Signed in as **benake**
    [Your profile](/benake) [Your stars](/benake?tab=stars)
    [Explore](/explore)
    [Help](https://help.github.com/enterprise/2.10/user)
    [Settings](/settings/profile)
    Sign out

Sign out

**Useful links:** [Self-service
portal](https://developer.paas.corp.adobe.com) |
[Wiki](https://wiki.corp.adobe.com/display/git/Home) |
[GitHubInsights](https://git.corp.adobe.com/pages/SCM/GitHubInsights/) |
[Activity](https://git.corp.adobe.com/dashboards/overview) |
[Stage](https://github-stage.corp.adobe.com) *(new release preview and
testing only)*

-   [](/world-readiness/globalization-shared/subscription)
    Watch [0](/world-readiness/globalization-shared/watchers)
    Notifications
    Not watching Be notified when participating or @mentioned.
    Watch
    Watching Be notified of all conversations.
    Unwatch
    Ignoring Never be notified.
    Stop ignoring
-   Unstar
    [0](/world-readiness/globalization-shared/stargazers)
    Star
    [0](/world-readiness/globalization-shared/stargazers)
-   [](#fork-destination-box "Fork your own copy of world-readiness/globalization-shared to your account")

    Fork

    Where should we fork this repository? {.facebox-header data-facebox-id="facebox-header"}
    -------------------------------------

    ![Loading](https://git.corp.adobe.com/images/spinners/octocat-spinner-128.gif)

    [0](/world-readiness/globalization-shared/network)

[world-readiness](/world-readiness)/**[globalization-shared](/world-readiness/globalization-shared)**

[](/world-readiness/globalization-shared)

Code [](/world-readiness/globalization-shared/issues)

Issues 0 [](/world-readiness/globalization-shared/pulls)

Pull requests 0 [](/world-readiness/globalization-shared/projects)

Projects 0 [](/world-readiness/globalization-shared/wiki)

Wiki [](/world-readiness/globalization-shared/pulse)

Pulse [](/world-readiness/globalization-shared/graphs)

Graphs

[Permalink](/world-readiness/globalization-shared/blob/846271ab8e6d60f49c837115faad71839f2d4827/guidelines/android_world_readiness_guidelines.html)

*Branch:* master

Switch branches/tags

-   [Branches](#)
-   [Tags](#)

[](/world-readiness/globalization-shared/blob/master/guidelines/android_world_readiness_guidelines.html)

master

Nothing to show

Nothing to show

[Find file](/world-readiness/globalization-shared/find/master)

Copy path

[globalization-shared](/world-readiness/globalization-shared)/[guidelines](/world-readiness/globalization-shared/tree/master/guidelines)/**android\_world\_readiness\_guidelines.html**

Fetching contributors…

![](https://git.corp.adobe.com/images/spinners/octocat-spinner-32-EAF2F5.gif)
Cannot retrieve contributors at this time

[Raw](/world-readiness/globalization-shared/raw/master/guidelines/android_world_readiness_guidelines.html)
[Blame](/world-readiness/globalization-shared/blame/master/guidelines/android_world_readiness_guidelines.html)
[History](/world-readiness/globalization-shared/commits/master/guidelines/android_world_readiness_guidelines.html)

[](https://desktop.github.com)

647 lines (516 sloc) 33.8 KB

  -- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
     \<html\>
     \<head\>
     \<meta http-equiv="Content-Type" content="text/html;charset=utf-8"\>
     \<meta name='title' content='Guidelines for creating world-ready Android applications'\>
     \<meta name='description' content=''\>
     \<meta name='keywords' content='guidelines for Android internationalization'\>
     \<meta name='author' content='Kaho Lo, Sudhakar Pandey'\>
     \<meta name='creation\_date' content='yyyy-mm-dd'\>
     \<meta name='update\_date' content='yyyy-mm-dd'\>
     \<meta name='language' content='en'\>
     
     \<link rel="stylesheet" type="text/css" href = "./includes/guidelines.css" /\>
     \<link rel="stylesheet" type="text/css" href="http://code.jquery.com/ui/1.10.4/themes/smoothness/jquery-ui.css" /\>
     \<link rel="stylesheet" type="text/css" href="guidelines.css" /\>
     \<script src="http://code.jquery.com/jquery-1.10.2.js"\>\</script\>
     \<script src="http://code.jquery.com/ui/1.10.4/jquery-ui.js"\>\</script\>
     \<title\>Guidelines for creating world-ready Android applications\</title\>
     \</head\>
     
     \<body\>
     
     \<h1 class="category\_description\_article\_header"\>Guidelines for creating world-ready Android applications\</h1\>
     \<br\>
     
     \<a name="Introduction"\>\</a\>
     \<h2\>Introduction\</h2\>
     
     \<div\>
     This article provides internationalization guidelines from technical requirement and implementation perspective, to the product teams developing web applications and services. Please direct any questions to \<a href="mailto:world-readiness@adobe.com"\>DL-world-readiness\</a\>.
     \</div\>
     
     \<a name="UI Resource Externalization"\>\</a\>
     \<h2\>UI Resource Externalization\</h2\>
     
     \<a name="UI Resource Externalization : General"\>\</a\>
     \<h3\>General\</h3\>
     Android framework provides an elegant mechanism to localize various resources in the App to be locale specific. In android not only strings but other contents can be localized as well. The main resource type which should be taken in consideration for localization are:
     \<ul\>
     \<li\>Strings\</li\>
     \<li\>Layouts\</li\>
     \<li\>Graphics/Images\</li\>
     \<li\>Sounds\</li\>
     \</ul\>
     Any other static data that your Android application needs can also be localized in android.
     \<h4\>Android Localization Process\</h4\>
     
     Android loads resources from the res/ folders. There is a specific order in which the resources are loaded by android. For example if the device locale is set to en-US then android will search for the strings in the following order:
     
     \<ol\>
     \<li\>res/values-en-rUS/strings.xml\</li\>
     \<li\>res/values-en/strings.xml\</li\>
     \<li\>res/values/strings.xml\</li\>
     \</ol\>
     The 3rd option is a default value which should be always present, in case the localized file is empty then android falls back to this default value to display the content. For placing your localized resources you should use the following format for the folder names:
     
     \<ul\>
     \<li\>Name the folder as : res/values-&ltlanguage\_part&gt-r&ltoptional\_region\_code&gt\</li\>
     \</ul\>
     The region\_code is optional and can be omitted, following are valid way of naming the localized folders:
     \<ul\>
     \<li\>res/values-en-rUS/strings.xml\</li\>
     \<li\>res/values-en/strings.xml\</li\>
     \</ul\>
     The other resources can be similarly localized e.g for images you can use:
     \<ul\>
     \<li\>res/drawable-en-rUS/images.png\</li\>
     \<li\>res/drawable-en/images.png\</li\>
     \</ul\>
     
     \<h4\>Strings\</h4\>
     English strings that live only in the source code are considered hard-coded strings. All strings should be externalized from the source code. This enables the Globalization team to get them translated into other languages. While the most obvious examples are UI strings such as button labels and error messages, there are other types of strings that should be externalized as well, including:
     \<ul\>
     \<li\>URLs: Localized versions of a particular URL may exist, but even if they don't, it's safer to always externalize them from the beginning in case that ever changes.\</li\>
     \<li\>Product Names: Even if they don't need to be localized, they will be easier to update in a string file than in the source code.\</li\>
     \</ul\>
     \<a name="UI Resource Externalization : Recommendations"\>\</a\>
     \<h3\>Recommendations\</h3\>
     There are various ways for externalizing already present strings in the source code:
     \<h4\>Eclipse:\</h4\>
     \<ul\>
     \<li\>Select the string to be localized and press Alt+Shift+S this will bring up a small window in right bottom corner. Either select the option to externalize the string or press A.\</li\>
     \<li\>One can also press \<b\>Ctrl+1\</b\> after selecting the text this will bring the context menu and then select \<b\>Externalize String\</b\>\</li\>
     \<li\>Or after selecting the text/string from the Refactor menu select Android and then select Externalize String: \<b\>Refactor-\>Android-\>Externalize\</b\>\</li\>
     \</ul\>
     \<h4\>Android Studio:\</h4\>
     \<ul\>
     \<li\>Select the string and press Alt+Enter in the appearing menu, select Add a string resource.\</li\>
     \</ul\>
     \<br\>
     Following is the recommended way of refer to the localized versions of strings in android project:
     \<ul\>
     \<li\>\<b\>In XML\</b\>\</li\>
     
     
     When referring strings in xml files like in layouts.xml use the following recommended way as described below:
     \<ul\>
     \<li\>someAttribute=“@string/name\_of\_string”\</li\>
     \<li\>E.g.:- android:text=“@string/name\_of\_string”\</li\>
     \</ul\>
     
     \<br\>
     
     \<li\>\<b\>In Java Code\</b\>\</li\>
     While referring to strings in Java code instead of hard coding “Text\_to\_use” use \<b\>\<i\>getString(R.string.”id\_Text\_to\_use”)\</i\>\</b\>
     \<ul\>
     \<li\>E.g:- TextView.setText(“HelloWorld”); wrong way \<br\>
     TextView.setText(getString(R.id.welcome\_msg))
     \</li\>
     \</ul\>
     \<!-- The ul for the In XML needs to be closed--\>
     
     \</ul\>
     
     Example strings.xml for en-rUS and de-rDE is shown as below:
     
     \<ul\>
     \<li\>\<b\>en-US\</b\>\</li\>
     
     \<xmp class="code\_sample"\>
     \<?xml version="1.0" encoding="utf-8"?\>
     \<resources\>
     
     \<string name="app\_name"\>TestLocale\</string\>
     \<string name="hello\_world"\>Hello world!\</string\>
     \<string name="action\_settings"\>Settings\</string\>
     \<string name="Test"\>Edit text\</string\>
     \</resources\>
     \</xmp\>
     
     \<li\>\<b\>de-DE\</b\>\</li\>
     
     \<xmp class="code\_sample"\>
     \<?xml version="1.0" encoding="UTF-8"?\>
     \<resources\>
     \<string name="app\_name"\>TestLocale\</string\>
     \<string name="hello\_world"\>Hallo Welt!\</string\>
     \<string name="Test"\>Bearbeiten von text\</string\>
     \<string name="action\_settings"\>Einstellungen\</string\>
     \</resources\>
     \</xmp\>
     \</ul\>
     
     
     \<h4\>Format Strings:\</h4\>You can format your strings for better localization by using parameters in the string.xml file as:
     \<xmp class="code\_sample"\>\<string name="welcome\_messages"\>Hello, %1\$s! You have %2\$d new messages.\</string\>\</xmp\>
     And then refer them in the code as follow:
     \<div class="code\_sample"\>
     Resources res = getResources();\<br\>
     String text = String.format(res.getString(R.string.welcome\_messages), “USERNAME”, 123);
     \</div\>
     
     In this example, the format string has two arguments: %1\$s is a string and %2\$d is a decimal number. The number after %sign is the parameter number which specifies the order in which the arguments supplied by String.format should be used. This makes it easy in case you need to change the order of the parameters in certain locales.
     \<h4\>Example:\</h4\>
     \<xmp class="code\_sample"\>\<string name="welcome\_messages"\>Hello, %1\$s! You have %2\$d new messages.\</string\>
     Hello, USERNAME! You have 123 new messages
     \</xmp\>
     
     \<xmp class="code\_sample"\>\<string name="welcome\_messages"\>Hello, %2\$d! You have %1\$s new messages.\</string\>
     Hello, 123! You have USERNAME new messages
     \</xmp\>
     
     
     \<h4\>Escaping Strings: \</h4\>
     If your strings contain apostrophes or quotes then you need to escape them or enclose them in the other type of enclosing quotes. Following is the recommended way of doing it:
     
     \<xmp class="code\_sample"\>\<string name="good\_example"\>"This'll work"\</string\>
     \<string name="good\_example\_2"\>This\\'ll also work\</string\>
     \</xmp\>
     
     In case you are using % in strings.xml then use should use one of the following way to include this in your strings:
     
     \<xmp class="code\_sample"\>\<string name="Test" formatted="false"\>%a + %a == 2%a\</string\>
     \<string name="Test2"\>\\u0025a + \\u0025a == 2\\u0025a\</string\>
     \</xmp\>
     Either you can specify formatted = “false” or you can replace the occurrence of % with \\u0025a which is the Unicode representation of %.
     
     \<b\>Array References: \</b\>You can also define a String Array in the xml to be used in the code. The syntax for doing this is:
     \<xmp class="code\_sample"\>
     \<?xml version="1.0" encoding="utf-8"?\>
     \<resources\>
     \<string-array
     name="string\_array\_name"\>
     \<item\>text\_string\_1\</item\>
     \<item\>text\_string\_2\</item\>
     \</string-array\>
     \</resources\>
     \</xmp\>
     The &lt;Item&gt; tag defines the individual element of the array and it can refer to other string resource as well. Any apostrophes and quotation marks in the string value needs to be escaped. For referencing the array in application you can use the following code snippet:
     
     \<div class="code\_sample"\>Resources res = getResources();\<br\>
     String[] planets = res.getStringArray(R.array. string\_array\_name);
     \</div\>
     
     \<h4\>Quantity Strings (Plurals): \</h4\>
     Different language handle plurals of nouns or unit expressions differently. Some languages have two forms, like English; some languages have only a single form; and some languages have multiple forms. There are total of six categories under this and depending upon the language these categories are defined to include a particular set/range of integers. The categories are defined by \<b\>Unicode CLDR Plurals Systems\</b\>, you can find more information here:
     \<a href="http://unicode.org/repos/cldr-tmp/trunk/diff/supplemental/language\_plural\_rules.html"\>http://unicode.org/repos/cldr-tmp/trunk/diff/supplemental/language\_plural\_rules.html\</a\>
     \<br\>
     These six categories include: \<b\>"zero", "one”, "two”, "few”,"many”, "other”\</b\>. As has already been explained it depends on language to define 1 or all of these categories. Following is an example from CLDR site:
     \<table style="margin-left:10px; margin-top:5px" border="1"\>
     \<tbody\>\<tr\>
     \<th\>Langauge\</th\>
     \<th\>Category\</th\>
     \<th\>Quantity(n)\</th\>
     \<th\>Rule\</th\>
     \</tr\>
     \<tr\>
     \<td\>Arabic\</td\>
     \<td\>Zero\</td\>
     \<td\>0\</td\>
     \<td\>n-&gt;0\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>One\</td\>
     \<td\>1\</td\>
     \<td\>n-&gt;1\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>Two\</td\>
     \<td\>2\</td\>
     \<td\>n-&gt;2\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>Few\</td\>
     \<td\>3-10, 103-110, 203-210...\</td\>
     \<td\>n mod 100 in 3..10\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>Many\</td\>
     \<td\>11-99, 111-199, 211-299...\</td\>
     \<td\>n mod 100 in 11..99;\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>Other\</td\>
     \<td\>100-102, 200-202, 300-302...;\</td\>
     \<td\>everything else\</td\>
     \</tr\>
     \<tr\>
     \<td\>\<br/\>\</td\>
     \<td\>\<br/\>\</td\>
     \<td\>\<br/\>\</td\>
     \<td\>\<br/\>\</td\>
     \</tr\>
     \<tr\>
     \<td\>English(en)\</td\>
     \<td\>One\</td\>
     \<td\>1\</td\>
     \<td\>n-&gt;0\</td\>
     \</tr\>
     \<tr\>
     \<td\>\</td\>
     \<td\>Other\</td\>
     \<td\>0, 2-999…\</td\>
     \<td\>everything else\</td\>
     \</tr\>
     \</tbody\>\</table\>
     
     
     
     As stated earlier in English there are only two plural forms but for Arabic it defines all the category of the plurals. Therefore in English, a string for zero will be ignored even if the quantity is 0, because 0 isn't grammatically different from 2, or any other number except 1 ("zero books", "one book", "two books", and so on). Conversely, in Korean only the other string will ever be used.\<br\>\<br\>
     \<b\>Example:\</b\>\<br\>
     \<b\>Default strings.xml @ res/values/strings.xml\</b\>
     \<xmp class="code\_sample"\>
     \<?xml version="1.0" encoding="utf-8"?\>
     \<resources\>
     \<plurals name="numberOfSongsAvailable"\>
     \<item quantity="one"\>%d song found.\</item\>
     \<item quantity="other"\>%d songs found.\</item\>
     \</plurals\>
     \</resources\>
     \</xmp\>
     \<b\>Strings.xml @ res/values-pl/strings.xml\</b\>
     \<xmp class="code\_sample"\>
     \<?xml version="1.0" encoding="utf-8"?\>
     \<resources\>
     \<plurals name="numberOfSongsAvailable"\>
     \<item quantity="one"\>Znaleziono %d piosenkę.\</item\>
     \<item quantity="few"\>Znaleziono %d piosenki.\</item\>
     \<item quantity="other"\>Znaleziono %d piosenek.\</item\>
     \</plurals\>
     \</resources\>
     \</xmp\>
     
     \<b\>Referencing in Application:\</b\>
     \<div class="code\_sample"\>
     int count = getNumberOfsongsAvailable();\<br\>
     Resources res = getResources();\<br\>
     String songsFound = res.getQuantityString(R.plurals.numberOfSongsAvailable, count, count);
     \</div\>
     
     
     When using the \<b\>\<i\>getQuantityString()\</i\>\</b\> method, you need to pass the count twice if your string includes string formatting with a number. For example, for the string %d songs found, the first count parameter selects the appropriate plural string and the second count parameter is inserted into the %d placeholder. If your plural strings do not include string formatting, you don't need to pass the third parameter to \<b\>\<i\>getQuantityString.\</i\>\</b\>\<br\>\<br\>
     
     \<b\>\<i\>Note: - You should always include %d in “one” because translator will need to use %d for languages where “one” doesn’t simply mean 1.\</i\>\</b\>
     
     
     \<h4\>Image and Icons\</h4\>
     Image and icons can follow the same logic. If shared, they can live in the default image folder \<b\>"res/drawables"\</b\>. You can also make it locale aware by adapting the same structure as the other resource types.
     \<ol\>
     \<li\>res/drawables-en-rUS\</li\>
     \<li\>res/drawables-en\</li\>
     \<li\>res/drawables\</li\>
     \</ol\>
     
     And in a similar way you can access these resources as \<b\>R.drawable.&lt;images&gt;\</b\> in the code and then android will take care of the locale automatically.
     \<h4\>Layouts\</h4\>
     Similarly, layouts can follow the same logic. Just place all layout files under each locale specific folders but don't forget to always use the default layout folder as a fallback.
     \<ol\>
     \<li\>res/layout-en-rUS\</li\>
     \<li\>res/layout-fr-rFR\</li\>
     \<li\>res/layout\</li\>
     \</ol\>
     
     \<p\>
     Apart from the different locales android also provides a way for providing different layouts to get loaded for Righ to Left languaes just put the specified layout in \<b\>res/layout-ldrtl/&lt;layout.xml&gt;\</b\> where ldrtl means layout-direction-right-to-left.
     \</p\>
     \<br\>
     
     \<img src="./images/layouts.png" align="middle"\>
     \<br\>
     \<b\>\<i\>Note: To enable right-to-left layout features for your app, you must setsupportsRtl to "true" and set targetSdkVersion to 17 or higher.\</i\>\</b\>
     
     
     \<a name="UI"\>\</a\>
     \<h2\>UI\</h2\>
     \<br\>
     
     \<a name="UI : General"\>\</a\>
     \<h3\>General\</h3\>
     UI truncations are some of the most common bugs you will run into after localizing an application. Therefore, it's important to design a UI that is flexible and allows some room to grow.
     
     \<a name="UI : Recommendations"\>\</a\>
     \<h3\>Recommendations\</h3\>
     UI should be designed and sized so that any language can fit without truncations. This means that UI components should be as wide and accommodating as possible while still adhering to the design specifications. Try to foresee future localization needs, such as allowing a label to go onto multiple lines, even if English doesn't require it. Try not to make designs too tight or only just wide enough to fit the English strings. As a rough guideline, expect translations to be at least 20% longer on average. But there are cases where certain languages can be shorter, such as Chinese, or even longer than that average, such as Russian.
     
     In case it is difficult to make a generic layout you can make locale specific layouts and put them in separate res folders as has been described in this documentation.
     \<br\>\<br\>
     Apart from different layouts for different locales you can also use resources corresponding to specific device, specific resolutions, and screen aspect as has been described here in developers guide:
     \<a href="http://developer.android.com/guide/topics/resources/providing-resources.html\#AlternativeResources"\>http://developer.android.com/guide/topics/resources/providing-resources.html\#AlternativeResources\</a\>
     
     \<!-- ------------------ --\>
     \<!--- Local Awareness ---\>
     \<!-- \#\#\#\#\#\#\#\#\#\#\#\#\#\#\# ---\>
     \<h2\>Locale Awareness\</h2\>
     
     \<a name="Locale Awareness : General"\>\</a\>
     \<h3\>General\</h3\>
     If your Android application displays data to the user such as dates, times, calendars, and numbers, currency, etc., then you need to consider making that data locale-aware. This refers to the rules that each locale has for formatting and displaying such data that may be different from US English formats.
     
     \<a name="Locale Awareness : Recommendations"\>\</a\>
     \<h3\>Recommendations\</h3\>
     Use the date, time, and number formatters that Android provides with their APIs. See the links below for more information for specific classes and methods to use.
     
     Our recommendation is to always use locale-aware methods for displaying data that can vary depending on the user's preferred locale. Even if your application is English-only or only localized into certain languages, do not constrict this data to those locales only. Write the code so that these types of data can be displayed in the correct format for whatever locale the user sets in their preferences.\<br\>\<br\>
     
     Note that in the code, when we refer to the current locale, such as \<b\>NumberFormat.getInstance()\</b\>, we are referring to the user's Language settings in the device.
     
     In cases where you need to explicitly pass the Locale Object you can use the following code fragment to get the device’s current locale:\<br\>
     
     \<div class="code\_sample"\>
     Locale current = getResources().getConfiguration().locale;
     \</div\>
     In most of the API this is not needed but for some cases when you need custom date-times this may be required as explained later in this documentation.
     
     \<!-- Work form --\>
     
     \<h4\>Dates and Times\</h4\>
     In the Android SDK, dates and times are managed by the Date class from the \<b\>java.util\</b\> namespace. The current date and time of the device is returned by the \<b\>java.util.Calendar\</b\>.\<br\>\<br\>
     
     \<b\>Localizing Dates:\</b\> Dates can be formatted using an instance of the \<b\>DateFormat\</b\> formatter from the \<b\>java.text\</b\> namespace. You must use the \<b\>DateFormat\</b\> class from the Android SDK in the \<b\>android.text.format\</b\> namespace to get the right formatter for the locale of the device. The following code snippet shows how to get a string with the current date formatted for the device's locale:
     
     \<div class="code\_sample"\>
     // Gets the current date and time\<br\>
     Date currentDate = Calendar.getInstance().getTime();\<br\>\<br\>
     
     // Gets the standard date formatter for the current locale of\<br\>
     // the device\<br\>
     java.text.DateFormat dateFormat;\<br\>
     dateFormat = android.text.format.DateFormat.getDateFormat(this);\<br\>\<br\>
     
     // Formats the current date according to the locale\<br\>
     String formattedCurrentDate = dateFormat.format(currentDate);\<br\>
     \</div\>
     
     \<p\>
     There are three default formats supported for displaying the Date this variation can be accessed by using the following options \<b\>android.text.format.DateFormat.&lt;Options&gt;\</b\>
     \<ol\>
     \<li\>\<b\>getDateFormat(this) : 01/04/2015\</b\>\</li\>
     \<li\>\<b\>getLongDateFormat(this): January 4,2015\</b\>\</li\>
     \<li\>\<b\>getMediumDateFormat(this): Jan 4,2015\</b\>\</li\>
     \</ol\>
     
     All these outputs will be localized depending on the system’s locale settings.
     
     \<b\>Example output: \</b\>
     \</p\>
     \<img src="./images/dates\_loc.png"\>
     
     \<br\>
     \<b\>Localizing Time:\</b\> Times are represented as \<b\>Date\</b\> objects by the Android SDK, they must also be displayed using a formatter returned by the DateFormat class from the \<b\>android.text.format\</b\> namespace. The \<b\>getTimeFormat\</b\> method returns a format that only displays the time of a Date object. The following code snippet show how to get a string with the current time formatted for the device's locale:
     
     \<div class="code\_sample"\>
     \<pre\>\<!--TODO: Font is mismatch remove the pre with br --\>
     // Gets the current date and time
     java.util.Date currentDate = Calendar.getInstance().getTime();
     
     // Gets a date formatter for the current locale of the device
     // that shows times.
     java.text.DateFormat timeFormat;
     timeFormat = android.text.format.DateFormat.getTimeFormat(this);
     
     // Formats the current time according to the locale
     String formattedTime = timeFormat.format(currentDate);
     \</pre\>
     \</div\>
     \<p\>
     \<br\>
     \<b\>Example Output:\</b\>
     \</p\>
     \<img src="./images/time\_loc.png"\>
     
     \<br\>
     \<b\>Custom Date and Time:\</b\> For displaying the date and time in custom format you can use the \<b\>SimpleDateFormat(String format , Lcoale loc)\</b\> ,but this requires you the specify the Locale as an input argument you can pass the device’s current Locale as the second argument to get the custom date and time in user’s locale specific way. For the format strings you can refer to the Android Developers Guide doc located at: \<a href="http://developer.android.com/reference/java/text/SimpleDateFormat.html"\>http://developer.android.com/reference/java/text/SimpleDateFormat.html.\</a\>\<br\>
     
     \<b\>Example Code Snippets:\</b\>
     
     \<div class="code\_sample"\>
     java.text.DateFormat dateFormat;\<br\>
     // Get the current locale\<br\>
     loc = getResources().getConfiguration().locale;\<br\>
     dateFormat = new SimpleDateFormat("dd/MMMM/yyyy", loc);\<br\>
     // Formats the current date according to the locale\<br\>
     String formattedCurrentDate = dateFormat.format(currentDate);\<br\>
     
     \</div\>
     
     
     \<h4\>Numbers\</h4\>
     \<b\>NumberFormat\</b\> helps you to format and parse numbers for any locale. Your code can be completely independent of the locale conventions for decimal points, thousands-separators, or even the particular decimal digits used, or whether the number format is even decimal.\<br\>\<br\>
     
     \<b\>Integers and Decimals:\</b\> Following code snippet shows the use of the \<b\>NumberFormat\</b\> class to get the numbers including integers and decimal numbers in the way they are displayed in different locales.
     
     \<div class="code\_sample"\>
     NumberFormat nFormatter = NumberFormat.getInstance();\<br\>
     nFormatter.format(number);
     \</div\>
     \<p\>
     where number can be float ,or decimal or integer values. Example output for above code is shown as:
     \</p\>
     \<img src="./images/num\_loc.png"\>
     \<br\>
     
     
     \<b\>Percentage:\</b\> Percentages require localization as well, as some locales require a space between the number and the percent symbol, while some do not. Use the \<b\>NumberFormat.getPercentInstance()\</b\> instead.\<br\>\<br\>
     
     Note: This requires the number to be between (0,1) where 0 corresponds to 0% and 1 corresponds to 100% and 0.1257 corresponds to 12.57%.If you specify a number like 53 it will be converted to 5300% instead.For more details please check the API doc at Android Developers at :
     \<a href="http://developer.android.com/reference/java/text/NumberFormat.html\#getPercentInstance()"\>http://developer.android.com/reference/java/text/NumberFormat.html\#getPercentInstance()\</a\>\<br\>\<br\>
     
     \<b\>Example Code Snippet:\</b\>
     
     \<div class="code\_sample"\>
     NumberFormat percentFormat = NumberFormat.getPercentInstance();\<br\>
     String result = percentFormat.format(0.125);
     \</div\>
     
     \<p\>
     \<br\>
     \<b\>Output:\</b\>
     \</p\>
     
     \<img src="./images/perc\_loc.png"\>
     \<br\>
     
     \<b\>Currencies:\</b\> Currencies can be displayed in two formats: \<b\>fully formatted\</b\> and \<b\>partially formatted\</b\>.
     
     \<b\>Fully Formatted:\</b\> In this case both the currency symbol and the numbers get localized in the user’s default locale.The code for doing it is as follows:
     
     \<div class="code\_sample"\>
     NumberFormat defaultFormat = NumberFormat.getCurrencyInstance();\<br\>
     defaultFormat.format(amount)
     \</div\>
     This results in the following output:
     
     \<img src="./images/cur1\_loc.png"\>
     
     \<br\>
     \<b\>Partially Formatted:\</b\> In this format the currency value do not get formatted and only the Currency symbol gets formatted. But in this case you need to provide the ISO Currency code for formatting the amount.
     
     \<div class="code\_sample"\>
     NumberFormat currencyFormat = NumberFormat.getCurrencyInstance();\<br\>\<br\>
     
     // This provides the currency symbol.\<br\>
     Currency currency = Currency.getInstance(isoCurrencyCode);\<br\>\<br\>
     
     // this method - uses default locale to format the currency symbol.\<br\>
     String symbol = currency.getSymbol();\<br\>
     DecimalFormatSymbols decimalFormatSymbols = ((java.text.DecimalFormat) currencyFormat).getDecimalFormatSymbols();\<br\>
     decimalFormatSymbols.setCurrencySymbol(symbol);\<br\>
     ((java.text.DecimalFormat) currencyFormat).setDecimalFormatSymbols(decimalFormatSymbols);\<br\>\<br\>
     
     return currencyFormat.format(amount);
     
     \</div\>
     \<p\>Output of this code is given below:\</p\>\<br\>
     \<img src="./images/cur2\_loc.png"\>
     
     \<h4\>Name Ordering\</h4\>
     
     In some locales, a person's full name is written out with last name (family name, surname) then first name (personal name, given name), instead of the more common first name then last name order. Some examples include, but are not limited to, China, Japan, Korea, Taiwan, and Vietnam. In Android no such API exists till date but \<b\>Adobe Creative SDK\</b\> provides a method with which you can get the current display name of user which will be in accordance with the user name displayed in Creative Cloud account for that particular user. The API to be used for this purpose is \<b\>AdobeAuthUserProfile.getDisplayName ()\</b\>.
     
     \<b\>\<i\>Note: - This method is specific to Adobe Creative SDK and is not part of Android API’s.\</i\>\</b\>
     
     
     
     \<h4\>Locale Sensitive Sorting\</h4\>
     Android has provision for performing locale aware sorting of strings, it is facilitated by the \<b\>Collator\</b\> Class. It follows the \<a href="http://www.unicode.org/"\>Unicode Consortium's\</a\> specifications for the \<a href="http://www.unicode.org/unicode/reports/tr10/"\>Unicode Collation Algorithm (UCA)\</a\>.According to this algorithm there are 4 different levels of strength used in comparisons:
     
     
     \<ol\>
     \<li\>\<b\>PRIMARY strength:\</b\> Typically, this is used to denote differences between base characters (for example, "a" &lt; "b"). It is the strongest difference. For example, dictionaries are divided into different sections by base character.\</li\>
     
     \<li\>\<b\>SECONDARY strength:\</b\> Accents in the characters are considered secondary differences (for example, "as" &lt; "às" &lt;"at"). Other differences between letters can also be considered secondary differences, depending on the language. A secondary difference is ignored when there is a primary difference anywhere in the strings.\</li\>
     
     \<li\>\<b\>TERTIARY strength:\</b\> Upper and lower case differences in characters are distinguished at tertiary strength (for example, "ao" &lt; "Ao" &lt; "aò"). In addition, a variant of a letter differs from the base form on the tertiary strength (such as "A" and "Ⓐ"). Another example is the difference between large and small Kana. A tertiary difference is ignored when there is a primary or secondary difference anywhere in the strings.\</li\>
     
     \<li\>\<b\>IDENTICAL strength:\</b\> When all other strengths are equal, the IDENTICAL strength is used as a tiebreaker. The Unicode code point values of the NFD form of each string are compared, just in case there is no difference. For example, Hebrew cantellation marks are only distinguished at this strength. This strength should be used sparingly, as only code point value differences between two strings are an extremely rare occurrence. Using this strength substantially decreases the performance for both comparison and collation key generation APIs. This strength also increases the size of the collation key.\</li\>
     
     \</ol\>
     
     
     \<p\>
     This Collator deals only with two decomposition modes, the canonical decomposition mode and one that does not use any decomposition. The compatibility decomposition mode java.text.Collator.FULL\_DECOMPOSITION is not supported here. If the canonical decomposition mode is set, Collator handles un-normalized text properly, producing the same results as if the text were normalized in NFD. If canonical decomposition is turned off, it is the user's responsibility to ensure that all text is already in the appropriate form before performing a comparison or before getting a CollationKey.
     \</p\>\<br\>
     
     Following is an example illustrating how to use Collator to get strings sorted with and without decomposition. The getInstance method causes the Collator to perform sorting based on the system’s current locale. You can force it to use a different locale by specifying a particular locale as follows:
     
     \<div class="code\_sample"\>
     Collator myCollator = Collator.getInstance(LOCALE.FR);
     \</div\>
     You can specify any locale supported by the Android platform in the above code.
     
     \<b\>Example:\</b\>
     
     \<div class="code\_sample"\>
     \<pre\>
     Collator myCollator = Collator.getInstance();
     myCollator.setDecomposition(Collator.NO\_DECOMPOSITION);
     if (myCollator.compare("ḁ̀", "ḁ̀") != 0) {
     System.out.println("ḁ̀ is not equal to ḁ̀ without decomposition");
     myCollator.setDecomposition(Collator.CANONICAL\_DECOMPOSITION);
     if (myCollator.compare("ḁ̀", "ḁ̀") != 0) {
     System.out.println("Error: ḁ̀ should be equal to ḁ̀ with decomposition");
     } else {
     System.out.println("ḁ̀ is equal to ḁ̀ with decomposition");
     }
     } else {
     System.out.println("Error: ḁ̀ should be not equal to ḁ̀ without decomposition");
     }
     \</pre\>
     \</div\>
     
     \<a name="Fonts"\>\</a\>
     \<h2\>Fonts\</h2\>
     
     \<h3\>General\</h3\>
     Android provides different ways to specify the size/dimensions of the font being used. The following units of measure are supported by Android: \<b\>dp, sp ,pt ,px ,mm ,in\</b\>. Apart from these 6 units of measure there are also some system standard font sizes which you can use in your applications. The brief description of these are as follows:\<br\>
     
     \<ol\>
     \<li\>\<b\>dp: Density-independent Pixels\</b\> - An abstract unit that is based on the physical density of the screen. These units are relative to a 160 dpi (dots per inch) screen, on which 1dp is roughly equal to 1px. When running on a higher density screen, the number of pixels used to draw 1dp is scaled up by a factor appropriate for the screen's dpi. Likewise, when on a lower density screen, the number of pixels used for 1dp is scaled down. The ratio of dp-to-pixel will change with the screen density, but not necessarily in direct proportion. Using dp units (instead of px units) is a simple solution to making the view dimensions in your layout resize properly for different screen densities. In other words, it provides consistency for the real-world sizes of your UI elements across different devices.\</li\>
     
     \<li\>\<b\>sp: Scale-independent Pixels\</b\> - This is like the dp unit, but it is also scaled by the user's font size preference. It is recommend you use this unit when specifying font sizes, so they will be adjusted for both the screen density and the user's preference.\</li\>
     \<li\>\<b\>pt: Points\</b\> - 1/72 of an inch based on the physical size of the screen. \</li\>
     \<li\>\<b\>px: Pixels\</b\> - Corresponds to actual pixels on the screen. This unit of measure is not recommended because the actual representation can vary across devices; each devices may have a different number of pixels per inch and may have more or fewer total pixels available on the screen.\</li\>
     \<li\>\<b\>mm : Millimeters\</b\> - Based on the physical size of the screen.\</li\>
     \<li\>\<b\>in: Inches\</b\> - Based on the physical size of the screen.\</li\>
     \</ol\>
     
     For specifying the text size in case of a text editor you can use broadly 3 categories of font sizes: \<b\>Fixed Font Size, Standard System Font Size, Dynamic Font size.\</b\>
     
     \<ul\>
     \<li\>\<b\>Standard Font Size:\</b\> Android provides you with 3 inbuilt system font size which you can use with in xml attribute android:textAppearance. Following are the examples of using these 3 types.
     \<xmp class="code\_sample"\>
     \<TextView
     android:id="@+id/textView1"
     android:layout\_width="wrap\_content"
     android:layout\_height="wrap\_content"
     android:text="Medium Text"
     android:textAppearance="?android:attr/textAppearanceMedium" /\>
     \<TextView
     android:id="@+id/textView1"
     android:layout\_width="wrap\_content"
     android:layout\_height="wrap\_content"
     android:text="Large Text"
     android:textAppearance="?android:attr/textAppearanceLarge" /\>
     
     \<TextView
     android:id="@+id/textView1"
     android:layout\_width="wrap\_content"
     android:layout\_height="wrap\_content"
     android:text="Small Text"
     android:textAppearance="?android:attr/textAppearanceSmall" /\>
     \</xmp\>
     \</li\>
     
     \<li\>
     \<b\>Fixed Pixel Size:\</b\> In case you want to provide text of fixed size you can do so by using the attribute android:textSize and specifying the font size in either pt , px , in, mm as explained above.
     \<xmp class="code\_sample"\>
     \<TextView
     android:id="@+id/textView3"
     android:layout\_width="wrap\_content"
     android:layout\_height="wrap\_content"
     android:textSize="20px"
     android:text="TextView" /\>
     \</xmp\>
     \</li\>
     \<li\>
     \<b\>Dynamic Pixel Size:\</b\> This is the recommended way of specifying the text size. There are two units which you can use : dp , sp. You can specify the size in the attribute android:textSize as has been shown in above example.
     \</li\>
     \</ul\>
     
     \<!-- ------------------ --\>
     \<!--- Language Switching ---\>
     \<!-- \#\#\#\#\#\#\#\#\#\#\#\#\#\#\# ---\>
     
     \<a name="Language Switching"\>\</a\>
     \<h2\>Language Switching\</h2\>
     
     \<h3\>General\</h3\>
     
     An Android application's language should match that of the system locale, if available. As long as the application keeps the language-specific resource files inside a resource bundle (res/values-fr-rFR, res/layouts-fr-rFR), your application doesn't have to do anything else to determine the its UI language. Android automatically loads these resource files based on bundle architecture and system locale.\<br\>\<br\>
     
     You should not try and set the UI language of the application yourself. Allow it to match the preferred system language set in the settings.But in case for testing purpose if you need to change the language settings then you can do so by going to \<b\>Settings -\> Language & Keyboard -\> Language.\</b\>\<br\>\<br\>
     
     There may be times you may need to get the current locale of device in code which you can do by calling the following API:
     
     \<div class="code\_sample"\>
     Locale current = getResources().getConfiguration().locale;
     \</div\>
     \<!-- Work form --\>
     \</body\>
     
     \</html\>
  -- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Jump to Line

Go

-   [API](https://developer.github.com/enterprise/2.10)
-   [Training](https://training.github.com)
-   [Shop](https://shop.github.com)
-   [Blog](https://github.com/blog)
-   [About](https://github.com/about)

[](https://git.corp.adobe.com "GitHub Enterprise Version 2.10.6")

-   © 2018 GitHub, Inc.
-   [Help](https://help.github.com/enterprise/2.10)
-   [Support](mailto:scm-servicedesk@adobe.com)

You can't perform that action at this time.

You signed in with another tab or window. [Reload]() to refresh your
session. You signed out in another tab or window. [Reload]() to refresh
your session.
