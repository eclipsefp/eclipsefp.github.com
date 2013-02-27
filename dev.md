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

<p>EclipseFP is done of three main components:
<ul>
<li><b>BuildWrapper</b> is a Haskell library and executable that wraps the GHC API and the Cabal executable to provide the functionality needed for IDEs.</li>
<li><b>EclipseFP</b> itself is a set of Eclipse plug-ins programmed mostly in Java. The development was started by Leif Frenzel, with contributions of (in alphabetical order) Andrei de A. Formiga, Thiago Arrais, Scott Michel, JP Moresmau, Alejandro Serrano (during his <a href="http://serras-haskell-gsoc.blogspot.com/">2011 Google Summer of Code</a>), and B. Thomas ten Cate (during his <a href="http://eclipsefp.wordpress.com/">2009 Google Summer of Code</a>). <a href="https://github.com/JPMoresmau">JP Moresmau</a> is the current maintainer.</li>
<li><b>Scion Browser</b> is a Haskell library that reads Hoogle documentation files for installed packaged and provides a way to navigate them. This component is mostly work of <a href="https://github.com/serras">Alejandro Serrano</a>.</li>
</ul>
</p>

<p>The <b>code</b> is hosted in <a href="http://github.com">GitHub</a>:
<ul>
<li>BuildWrapper: <a href="https://github.com/JPMoresmau/BuildWrapper"><code>https://github.com/JPMoresmau/BuildWrapper</code></a></li>
<li>EclipseFP: <a href="https://github.com/JPMoresmau/eclipsefp"><code>https://github.com/JPMoresmau/eclipsefp</code></a></li>
<li>Scion Browser: <a href="https://github.com/JPMoresmau/scion-class-browser"><code>https://github.com/JPMoresmau/scion-class-browser</code></a></li>
</ul>
but the <b>mailing list</b> is hosted in the <a href="http://sourceforge.net/mailarchive/forum.php?forum_name=eclipsefp-develop">old site in SourceForge</a>.
</p>

## Building from source

<p>As usual, this assumes that you have GHC, cabal-install, and <a href="http://www.git-scm.org/">Git</a>. This should work on all platforms.</p>
<ol>
<li>Get <a href="http://www.eclipse.org/downloads/">Eclipse</a>, the distribution named <i>Eclipse Classic</i>. Extraction equals installation.</li>
<li>You need to install the <a href="http://download.eclipse.org/birt/">BIRT Charting Engine</a> to be able to build EclipseFP. The update site is <code>http://download.eclipse.org/birt/update-site/3.7</code> for Eclipse 3.7 (Indigo). For Eclipse 4.2, install the BIRT Engine OSGi Runtime SDK Feature from <i>http://download.eclipse.org/birt/update-site/4.2</i>.</li>
<li>Get the BuildWrapper source: <code>git clone git://github.com/JPMoresmau/BuildWrapper.git</code><br />
</li>
<li>Build and install BuildWrapper, (it will install both the library as well as the exectuable program):<br />
<code>cd BuildWrapper<br />
cabal install<br />
</code>
</li>
<li>Get the EclipseFP source: <code>git clone git://github.com/JPMoresmau/eclipsefp.git</code></li>
<li>Import all Eclipse projects from these repositories into Eclipse.</li>
<li>Build all projects or set your workspace to automatically build all projects for you</li>
<li>Hit <b>Run &gt; Run Configurations</b>. Add a new launch <i>Eclipse Application</i> launch configuration. The default settings for this launch configuration should work, so just click <b>Run</b>.</li>
<li>In the new Eclipse window that (hopefully) pops up, check the location of the BuildWrapper executable via <b>Window &gt; Preferences &gt; Haskell &gt; Helper Executables</b>. You may want to use the location of a locally built version of BuildWrapper if you've made changes to it.</li>
<li>If something doesn't work, turn on tracing. In the <i>Run Configurations</i> dialog, on the <i>Tracing</i> tab, you can enable tracing options for various plug-ins. These will output to the Console at the bottom of the host Eclipse window. Also in preferences turn on debug mode for BuildWrapper, that will show you the output from BuildWrapper.</li>
</ol>

