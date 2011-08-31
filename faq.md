---
layout: web
title: EclipseFP > FAQ
---

<!-- The list of elements -->
<center>
<table id="tableofcontents">
  <tr>
    <td width="160px" align="center" class="toc"><a href="index.html">Home</a></td>
    <td width="160px" align="center" class="toc"><a href="features.html">Features</a></td>
    <td width="160px" align="center" class="toc"><a href="install.html">Installation</a></td>
    <td width="160px" align="center" class="toc selected"><a href="faq.html">FAQ</a></td>
    <td width="160px" align="center" class="toc"><a href="dev.html">Development</a></td>
  </tr>
</table>
</center>
<hr />
<br />
<!-- Until here the list -->

<p><b>Q:</b> <i>Why is EclipseFP sometimes so slow to start?</i></p>
<p><b>A:</b> The first time EclipseFP starts, it needs to build some Haskell components and to download package information from the Internet. This may take a long time, depending on your machine. This is a procedure that only needs to be done once. However, each time you start EclipseFP, the plug-in checks if your set of installed packages has changed and if so, it downloads and builds the documentation for them. Depending of how big the change was, this may be a lot of work.</p>
<p>In any case, once the <i>Rebuilding local database</i> message disappears from the status bar, the startup is complete and the full power of EclipseFP is at your disposal.</p>

<br />

<p><b>Q:</b> <i>When <code>scion-browser</code> is building, I get an error like <code>Loading package double-conversion-0.2.0.0 ... can't load .so/.DLL for: stdc++ (libstdc++.so: cannot open shared object file: No such file or directory)</code>.</i></p>
<p><b>A:</b> This is a bug in GHC as pointed <a href="http://hackage.haskell.org/trac/ghc/ticket/5289">here</a>. If you are using a Linux distribution, the recommended way to cicumvent the problem is running on a terminal:
<p><code>sudo ln -vs $(gcc --print-file-name=libstdc++.so) /usr/local/lib/<br />
sudo ldconfig</code></p>
If you are using Mac OS X, the following command will do the trick:
<p><code>sudo ln -s /usr/lib/libstdc++.6.dylib /usr/lib/libstdc++.dylib</code></p>
Then, restart Eclipse to force <code>scion-browser</code> to be rebuilt.
</p>
<br />

<p><b>Q:</b> <i>I'm on Windows and/or the error is more like <code>Loading package double-conversion-0.2.0.0 ... can't load .so/.DLL for: stdc++ (addDLL: could not load DLL)
ghc.exe: stdc++: The specified module could not be found.</code>.</i></p>
<p><b>A:</b> Try the workaround outlined <a href="https://github.com/mailrank/blaze-textual#readme">here</a>:<br />
<code>cabal install blaze-textual --user -fnative --reinstall</code><br />
<code>cabal install aeson --user --reinstall</code><br />
Then, restart Eclipse to force <code>scion-browser</code> to be rebuilt.
</p>
<br />

<p><b>Q:</b> <i>In my installation of EclipseFP some of the features that you announce are not available.</i></p>
<p><b>A:</b> First of all, check that you have all the <a href="install.html#extra">extra components</a> needed for those features to work.</p>
<p>If you created your project with an older version of EclipseFP, the support for HLint, Alex, Happy or UUAGC needs to be enabled in the project (for new projects all these features are enabled automatically). For doing so, right-click on your project root, and in the <i>Configure</i> submenu, choose the builder you want to add.</p>
