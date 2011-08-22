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

<p><b>Q:</b> <i>When <code>scion-browser</code> is building, I get an error like <code>Loading package double-conversion-0.2.0.0 ... can't load .so/.DLL for: stdc++ (libstdc++.so: cannot open shared object file: No such file or directory)</code>.</i></p>
<p><b>A:</b> This is a bug in GHC as pointed <a href="http://hackage.haskell.org/trac/ghc/ticket/5289">here</a>. If you are using a Linux distribution, the recommended way to cicumvent the problem is running
<p><code>sudo ln -vs $(gcc --print-file-name=libstdc++.so) /usr/local/lib/<br />
sudo ldconfig</code></p>
If you are using Mac OS X, the following command will do the trick:
<p><code>sudo ln -s /usr/lib/libstdc++.6.dylib /usr/lib/libstdc++.dylib</code></p>
Then, restart Eclipse to force <code>scion-browser</code> to be rebuilt.
</p>
