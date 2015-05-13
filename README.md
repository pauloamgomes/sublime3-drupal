# sublime3-drupal

Sublime3 configurations (user settings) and recommended addons for drupal development.

<h3>Main advantages of using sublime for Drupal:</h3>
<ul>
  <li>Simplicity of usage</li>
  <li>Fast and light</li>
  <li>Supports multiple platforms (Mac, Linux, Windows)</li>
  <li>Plugin mechanism</li>
  <li>Great user adoption</li>
</ul>

<h3>How to apply the settings</h3>
<p>Goto to <em>preferences > settings - user</em> and replace contents from <a href="https://github.com/pauloamgomes/sublime3-drupal/blob/master/Preferences.sublime-settings">here</a>

<h3>Recommended addons</h3>
<ul>
  <li>Bracket Highlighter</li>
  <li>Doc Blockr</li>
  <li>Sidebar Enhancements</li>
  <li>Drupal</li>
  <li>Drupal Completions</li>
  <li>Drupal Project Autocomplete</li>
  <li>AdvancedNewFile</li>
  <li>SublimeLinter</li>
  <li>SublimeLinter phplint</li>
</ul>

<h4>SublimeLinter and Code Sniffer</h4>
<p>Install PHP_Codesniffer and drupalcs</p>
<ul>
  <li>Install PHP Code Sniffer <br/>```pear install PHP_CodeSniffer```</li>
  <li>Download coder module from https://www.drupal.org/project/coder - use 8.x branch since 7.x seems broken (8.x branch can be also used for validating D7 code) and copy or link the coder/coder_sniffer/Drupal folder to to your PHP CodeSniffer Standards folder (e.g. /usr/share/php/PHP/CodeSniffer/Standards)</li>
  <li>Configure sublimelinter prefs by updating Preferences/Package Settings/Sublime Linter/Settings - User<br/>
<pre><code>
    "paths": {
        "linux": ["/usr/bin/php"],
        "osx": [],
        "windows": []
    },
    "syntax_map": {
        "php": "php"
    },
    "sublimelinter_popup_errors_on_save": true,
    "sublimelinter_fill_outlines": true,
    "sublimelinter_gutter_marks": true,
</code></pre>
  </li>
  <li>Create a new Build System in Tools/Build System/New Build System... with the following code:<br/>
<pre><code>
  {
    "cmd": ["phpcs", "--report=emacs", "--standard=Drupal","--extensions=php,module,inc,install,test,profile,theme", "$file"],
    "file_regex": "^(.*):(.*):(.*):(.*)$"
  }
</code></pre>
  and save the file on your User Package folder with the name Drupal.sublime-build
  </li>
</ul>
