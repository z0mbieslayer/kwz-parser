<p>Experimental decoder and utilities (image/video conversion, etc) for Flipnote Studio 3D's .kwz animation format. Frames and audio can both be decoded without any problems.</p>
<p>All scripts were written for Python 3.7 and require the <a href="http://www.numpy.org/" rel="nofollow">numpy</a> module to be installed.</p>
<h4><a id="user-content-credits" class="anchor" aria-hidden="true" href="#credits"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Credits</h4>
<ul>
<li><strong><a href="https://github.com/jaames">Jaames</a></strong> - general reverse-engineering and python implementation</li>
<li><strong><a href="https://github.com/Kinnay">Kinnay</a></strong> - reverse-engineering tile compression</li>
<li><strong><a href="https://github.com/khang06">Khangaroo</a></strong> - reverse-engineering a large chunk of the audio format</li>
<li><strong><a href="https://github.com/shutterbug2000">Shutterbug</a></strong> - early decompression and frame diffing work</li>
<li><strong><a href="https://github.com/MrNbaYoh">MrNbaYoh</a></strong> - identifying the use of a line table</li>
<li><strong><a href="https://github.com/stary2001">Stary</a></strong>, <strong><a href="https://github.com/JoshuaDoes">JoshuaDoes</a></strong> and <strong><a href="https://github.com/thejsa">thejsa</a></strong> - debugging/optimisation help</li>
<li><strong><a href="https://github.com/sudofox">Sudofox</a></strong> - audio format help and comment sample files</li>
</ul>
<h2><a id="user-content-utilities" class="anchor" aria-hidden="true" href="#utilities"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Utilities</h2>
<h3><a id="user-content-kwzimage" class="anchor" aria-hidden="true" href="#kwzimage"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>kwzImage</h3>
<p>Converts specific kwz frames as well folder icons and Flipnote Gallery World comments (.kwc) to standard image formats such as png, gif, jpeg, etc. Requires the <a href="https://pillow.readthedocs.io/en/5.2.x/" rel="nofollow">Pillow</a> module to be installed.</p>
<p>Usage:</p>
<div class="highlight highlight-source-shell"><pre>python kwzImage.py <span class="pl-k">&lt;</span>input path<span class="pl-k">&gt;</span> <span class="pl-k">&lt;</span>frame index<span class="pl-k">&gt;</span> <span class="pl-k">&lt;</span>output path<span class="pl-k">&gt;</span></pre></div>
<p><code>&lt;frame index&gt;</code>:</p>
<ul>
<li>Specific frame index (e.g. <code>0</code> for the first frame)</li>
<li><code>thumb</code> to get the thumbnail frame</li>
<li><code>gif</code> to encode the whole Flipnote to an animated GIF.</li>
</ul>
<p><code>&lt;output path&gt;</code>:</p>
<ul>
<li>Can include placeholders: <code>{name}</code> for the input filename (without extention), <code>{ext}</code> for input extention, <code>{index}</code> for the item index and <code>{dirname}</code> for the input file directory.</li>
</ul>
<p><code>&lt;input path&gt;</code>:</p>
<ul>
<li>
<p>You can pass glob patterns as the input filepath to batch convert. For example, the following will extract thumbnail images from all the kwzs in a directory:</p>
<div class="highlight highlight-source-shell"><pre>python kwzImage.py <span class="pl-s"><span class="pl-pds">"</span>/flipnotes/*.kwz<span class="pl-pds">"</span></span> thumb /flipnotes/{name}.png</pre></div>
</li>
</ul>
<h3><a id="user-content-kwzvideo" class="anchor" aria-hidden="true" href="#kwzvideo"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>kwzVideo</h3>
<p>Experimental kwz to mp4 encoder using <a href="https://www.ffmpeg.org/" rel="nofollow">ffmpeg</a>. Tries to ensure optimal compression and image quality while also upscaling the Flipntote to 480p.</p>
<p>Usage:</p>
<div class="highlight highlight-source-shell"><pre>python kwzVideo.py <span class="pl-k">&lt;</span>input.kwz<span class="pl-k">&gt;</span> <span class="pl-k">&lt;</span>output.kwz<span class="pl-k">&gt;</span></pre></div>
<h3><a id="user-content-kwzaudio" class="anchor" aria-hidden="true" href="#kwzaudio"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>kwzAudio</h3>
<p>Exports a Flipnote audio track and converts it to WAV.</p>
<p><strong>Usage:</strong></p>
<div class="highlight highlight-source-shell"><pre>python kwzAudio.py <span class="pl-k">&lt;</span>input.kwz<span class="pl-k">&gt;</span> <span class="pl-k">&lt;</span>track id<span class="pl-k">&gt;</span> <span class="pl-k">&lt;</span>output.wav<span class="pl-k">&gt;</span></pre></div>
<p>Where <code>&lt;track id&gt;</code> is <code>0</code> for BGM, or <code>1</code> - <code>4</code> for SE1 - SE4.</p>
<h3><a id="user-content-kwzviewer" class="anchor" aria-hidden="true" href="#kwzviewer"><svg class="octicon octicon-link" viewbox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>kwzViewer</h3>
<p>Crappy viewer made with <a href="https://www.pygame.org/news" rel="nofollow">pygame</a>. It doesn't quite achieve realtime decoding for most Flipnotes, but it can be useful as a quick debug tool.</p>
<p><strong>Usage:</strong></p>
<div class="highlight highlight-source-shell"><pre>python kwzViewer.py <span class="pl-k">&lt;</span>input.kwz<span class="pl-k">&gt;</span></pre></div>
</article>
