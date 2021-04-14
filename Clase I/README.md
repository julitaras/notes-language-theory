<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Clase I</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li>
<ul>
<li><a href="#acerca-del-lenguaje-oz">Acerca del lenguaje oz:</a></li>
<li><a href="#records">Records</a></li>
<li><a href="#tuplas">Tuplas</a></li>
<li><a href="#binding">Binding</a></li>
<li><a href="#lista">Lista</a></li>
<li><a href="#pattern-matching">Pattern Matching</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 align="center">TDL - Clase I
</h1><p>Objetivo:</p>
<ul>
<li>Entender a la programación como conceptos</li>
<li>Entender a los lenguajes por los conceptos que tienen</li>
</ul>
<p><strong>Como? - Analizar los lenguajes de programacion</strong></p>
<ul>
<li>A traves de su sintaxis y su semantica
<ul>
<li>Sintaxist
<ul>
<li>Como se escribe - Estructura o forma de los programas</li>
</ul>
</li>
<li>Semantica:
<ul>
<li>Como se ejecuta</li>
</ul>
</li>
</ul>
</li>
</ul>
<p>Vamos a utilizar --&gt; lenguaje Oz</p>
<hr>
<p>Modelo computacional</p>
<ul>
<li>Sistema formal que define <strong>como</strong> se ejecutan los calculos</li>
<li>Se define en terminos de los conceptos que incluye.</li>
<li>Definicion mas precisa de un paradigma de programacion</li>
<li>Declarativo - Imperativo
<ul>
<li><strong>Declarativo:</strong> Uno habla del QUE. --&gt; Por ejemplo: SQL.  Algo muy fuerte es la inmutalidad.</li>
<li><strong>Imperativo:</strong> Tiene que ver con las instrucciones. Uno habla del COMO. Ejemplo: Una receta, ya que se esta diciendo COMO hacerlo.</li>
</ul>
</li>
</ul>
<p>Determinismo --&gt; Ante un mismo input tengo que tener el mismo output. --&gt; Caracterista de programacion funcional.</p>
<p><strong>Que es un lenguaje de programacion?</strong><br>
Se dice que es un lenguaje de programacion si es <strong>turing completo</strong><br>
Si puede ser procesado por la maquina que turing hizo.</p>
<ul>
<li>Sintaxis</li>
<li>Semantica</li>
<li>Pragmatica</li>
</ul>
<p><code>Mozart</code> --&gt; Implementacion de <code>Oz</code></p>
<p>Tarea para el hogar:</p>
<ul>
<li>Instalar Mozart y Oz</li>
<li>Bajarse emacs</li>
</ul>
<hr>
<h2 id="acerca-del-lenguaje-oz">Acerca del lenguaje <code>oz</code>:</h2>
<h3 id="hello-world">Hello world:</h3>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token atom builtin">'Hello world!'</span><span class="token punctuation">}</span>
</code></pre>
<h3 id="variables">Variables</h3>
<ul>
<li>Variables de simple asignacion, no mutan</li>
<li>Una variable no es mas que un nombre de algo, representa el nombre de un valor</li>
<li>La vraible siempre empieza con mayuscula</li>
<li>Tipado es dinamico.</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">declare</span> <span class="token variable">A</span> <span class="token variable">B</span> <span class="token variable">C</span>
<span class="token variable">A</span> <span class="token operator">=</span> <span class="token number">4</span>
<span class="token variable">B</span> <span class="token operator">=</span> <span class="token number">5</span> 
<span class="token variable">C</span> <span class="token operator">=</span> <span class="token variable">A</span><span class="token operator">*</span><span class="token variable">B</span> <span class="token operator">+</span> <span class="token number">3</span>
<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">C</span><span class="token punctuation">}</span>
</code></pre>
<h4 id="scopes">Scopes</h4>
<ul>
<li>En donde existe esa variable. En donde vive</li>
<li>Dos tipos de scopes:
<ul>
<li>Globales</li>
<li>Locales</li>
</ul>
</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">A</span> <span class="token variable">B</span> <span class="token variable">C</span> <span class="token keyword">in</span>
	<span class="token variable">A</span> <span class="token operator">=</span> <span class="token number">4</span>
	<span class="token variable">B</span> <span class="token operator">=</span> <span class="token number">5</span> 
	<span class="token variable">C</span> <span class="token operator">=</span> <span class="token variable">A</span><span class="token operator">*</span><span class="token variable">B</span> <span class="token operator">+</span> <span class="token number">3</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">C</span><span class="token punctuation">}</span>
<span class="token keyword">end</span> 
</code></pre>
<blockquote>
<p>No usar <code>declare</code> nunca</p>
</blockquote>
<ul>
<li>Se puede tener un local dentro de otro, puedo re declarar variables</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">A</span> <span class="token variable">B</span> <span class="token variable">C</span> <span class="token keyword">in</span>
	<span class="token variable">A</span> <span class="token operator">=</span> <span class="token number">4</span>
	<span class="token variable">B</span> <span class="token operator">=</span> <span class="token number">5</span> 
	<span class="token keyword">local</span> <span class="token variable">A</span> <span class="token keyword">in</span>
		<span class="token variable">A</span> <span class="token operator">=</span> <span class="token number">10</span>
		<span class="token variable">C</span> <span class="token operator">=</span> <span class="token variable">A</span><span class="token operator">*</span><span class="token variable">B</span> <span class="token operator">+</span> <span class="token number">3</span>
		<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">C</span><span class="token punctuation">}</span>
	<span class="token keyword">end</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">C</span><span class="token punctuation">}</span>
