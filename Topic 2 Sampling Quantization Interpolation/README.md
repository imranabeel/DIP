# DIP: Digital image processing


## Sampling, Quantization and Interpolation
```python
<pre class="with-background"><code class="with-syntax-highlighting code"><div class="example-prelude"><div><code class="  language-python"><span class="token keyword">from</span> scipy <span class="token keyword">import</span> random<span class="token punctuation">,</span> mgrid
<span class="token keyword">from</span> scipy<span class="token punctuation">.</span>interpolate <span class="token keyword">import</span> griddata
</code></div></div><div class="example-main"><div><code class="  language-python"><span class="token keyword">def</span> <span class="token function">f</span><span class="token punctuation">(</span>x<span class="token punctuation">,</span> y<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">return</span> x <span class="token operator">+</span> y

grid_x<span class="token punctuation">,</span> grid_y <span class="token operator">=</span> mgrid<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">:</span><span class="token number">5j</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">:</span><span class="token number">1</span><span class="token punctuation">:</span><span class="token number">5j</span><span class="token punctuation">]</span>
points <span class="token operator">=</span> random<span class="token punctuation">.</span>rand<span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span>
values <span class="token operator">=</span> f<span class="token punctuation">(</span>points<span class="token punctuation">[</span><span class="token punctuation">:</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">,</span> points<span class="token punctuation">[</span><span class="token punctuation">:</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">)</span>

<span class="token keyword">print</span> griddata<span class="token punctuation">(</span>points<span class="token punctuation">,</span> values<span class="token punctuation">,</span> <span class="token punctuation">(</span>grid_x<span class="token punctuation">,</span> grid_y<span class="token punctuation">)</span><span class="token punctuation">,</span> method<span class="token operator">=</span><span class="token string">"cubic"</span><span class="token punctuation">)</span></code></div><div class="example-output"><h3 class="output-header">Output</h3><div class="output-wrapper"><div class="output">[[  nan   nan   nan   nan   nan]
 [  nan  0.5   0.75  1.     nan]
 [  nan  0.75  1.    1.25   nan]
 [  nan  1.    1.25  1.5    nan]
 [  nan   nan   nan   nan   nan]]
</div></div></div><div><code class="  language-python"><span class="token keyword">print</span> griddata<span class="token punctuation">(</span>points<span class="token punctuation">,</span> values<span class="token punctuation">,</span> <span class="token punctuation">(</span>grid_x<span class="token punctuation">,</span> grid_y<span class="token punctuation">)</span><span class="token punctuation">,</span> method<span class="token operator">=</span><span class="token string">"nearest"</span><span class="token punctuation">)</span></code></div><div class="example-output"><h3 class="output-header">Output</h3><div class="output-wrapper"><div class="output">[[ 0.15816536  0.15816536  0.6364253   0.85283824  1.0880222 ]
 [ 0.33930886  0.33930886  0.79653985  1.0387893   1.0880222 ]
 [ 0.75785667  0.93651026  1.02458428  1.24200854  1.4936412 ]
 [ 0.75785667  0.75785667  1.32061996  1.33740459  1.6481689 ]
 [ 0.75785667  1.34710428  1.34710428  1.77777691  1.77777691]]
</div></div></div></div><div class="example-postlude"></div></code></pre>
'''