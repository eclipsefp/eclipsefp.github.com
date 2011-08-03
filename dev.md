---
layout: web
title: EclipseFP > Development
---

<!-- The list of elements -->
<center>
<table style="width: 800px:">
  <tr>
    <td width="160px" align="center" class="toc"><a href="index.html">Home</a></td>
    <td width="160px" align="center" class="toc"><a href="features.html">Features</a></td>
    <td width="160px" align="center" class="toc"><a href="install.html">Installation</a></td>
    <td width="160px" align="center" class="toc"><a href="faq.html">FAQ</a></td>
    <td width="160px" align="center" class="toc selected"><a href="dev.html">Development</a></td>
  </tr>
</table>
</center>
<hr style="width: 780px; margin: 0;" />
<br />
<!-- Until here the list -->

<p>EclipseFP is done of two main components:
<ul>
<li><b>Scion</b> is a Haskell library and server that wraps the GHC API to provide the functionality needed for IDEs. Scion is mostly due to the work of <a href="https://github.com/nominolo">Thomas Schilling</a>.</li>
<li><b>EclipseFP</b> itself is a set of Eclipse plug-ins programmed mostly in Java. The development was started by Leif Frenzel, with contributions of (in alphabetical order) Andrei de A. Formiga, Thiago Arrais, Scott Michel, JP Moresmau, Alejandro Serrano (during his <a href="http://serras-haskell-gsoc.blogspot.com/">2011 Google Summer of Code</a>), and B. Thomas ten Cate (during his <a href="http://eclipsefp.wordpress.com/">2009 Google Summer of Code</a>). <a href="https://github.com/JPMoresmau">JP Moresmau</a> is the current maintainer.</li>
</ul>
</p>

<p>The <b>code</b> is hosted in <a href="http://github.com">GitHub</a>:
<ul>
<li>Scion: <a href="https://github.com/JPMoresmau/scion"><code>https://github.com/JPMoresmau/scion</code></a></li>
<li>EclipseFP: <a href="https://github.com/JPMoresmau/eclipsefp"><code>https://github.com/JPMoresmau/eclipsefp</code></a></li>
</ul>
but the <b>mailing list</b> is hosted in the <a href="http://sourceforge.net/mailarchive/forum.php?forum_name=eclipsefp-develop">old site in SourceForge</a>.
</p>

## Building from source

<p>As usual, this assumes that you have GHC, cabal-install, and <a href="http://www.git-scm.org/">Git</a>. This should work on all platforms.</p>
<ol>
<li>Get <a href="http://www.eclipse.org/downloads/">Eclipse</a>, the distribution named <i>Eclipse Classic</i>. Extraction equals installation. After that, you need to install the <a href="http://download.eclipse.org/birt/">BIRT Charting Engine</a> to be able to build EclipseFP.</li>
<li>Get the Scion source: <code>git clone git://github.com/JPMoresmau/scion.git</code><br />
</li>
<li>Build and install Scion, (it will install both the library as well as the server program):<br />
<code>cd scion<br />
cabal install<br />
</code>
</li>
<li>Get the EclipseFP source: <code>git clone git://github.com/JPMoresmau/eclipsefp.git</code></li>
<li>Import all Eclipse projects from these repositories into Eclipse.</li>
<li>Build all projects or set your workspace to automatically build all projects for you</li>
<li>Hit <b>Run &gt; Run Configurations</b>. Add a new launch <i>Eclipse Application</i> launch configuration. The default settings for this launch configuration should work, so just click <b>Run</b>.</li>
<li>In the new Eclipse window that (hopefully) pops up, set the location of the Scion server via <b>Window &gt; Preferences &gt; Haskell &gt; Scion</b>. If you installed it in a fairly standard location, the <i>Autodetect</i> button should do the trick; otherwise, just <i>Browse</i>.</li>
<li>If something doesn't work, turn on tracing. In the <i>Run Configurations</i> dialog, on the <i>Tracing</i> tab, you can enable tracing options for various plug-ins. These will output to the Console at the bottom of the host Eclipse window. To see the traffic between the Scion client and server, turn on the logs for <code>net.sf.eclipsefp.haskell.scion.client</code>.</li>
</ol>

