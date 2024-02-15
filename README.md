<h1 id="intro">Intro</h1>
<p><strong>richly</strong> converts markdown or emacs org-mode files into html and renders latex as inline svg. You can visit <a href="https://xwcal.github.io/posts/2024/01/21/on-exponentiation/">this page</a> to see its product.</p>
<p>The initial iteration I wrote overnight a few years ago also included PlantUML integration (thus the name "richly"). The diagramming feature can be added back if there is popular demand.</p>
<h1 id="dependencies">Dependencies</h1>
<p>In order to use richly, you need:</p>
<ul>
<li>a working latex setup that generates dvi output</li>
<li>pandoc</li>
<li>dvisvgm</li>
<li>python3</li>
<li>linux</li>
</ul>
<h1 id="basic-usage">Basic usage</h1>
<p>The <code>&lt;input file&gt;</code> below should be either a <code>.md</code> or a <code>.org</code> file.</p>
<p>For a one shot conversion:</p>
<pre><code>$ richly &lt;input file&gt; &lt;output file&gt;
</code></pre>
<p>To let richly monitor <code>&lt;input file&gt;</code> and do incremental conversion as you edit it, add the <code>-s</code> switch:</p>
<pre><code>$ richly -s &lt;input file&gt; &lt;output file&gt;
</code></pre>
<p>In either case, you may find the <code>-v</code> switch helpful.</p>
<h1 id="hugo-integration">Hugo integration</h1>
<p>If you use org-mode, the input org files can coexist with markdown files under <code>content/</code>: simply add <code>"\\.org$"</code> to <code>ignoreFiles</code> in your site configuration file.</p>
<p>Say you are writing a post named <code>some-post.org</code>, you need to enclose the front matter between <code>#+begin_src</code> and <code>#+end_src</code>, then run <code>richly</code> with the <code>-r</code> swtich:</p>
<pre><code>$ richly -s -r -v some-post.org some-post.md
</code></pre>
<p>With <code>hugo server</code> running you can see the result update in real time as you edit <code>some-post.org</code>.</p>
<p>If you use markdown, you need to keep a seperate "richly source files" directory outside your hugo site directory so that hugo doesn't get confused. And you need to enclose the front matter in a code block using a pair of <code>```</code> (or more backticks if necessary) instead.</p>

<h1 id="todos">TODOs</h1>
<p>Add an option for saving and restoring the cache to avoid potentially lengthy cold starts.</p>

