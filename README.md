# sublime3-drupal

<a href="http://www.sublimetext.com/3">Sublime3</a> configurations (user settings) and recommended addons for drupal development.

<h3>Main advantages of using sublime for Drupal:</h3>
<ul>
  <li>Simplicity of usage</li>
  <li>Fast and light</li>
  <li>Supports multiple platforms (Mac, Linux, Windows)</li>
  <li>Plugin mechanism</li>
  <li>Great user adoption</li>
</ul>

<h3>How to apply the settings</h3>
<p>Goto to <em>Preferences > Settings - user</em> and replace contents from <a href="https://github.com/pauloamgomes/sublime3-drupal/blob/master/Preferences.sublime-settings">Preferences.sublime-settings</a>

<h3>Package Manager</h3>
<p>Package Manager provides a mechanism for installing and managing sublime packages (addons) from the sublime package repository.</p>
<p>Use installation steps provided on <a href="https://packagecontrol.io/installation">Package Control installation page</a></p>

<h3>Drupal packages</h3>
<ul>
  <li><a href="https://packagecontrol.io/packages/Drupal">Drupal</a></li>
  <li><a href="https://packagecontrol.io/packages/Drupal%20Completions">Drupal Completions</a></li>
  <li><a href="https://packagecontrol.io/packages/Drupal%20Project%20Autocomplete">Drupal Project Autocomplete</a></li>
  <li><a href="https://packagecontrol.io/packages/Goto%20Drupal%20API">Goto Drupal API</a></li>
</ul>

<h3>Other recommended packages</h3>
<ul>
  <li><a href="https://packagecontrol.io/packages/BracketHighlighter">Bracket Highlighter</a></li>
  <li><a href="https://packagecontrol.io/packages/DocBlockr">Doc Blockr</a></li>
  <li><a href="https://packagecontrol.io/packages/SideBarEnhancements">Sidebar Enhancements</a></li>
  <li><a href="https://packagecontrol.io/packages/AdvancedNewFile">AdvancedNewFile</a></li>
  <li><a href="https://packagecontrol.io/packages/SublimeLinter">SublimeLinter</a></li>
  <li><a href="https://packagecontrol.io/packages/SublimeLinter-php">SublimeLinter-php</a></li>
</ul>

<h4>SublimeLinter and Code Sniffer</h4>
<p>Install PHP_Codesniffer and drupalcs</p>
<ol>
  <li>Install PHP Code Sniffer <pre><code>pear install PHP_CodeSniffer</code></pre></li>
  <li>Download coder module from https://www.drupal.org/project/coder - use 8.x branch since 7.x seems broken (8.x branch can be also used for validating D7 code) and copy or link the coder/coder_sniffer/Drupal folder to to your PHP CodeSniffer Standards folder (e.g. /usr/share/php/PHP/CodeSniffer/Standards)</li>
  <li>Configure sublimelinter prefs by updating Preferences/Package Settings/Sublime Linter/Settings - User<br/>
<pre><code>
    "paths": {"linux": ["/usr/bin/php"]},
    "syntax_map": {"php": "php"},
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
</ol>
