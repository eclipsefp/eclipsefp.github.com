---
layout: web
title: EclipseFP > Installation
---

<!-- The list of elements -->
<center>
<table id="tableofcontents">
  <tr>
    <td width="160px" align="center" class="toc"><a href="index.html">Home</a></td>
    <td width="160px" align="center" class="toc"><a href="features.html">Features</a></td>
    <td width="160px" align="center" class="toc selected"><a href="install.html">Installation</a></td>
    <td width="160px" align="center" class="toc"><a href="faq.html">FAQ</a></td>
    <td width="160px" align="center" class="toc"><a href="dev.html">Development</a></td>
  </tr>
</table>
</center>
<hr />
<br />
<!-- Until here the list -->

If are already proficient with Eclipse plug-ins installation, all you need to know is that the EclipseFP update site is located in
``http://eclipsefp.sf.net/updates`` and then follow the <a href="#extra">extra configuration steps</a>. If you don't know what
"update site" means, don't worry, just follow the steps right below this text.

## Getting Eclipse up and running

If it's the first time that you use Eclipse or install plug-ins, follow this set of instructions:
<ul>
<li>Go to the <a href="http://eclipse.org/downloads/">Eclipse download page</a> and get any of the Eclipse bundles. With each of them you will get a different initial set of language support, but EclipseFP is compatible with any of them.</li>
<li>Uncompress the archive you just downloaded. A <code>eclipse</code> folder will be created.</li>
<li>Inside this folder, you will find an executable called <code>eclipse</code>. Double-click it to start the Eclipse environment (yes, "installing Eclipse" means uncompressing it somewhere, even on a portable drive).</li>
<li>The first time you execute Eclipse, you will be asked about a workspace. A <i>workspace</i> is just the folder where your preferences and configurations are stored (you can have different sets of preferences using different workspaces), and where your projects will be created by default. For trying, you can just use the default choice (usually <code>&lt;your user folder&gt;/workspace</code>).</li>
<li>Now, let's install EclipseFP. First, on the menu, go to <b>Help &gt; Install New Software...</b>.</li>
<li>In the <i>Available software</i> window that will appear, click the <b>Add...</b> button.</li>
<li>You will be asked about the details of the update site you want to add. An <i>update site</i> is just a place on the internet where your Eclipse installation can find new plug-ins to install. If you use Linux, the concept is very similar to a repository. The name is not important, but the URL must point to <code>http://eclipsefp.sf.net/updates</code>.
<br />
<center><img src="images/update-site.png" style="margin: 10px;" /></center>
</li>
<li>The <i>Available software</i> window will show the plug-ins in the EclipseFP repository. Check <b>FP: Haskell support for Eclipse</b> and click <b>Next</b>.</li>
<li>After clicking <b>Next</b> a few more times (for accepting the licenses), the plug-in will be downloaded and installed.
<br />
<center><img src="images/install.png" style="margin: 10px;" /></center>
</li>
<li>You will be asked for an Eclipse restart. After doing it, you can start using EclipseFP by going to <b>Window &gt; Open perspective &gt; Other...</b> and selecting <i>Haskell</i>.</li>
<li>Now, follow the <a href="#extra">extra configuration steps</a></li>
</ul>

<a name="extra" />
## Extra configuration steps