<span class="token keyword">end</span> 
</code></pre>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Uno</span> <span class="token variable">Dos</span> <span class="token keyword">in</span>
	<span class="token variable">Uno</span> <span class="token operator">=</span> <span class="token number">1</span>
	<span class="token number">2</span> <span class="token operator">=</span> <span class="token variable">Dos</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">Uno</span> <span class="token operator">+</span> <span class="token variable">Dos</span><span class="token punctuation">}</span>
<span class="token keyword">end</span> 
</code></pre>
<p>2 <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>⇔</mo></mrow><annotation encoding="application/x-tex">\Leftrightarrow</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.36687em; vertical-align: 0em;"></span><span class="mrel">⇔</span></span></span></span></span> Dos</p>
<h3 id="funciones">Funciones</h3>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Mayor</span> <span class="token variable">A</span> <span class="token variable">B</span> <span class="token variable">M</span> <span class="token keyword">in</span>
	<span class="token keyword">fun</span> <span class="token punctuation">{</span><span class="token function">Mayor</span> <span class="token variable">X</span> <span class="token variable">Y</span><span class="token punctuation">}</span>
		<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token variable">X</span> <span class="token operator">&gt;</span> <span class="token variable">Y</span><span class="token punctuation">)</span> <span class="token keyword">then</span>
			<span class="token variable">X</span> 
		<span class="token keyword">else</span>
			<span class="token variable">Y</span> 
		<span class="token keyword">end</span>
	<span class="token keyword">end</span> 
	<span class="token variable">A</span><span class="token operator">=</span><span class="token number">30</span>
	<span class="token variable">B</span><span class="token operator">=</span><span class="token number">20</span>
	<span class="token variable">M</span><span class="token operator">=</span><span class="token punctuation">{</span><span class="token function">Mayor</span> <span class="token variable">A</span> <span class="token variable">B</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">M</span><span class="token punctuation">}</span>
<span class="token keyword">end</span>
</code></pre>
<ul>
<li>Variables y funciones estan al mismo nivel
<ul>
<li>Funciones: Ciudadanos de primera clase. Como si fuera “un tipo mas de dato”</li>
</ul>
</li>
</ul>
<p>Otra sintaxis:</p>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Mayor</span> <span class="token variable">A</span> <span class="token variable">B</span> <span class="token variable">M</span> <span class="token keyword">in</span>
	<span class="token variable">Mayor</span> <span class="token operator">=</span> <span class="token keyword">fun</span> <span class="token punctuation">{</span><span class="token keyword">$</span> <span class="token variable">X</span> <span class="token variable">Y</span><span class="token punctuation">}</span>
		<span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token variable">X</span> <span class="token operator">&gt;</span> <span class="token variable">Y</span><span class="token punctuation">)</span> <span class="token keyword">then</span>
			<span class="token variable">X</span> 
		<span class="token keyword">else</span>
			<span class="token variable">Y</span> 
		<span class="token keyword">end</span>
	<span class="token keyword">end</span> 
	<span class="token variable">A</span><span class="token operator">=</span><span class="token number">30</span>
	<span class="token variable">B</span><span class="token operator">=</span><span class="token number">20</span>
	<span class="token variable">M</span><span class="token operator">=</span><span class="token punctuation">{</span><span class="token function">Mayor</span> <span class="token variable">A</span> <span class="token variable">B</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">M</span><span class="token punctuation">}</span>
<span class="token keyword">end</span>
</code></pre>
<p><code>$</code> en la funcion, vendria a representar una funcion <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>λ</mi></mrow><annotation encoding="application/x-tex">\lambda</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.69444em; vertical-align: 0em;"></span><span class="mord mathnormal">λ</span></span></span></span></span></p>
<ul>
<li>La variables no necesariamente mutan</li>
<li>Las funciones son variabes que tienen guardado otro tipo de valor</li>
</ul>
<h3 id="expression-vs-statement">Expression vs Statement</h3>
<ul>
<li><strong>Statement</strong> --&gt; A= 30 es un statemente , M={Mayor A B} es un statemente
<ul>
<li>Es cualquier bloque o instreucccion que no devuelve valor</li>
</ul>
</li>
<li><strong>Expression</strong> algo que devuelve valor. Algop que es asignable a una variable.</li>
</ul>
<p>Las funciones no tienen return.<br>
Las funciones devuelven a ultima expresion.</p>
<h2 id="records">Records</h2>
<ul>
<li>Estructura de datos para agrupar referencias</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token function">tree</span><span class="token punctuation">(</span><span class="token attr-name">key</span><span class="token punctuation">:</span> <span class="token variable">I</span> <span class="token attr-name">value</span><span class="token punctuation">:</span> <span class="token attr-name">left</span><span class="token punctuation">:</span><span class="token variable">LT</span> <span class="token attr-name">right</span><span class="token punctuation">:</span><span class="token variable">RT</span><span class="token punctuation">)</span>
</code></pre>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Arbol</span> <span class="token keyword">in</span>
	<span class="token variable">Arbol</span> <span class="token operator">=</span> <span class="token function">tree</span><span class="token punctuation">(</span><span class="token attr-name">key</span><span class="token punctuation">:</span> <span class="token number">1</span> <span class="token attr-name">value</span><span class="token punctuation">:</span> <span class="token number">8</span> <span class="token attr-name">left</span><span class="token punctuation">:</span> <span class="token keyword">nil</span> <span class="token attr-name">right</span><span class="token punctuation">:</span> <span class="token keyword">nil</span><span class="token punctuation">)</span>
	
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">Arbol</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">Arbol</span><span class="token punctuation">.</span>value<span class="token punctuation">}</span>
<span class="token keyword">end</span>
</code></pre>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Alumno</span> <span class="token variable">E</span> <span class="token keyword">in</span>
	<span class="token variable">E</span> <span class="token operator">=</span> <span class="token number">20</span>
	<span class="token variable">Alumno</span> <span class="token operator">=</span> <span class="token function">persona</span><span class="token punctuation">(</span><span class="token attr-name">nombre</span><span class="token punctuation">:</span> <span class="token atom builtin">'Nombre'</span> <span class="token attr-name">apellido</span><span class="token punctuation">:</span> <span class="token atom builtin">'Apellido'</span> <span class="token attr-name">edad</span><span class="token punctuation">:</span> <span class="token variable">E</span><span class="token punctuation">)</span>
	
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">Alumno</span><span class="token punctuation">}</span>
<span class="token keyword">end</span>
</code></pre>
<p><strong>arity</strong> --&gt;lista de features que tiene el record<br>
width --&gt;<br>
label  —&gt; Nombre de el record</p>
<h2 id="tuplas">Tuplas</h2>
<ul>
<li>Es un record cuyos features son numericos comenzando por el 1.</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">Alumno</span> <span class="token variable">E</span> <span class="token keyword">in</span>
	<span class="token variable">E</span> <span class="token operator">=</span> <span class="token number">20</span>
	<span class="token variable">Alumno</span> <span class="token operator">=</span> <span class="token function">persona</span><span class="token punctuation">(</span><span class="token atom builtin">'Nombre'</span> <span class="token atom builtin">'Apellido'</span> <span class="token variable">E</span><span class="token punctuation">)</span>
	
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">Alumno</span><span class="token punctuation">}</span>
<span class="token keyword">end</span>
</code></pre>
<h2 id="binding">Binding</h2>
<ul>
<li>Asignale un valor a una variable</li>
</ul>
<h2 id="lista">Lista</h2>
<ul>
<li>Una tupla de dos elementos</li>
<li>El primer elemento es el primer</li>
<li>El segundo elemento es el resto de la cola</li>
</ul>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">L1</span> <span class="token variable">L2</span> <span class="token keyword">in</span>
	<span class="token variable">L1</span> <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token number">1</span> <span class="token number">2</span> <span class="token number">3</span> <span class="token number">4</span> <span class="token number">5</span> <span class="token number">6</span><span class="token punctuation">]</span>
	<span class="token variable">L2</span> <span class="token operator">=</span> <span class="token number">1</span><span class="token operator">|</span><span class="token number">2</span><span class="token operator">|</span><span class="token number">3</span><span class="token operator">|</span><span class="token number">4</span><span class="token operator">|</span><span class="token number">5</span><span class="token operator">|</span><span class="token number">6</span><span class="token operator">|</span>
	
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L1</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L2</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L1</span><span class="token punctuation">.</span><span class="token number">1</span><span class="token punctuation">}</span> <span class="token comment">%Cabeza, primer elemento%</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L2</span><span class="token punctuation">.</span><span class="token number">1</span><span class="token punctuation">}</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L1</span><span class="token punctuation">.</span><span class="token number">2</span><span class="token punctuation">}</span> <span class="token comment">%Resto de la cola%</span>
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L2</span><span class="token punctuation">.</span><span class="token number">2</span><span class="token punctuation">}</span> 
	<span class="token punctuation">{</span><span class="token function">Browse</span> <span class="token variable">L</span><span class="token punctuation">.</span><span class="token number">2.2</span><span class="token punctuation">.</span><span class="token number">2.1</span><span class="token punctuation">}</span> <span class="token comment">%Acceder a 5to elemento%</span>
<span class="token keyword">end</span>
</code></pre>
<h2 id="pattern-matching">Pattern Matching</h2>
<p>Trata de matchear un record por el label, features</p>
<pre class=" language-oz"><code class="prism  language-oz"><span class="token keyword">local</span> <span class="token variable">L1</span> <span class="token variable">L2</span> <span class="token keyword">in</span>
	<span class="token variable">EdadAlumno</span>
<span class="token keyword">end</span>
</code></pre>

    </div>
  </div>
</body>

</html>
