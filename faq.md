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
<p>If you feel this is really slow, you can try to rebuild the database manually to get a feel if there's a problem with Hackage:<br/>
<code>scion-browser</code>
<code>{"filepath":"/home/user/workspace/.metadata/.plugins/net.sf.eclipsefp.haskell.browser/scion-browser-0.2-dbs/local.db","command":"load-local-db","rebuild":true}</code>
This starts the scion-browser console, that accepts commands in JSON format. You should then see the packages downloading from Hackage.</p>
<br />

<p><b>Q:</b> <i>I've installed BuildWrapper and scion-browser, but nothing works.</i></p>
<p><b>A:</b> You need to be sure that your PATH is correct. So check in the Preferences that all the paths to GHC, Cabal, BuildWrapper and others are correct.<br/>
Things to look for:
<ul>
<li>On Windows, you haven't installed the Haskell Platform as an Administrator, and your PATH has not been updated correctly. Add %USERPROFILE%\AppData\Roaming\cabal\bin and all the bin folders you can find inside the Haskell Platform folder to your PATH.</li>
<li>You're on MacOS and the PATH used by GUI applications is not the same as the one you see in your shell. Need help? Click <a href="http://leohacker.wordpress.com/2011/12/05/add-your-path-into-path-for-gui-application-for-macos/">here</a> and <a href="http://serverfault.com/questions/16355/how-to-set-global-path-on-os-x">here</a>.</li>
</ul>
<br/>

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

<br />

<p><b>Q:</b> <i>Scion-browser doesn't install on Fedora 16: undefined reference to symbol 'tparm'</i></p>
<p><b>A:</b>The full message is something like:<br />
<code>Linking dist/build/scion-browser/scion-browser ...</code><br />
<code>/usr/bin/ld: /home/user/.cabal/lib/terminfo-0.3.2.3/ghc-7.0.4/libHSterminfo-0.3.2.3.a(Base.o): undefined reference to symbol 'tparm'</code><br />
<code>/usr/bin/ld: note: 'tparm' is defined in DSO /lib64/libtinfo.so.5 so try adding it to the linker command line</code><br />
<code>/lib64/libtinfo.so.5: could not read symbols: Invalid operation</code><br />
<code>collect2: ld returned 1 exit status</code><br />
<code>cabal: Error: some packages failed to install:</code><br />
</p>
<p>
An explanation can be found <a href="http://lists.fedoraproject.org/pipermail/devel/2010-March/133601.html">here</a>. 
<br />A work around: try adding this to the executable section of scion-browser.cabal:<br />
<code>Extra-libraries: tinfo</code>
</p>

<br />

<p><b>Q:</b> <i>I get an error about <code>ncurses</code> while compiling <code>scion-browser</code>: something like <code>can't load .so/.DLL for: ncursesw (/usr/lib/libncursesw.so: file too short)</code></i></p>
<p><b>A:</b> This happens because GHC does not follow some kinds of links between libraries that GCC does. In a Ubuntu system, you can solve it opening a terminal and running:<br />
<code>cd /usr/lib</code><br />
<code>sudo mv libncurses.so libncurses.so.bak</code><br />
<code>sudo mv libncursesw.so libncursesw.so.bak</code><br />
<code>sudo ln -s /lib/libncurses.so.5 libncurses.so</code><br />
<code>sudo ln -s /lib/libncursesw.so.5 libncursesw.so</code><br />
</p>

<br />

<p><b>Q:</b> <i>I still have an issue that I can't solve, what do I do?</i></p>
<p><b>A:</b> Search the <a href="http://sourceforge.net/projects/eclipsefp/forums/forum/371922">SourceForge forum</a>, and if you find nothing, post your question!</p>


