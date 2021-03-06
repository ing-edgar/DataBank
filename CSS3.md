---


---

<p><strong>Me quede en FLOATS</strong></p>
<p>ATENCION:</p>
<p>ritten th <a href="https://stackedit.io/">StackEdit</a>.<br>
ATENCION:</p>
<p><strong>Me quede en 8.4 padding</strong><br>
<strong>Probablemente necesito leer  9 Visual formatting model para entender muchas cosas del cap. 8</strong></p>
<p>Arranque con CSS2.1, Despues tengo que leer todas las otras specs</p>
<p>CSS2.1:<br>
<a href="https://www.w3.org/TR/CSS2/intro.html#q2.0">https://www.w3.org/TR/CSS2/intro.html#q2.0</a></p>
<p>LAS DEMAS:<br>
<a href="https://www.w3.org/TR/css-2018/">https://www.w3.org/TR/css-2018/</a></p>
<h1 id="css-2.1">CSS 2.1</h1>
<h2 id="ideologia">Ideologia</h2>
<p>CSS es un lenguaje de estilos pero tambien intenta mantener ciertos ideales, estos son:</p>
<ul>
<li><strong>GENERALIDAD:</strong> CSS es un lenguaje ideado para presentar y describir contenido en <strong>cualquier formato (voz, texto escrito, impreso, audio, imagenes, braille, etc)</strong> aunque sus aplicaciones mas conocidas son la renderizacion visual de paginas web.</li>
<li><strong>BACKWARDS COMPATIBLE:</strong> CSS debe ser compatible con todas sus versiones anteriores</li>
<li><strong>FORWARD COMPATIBLE:</strong> SI una regla css no se conoce se ignora, siempre se preserva el contenido</li>
<li><strong>COMPLEMENTARIO:</strong> Debe ser posible cambiar los estilos con minimos cambios en el contenido/markup</li>
<li><strong>DEVICE/VENDOR INDEPENDENT:</strong> Deben funcionar en todo dispositivo y para toda marca</li>
<li><strong>ACCESIBILIDAD:</strong> CSS proovera de herramientas para que el contenido sea accesbile a personas con inhabilidades</li>
</ul>
<h2 id="terminos">Terminos</h2>
<p>CSS utiliza ciertos terminos propios:</p>
<ul>
<li><strong>Canvas</strong>  - No confundir con el HTML5 canvas, es el area donde css va a renderizar. es infinita en todas las dimensiones y se elige una subarea dependiendo del media type, generalmente es elegido por el user-agent. se define como <strong>El area donde la FORMMATTING STRUCTURE</strong> se renderiza</li>
<li><strong>Source document</strong> - El documento al cual se le aplicaran las stylesheets (ej HTML)</li>
<li><strong>Document tree</strong> - Un arbol de nodos que contiene los elementos del source document antes de ser  aplicadas las reglas de los stylesheets. (generalmente un arbol de elementos html)</li>
<li><strong>Formatting structure</strong> - Una descripcion programatica (generalmente arbol de nodos) de lo que se va a mostrar, se computa a partir de un Document tree y las style sheets</li>
<li><strong>Canvas</strong>  - No confundir con el HTML5 canvas, es el area donde css va a renderizar. es infinita en todas las dimensiones y se elige una subarea dependiendo del media type, generalmente es elegido por el user-agent. se define como <strong>El area donde la FORMMATTING STRUCTURE</strong> se renderizara.</li>
<li><strong>Selector</strong> - Algo que te permite indicar un elemento o elementos del document tree y/o
<ul>
<li>relaciones entre ellos</li>
<li>sus atributos</li>
<li>Su estado (:hover)</li>
<li>Partes de su contenido (:first-line)</li>
</ul>
</li>
</ul>
<h2 id="procesamiento-y-formatting-structure">procesamiento y formatting structure</h2>
<h3 id="unidades-de-medida">Unidades de medida</h3>
<blockquote>
<p><strong>ATENCION: Esta parte fue reemplazada por CSS 3!!!</strong></p>
</blockquote>
<p><strong>ABOLUTAS:</strong></p>
<ul>
<li><strong>in</strong>: inches — 1in is equal to 2.54cm.</li>
<li><strong>cm</strong>: centimeters</li>
<li><strong>mm</strong>: millimeters</li>
<li><strong>pt</strong>: points — the points used by CSS are equal to 1/72nd of 1in.</li>
<li><strong>pc</strong>: picas — 1pc is equal to 12pt.</li>
<li><strong>px</strong>: pixel units — 1px is equal to 0.75pt.</li>
</ul>
<blockquote>
<p><strong>Las medidas se aproximan dependiendo del css media type basado en una medida de referencia (EJ:px para pantalla, mm para impresion)</strong></p>
<ul>
<li><strong>Px</strong> Se mide como el pixel de referancia en dispositivos, que puede no ser un pixel fisico. se usa tambien el pixel de referencia para deducir el tamaño al pasar a mm para imprimir medidan en px<br>
<strong>mm</strong> Se mide en mm reales para impresion y se aproxima en px fisicos para renderizar en pantallas<br>
<strong>PIXEL DE REFERECIA:</strong> Es el tamaño de un pixel caluclado como 1/96 inch a una distancia de un brazo y con un angulo de vision,</li>
</ul>
</blockquote>
<p><strong>RELATIVAS:</strong></p>
<ul>
<li>
<p><strong>em</strong> The ‘em’ unit is equal to the computed value of the <a href="https://www.w3.org/TR/CSS2/fonts.html#propdef-font-size">‘font-size’</a> property of the element on which it is used. The exception is when ‘em’ occurs in the value of the ‘font-size’ property itself, in which case it refers to the font size of the parent element.</p>
</li>
<li>
<p><strong>%</strong> es un procentaje,  <strong>su valor computado depende de cada propiedad</strong> y no hay regla general.</p>
</li>
</ul>
<h3 id="colores">Colores</h3>
<p>Los colores se implementan siempre en <strong>RGB</strong>, hay dos maneras de escribirlos pero <strong>siempre</strong> simbolizan RGB</p>
<ul>
<li><strong>rgb(255,255,255)</strong> - Byte en rojo, verde y azul en numeros 0-255</li>
<li><strong>#rrggbb</strong> - Byytes en hexadecimal con dos caracteres para cada color de RGB ej ff=255</li>
<li><strong>#rgb</strong> bytes en exadecimal acortado, un caracter para cada color de RGB ej f=ff=255</li>
</ul>
<blockquote>
<p>A su vez hay colores mapeados en keywords, ej <strong>red, green, blue</strong></p>
</blockquote>
<h3 id="document-tree-y-formatting-structure">Document tree y formatting structure</h3>
<p>La especificacion propone un modelo de procesamiento  que funciona de la siguiente manera</p>
<ul>
<li>Se lee el documento html/xml y se genera un arbol de nodos llamado <strong>Document tree</strong> con un nodo por cada elemento</li>
<li>Se identifica el <strong>media type</strong></li>
<li>Se juntan todas las stylesheets y se extrae  el valor computado final de cada propiedad para cada elemento</li>
<li>Se añade al <strong>document tree</strong> las propiedades y valores css</li>
<li>Se genera un nuevo arbol de nodos llamado <strong>Formatting structure/tree</strong> que indica los elementos que se mostraran. <strong>este se puede parecer mucho al Document tree pero puede haber elementos de mas (:after, :before, los bullets de un elemento &lt;li&gt;) o de menos (display:none)</strong></li>
<li>Se Muestra el resultado en el medio elegido (pantalla, papel, etc)</li>
</ul>
<h3 id="computo-de-valores">Computo de valores</h3>
<h4 id="valores-que-se-calculan">Valores que se calculan</h4>
<p>Para cada propiedad se debe calcular una serie de valores:</p>
<ul>
<li><strong>Valor especificado:</strong> El valor de la propiedad que se obtiene despues de las herencias, cascada, etc.
<ul>
<li><strong>Valor computado / a heredar:</strong> El valor que se heredara a los elementos hijos, llamado <em>computed value</em>
<ul>
<li><strong>Valor usado/absoluto:</strong> El valor que se calcula en terminos absolutos a partir del valor a heredar. ej: de % a pixeles para mostrar en pantalla.</li>
</ul>
</li>
</ul>
</li>
</ul>
<h4 id="valores-especificados">Valores especificados</h4>
<p>Se calculan de la siguiente manera</p>
<ol>
<li>Si la  <a href="https://www.w3.org/TR/CSS2/cascade.html#cascade">cascade</a> resuelve un valor,  se usa ese.</li>
<li>Si hay una propiedad <a href="https://www.w3.org/TR/CSS2/cascade.html#inheritance">inherited</a> se usa el <em>computed value</em> del elemento padre.</li>
<li>Se usa la propiedad <em>default</em> o <em>initial</em></li>
</ol>
<h4 id="valores-a-heredar--computados">Valores a heredar / computados</h4>
<ul>
<li>Las URIs se hacen absolutas</li>
<li>Se pasan todas las medidas posibles a Px (em, %, etc) (salvo las heredadas)</li>
<li>Las propiedades se computan de acuerdo a cada una de sus funciones de computo especificas.</li>
</ul>
<h4 id="valores-absoluto">Valores <strong>absoluto</strong></h4>
<p>Muchos valores no pueden ser computados por que dependen de que los elementos del padre sean pasados a valor abosluto para calcular sus valores y asi calcular los valores absolutos. En esta insatancia se hace eso.</p>
<h3 id="herencia">Herencia</h3>
<p>Para muchas propiedades se hereda su valor de <strong>A</strong> a <strong>B</strong> siempre que la propiedad del <strong>B</strong> no tenga un valor explicito declarado.<br>
Si la propiedad no hereda el valor de forma default se lo puede forzar usando el valor <code>'inherit'</code></p>
<blockquote>
<p>Es importante aclarar que el valor heredado es siempre el <strong>Valor a heredar / computado</strong>  y no el <strong>valor especificado ni absoluto</strong></p>
</blockquote>
<p>Este valor se transforma en el nuevo <strong>valor especificado Y valor computado</strong> del elemento <strong>B</strong>.</p>
<p><strong>EJ:</strong></p>
<pre><code>body { font-size: 10pt }
h1 { font-size: 130% }
&lt;BODY&gt;
  &lt;H1&gt;A &lt;EM&gt;large&lt;/EM&gt; heading&lt;/H1&gt;
&lt;/BODY&gt;
</code></pre>
<p>El <strong>valor computado y entonces heredado</strong> en el h1 es <strong>13pt</strong>, entonces el EM <strong>hereda el valor 13p y NO 130%</strong></p>
<h3 id="the-cascade">The cascade</h3>
<p>El user agent colocara un pero a cada regla declarada y luego seleccionara la regla con mayor peso. Se calculan con la siguiente prioridad.</p>
<h4 id="calculo-de-cascada">Calculo de cascada</h4>
<ul>
<li><strong>Busqueda:</strong> Buscar todas las reglas que apliquen a un elemento.</li>
<li><strong>Origen:</strong> Ordenar en orden de prioridad por
<ol>
<li><strong>user-agent</strong> declarations</li>
<li><strong>user</strong> normal declarations</li>
<li><strong>author</strong> normal declarations</li>
<li><strong>author</strong> important declarations</li>
<li><strong>user</strong> important declarations (para accesibilidad)</li>
</ol>
</li>
<li><strong>Especificidad:</strong> Tomar las de mayor prioridad y ordenarlas por especificidad tomando la mas especifica.</li>
<li><strong>Orden:</strong> Si aun quedan valores de igual prioridad, tomar el ultimo declarado.</li>
</ul>
<h4 id="calculo-de-especificidad">Calculo de especificidad</h4>
<p>La especificidad que se usa en el calculo de cascada se computa con las siguientes prioridades.</p>
<ol>
<li><strong>Styles=</strong> Estilos indicados en atributo <em>styles</em></li>
<li><strong>#Id</strong> Estilos indicados mediante referencia al Id</li>
<li><strong>Cantidad de selectores usados</strong> Mayor cantidad de selectores, atributos y pseudo-clases se considera como mas especifico <strong>ej</strong> <code>.Conteneodor .parrafo .enfasis{}</code></li>
<li><strong>Cantidad de nombres de elementos usados</strong> Cuantos mas nombres de elementos usados mas especificidad <strong>ej</strong> <code>div h1{}</code></li>
</ol>
<h2 id="selectores">Selectores</h2>
<p>CSS 2.1 provee la siguiente lista de selectores para ubicar uno o varios elementos dentro del <strong>Document tree</strong></p>
<h3 id="por-orden-de-los-elementospor-orden-de-los-elementos">Por orden de los elementos<strong>POR ORDEN DE LOS ELEMENTOS</strong></h3>
<ul>
<li><strong>*</strong> - Cualquier elemento, cuando no se especifica un elemento en un selector se presume que se utiliza este</li>
<li><strong>E</strong> - Donde E es un tipo de elemento ej “div”, selecciona los elementos de ese tipo</li>
<li><strong>E F</strong> elementos de tipo F que sean descendientes de un elemento tipo E</li>
<li><strong>E &gt; F</strong> elemento tipo F que sea hijo directo de F</li>
<li><strong>E + F</strong> elemento de tipo F cuyo hermano inmediato precedente sea E (semanticamente tiene sentido entonces E + F)</li>
<li><strong>E:first-child</strong> Elemento E que ademas sea el primer hijo  de su elemento padre</li>
</ul>
<h3 id="por-atributo-de-los-elementospor-atributo-de-los-elementos">Por atributo de los elementos<strong>POR ATRIBUTO DE LOS ELEMENTOS:</strong></h3>
<blockquote>
<p><strong>ATENCION:</strong></p>
<ul>
<li>las <strong>clases de CSS</strong> son atributos y se povee el <strong>shorthand .foo</strong> para referirse a clases, pero <strong>la forma original seria *[class~=“foo”]</strong></li>
<li>Cuando no se provee elemento <strong>E</strong> se presume <strong>*</strong></li>
</ul>
</blockquote>
<ul>
<li><strong>E[foo]</strong> Elemento E con un atributo foo (sin importar el valor)</li>
<li><strong>E[foo=“warning”]</strong> Elemento E con atributo foo valor ‘warning’</li>
<li><strong>E[foo~=“warning”]</strong> elemento E con atributo foo que tiene una lista de valores separado por espacios entre los cuales esta ‘warning’</li>
<li><strong>E[foo|=“warning”]</strong> elemento E con atributo foo que tiene una lista de valores separado por guiones entre los cuales esta ‘warning’</li>
<li><strong>E#myid</strong> Elemmento E con id #myid</li>
</ul>
<h3 id="pseudo-clasespseudo-clases">Pseudo-clases<strong>PSEUDO-CLASES</strong></h3>
<p>Son la forma que tiene CSS de acceder a informacion que no esta explicitamente provista en el lenguaje de markup o el arbol de nodos <strong>Document tree</strong>, por ejemplo el primer renglon de un parrafo</p>
<ul>
<li><strong>E:link</strong>  si E es un achor NO visitado</li>
<li><strong>E:visited</strong> si E es un achor SI visitado</li>
<li><strong>E:active, E:hover, E:focus</strong> Si el elemento es sujeto a una accion del usuario</li>
</ul>
<p>Podes combinar selectores uno despues del otro para indicar mas especificamente que deseas seleccionar.</p>
<h3 id="pseudo-elementos">Pseudo-elementos</h3>
<ul>
<li><strong>E:first-line</strong> La primera linea de texto del contenido del elemento E se enmarca en un pseudo elemento al que le podes poner estilos</li>
<li><strong>E:first-letter</strong> La primera letra del elemento E se enmarca en un pseudo elemento al que le podes poner estilos</li>
<li><strong>E:after</strong> Inserta un pseudo elemento despues del elemento E el cual debe tener contenido usando <em>content:""</em> y se le pueden agregar estilos</li>
<li><strong>E:before</strong> Inserta un pseudo elemento antes del elemento E el cual debe tener contenido usando <em>content:""</em> y se le pueden agregar estilos</li>
</ul>
<h2 id="media-types">Media types</h2>
<p>Una de las propiedades de CSS es que describe la presentacion del contenido en cualquier formato (audio, braile, texto, impreso, digital).</p>
<p>Algunas propiedades de CSS aplican a uno o varios media types, otros pueden aplicar a todos.</p>
<blockquote>
<p><strong>Las propiedades no declaradas para un media type especifico aplican a todos los media types.</strong></p>
</blockquote>
<p><strong>Se declara asi:</strong></p>
<pre><code>@media print, scree, otros {
  /* style sheet for print goes here */
}
</code></pre>
<p><strong>Los media types validos son:</strong></p>
<ul>
<li><strong>all</strong> Suitable for all devices.</li>
<li><strong>braille</strong> Intended for braille tactile feedback devices.</li>
<li><strong>embossed</strong> Intended for paged braille printers.</li>
<li><strong>handheld</strong> Intended for handheld devices (typically small screen, limited bandwidth).</li>
<li><strong>print</strong> Intended for paged material and for documents viewed on screen in print preview mode.</li>
<li><strong>projection</strong> Intended for projected presentations, for example projectors.</li>
<li><strong>screen</strong> Intended primarily for color computer screens.</li>
<li><strong>speech</strong> Intended for speech synthesizers.</li>
<li><strong>tty</strong> Intended for media using a fixed-pitch character grid (such as teletypes, terminals, or portable devices with limited display capabilities).</li>
<li><strong>tv</strong> Intended for television-type devices (low resolution, color, limited-scrollability screens, sound available).</li>
</ul>
<h2 id="box-model">Box model</h2>
<p>TODOS los elementos en CSS se representan como CAJAS. El modelo de cajas se basa en que <strong>un elemento consiste en varias cajas una dentro de la otra</strong>, esas cajas son:</p>
<ul>
<li>El tamaño del contenido</li>
<li>El padding</li>
<li>El border</li>
<li>El Margen</li>
</ul>
<p><img src="https://lh3.googleusercontent.com/BSdXPy1iKoW_RdmcsEKVAomZV7hcOWc2t3DHqPnHPZeBrjYYxV3JsN2BzdoCs8BlIPchL5dprAH6" alt="enter image description here" title="ff"></p>
<ul>
<li>El tamaño del contenido</li>
<li>El padding</li>
<li>El border</li>
<li>El Margen</li>
</ul>
<h3 id="margen">Margen</h3>
<ul>
<li>Siempre es <strong>transparente</strong></li>
<li>Su <strong>%</strong> se calcula en base al ancho del <strong>contianing blockenido</strong>.</li>
<li>Para elementos <strong>inline-block se ignoran</strong> los margenes <strong>Top y Bottom</strong></li>
</ul>
<p>Tiene las siguientes caracteristicas</p>
<blockquote>
<ul>
<li><strong>Value:</strong> length | percentage |auto | inherit</li>
<li><strong>Initial:</strong> 0</li>
<li><strong>Applies to:</strong> all elements except elements with table display types other than table-caption, table and inline-table</li>
<li><strong>Inherited:</strong> no</li>
<li><strong>Percentages:</strong> refer to width of containing block</li>
<li><strong>Media:</strong> <a href="https://www.w3.org/TR/CSS2/media.html#visual-media-group">visual</a></li>
<li><strong>Computed value:</strong> the percentage as specified or the absolute length</li>
</ul>
</blockquote>
<h4 id="collapsing-margins">Collapsing margins</h4>
<p><a href="https://www.youtube.com/watch?v=uEfH6qnFF6Y&amp;t=944s">VER VIDEO PARA ENTENDER BIEN</a></p>
<p>Los margenes <strong>verticales</strong> colapsan en uno solo <strong>siempre que se tocan y son block o inline block elements Y participan del mismo BFC</strong>. para evitar que se toquen hay que colocar algo en el medio (ej border)<br>
<a href="https://www.w3.org/TR/CSS2/box.html#collapsing-margins">hay varias posibles condiciones para que los margenes colapsen</a></p>
<blockquote>
<p>Este mecanismo pemite que los textos esten separados por margenes siempre de por lo menos un cierto tamaño (ej que no se sumen)</p>
</blockquote>
<p><strong>Eso puede ocurrir con:</strong></p>
<ul>
<li><strong>Siblings</strong> si se toca el margin-bottom de uno con el margin-top de otro</li>
<li><strong>parent-child/grandchild SUPER ANTI-INTUITIVO</strong> si los dos margenes top se tocan (no hay padding o border)
<ul>
<li><strong>En este caso si el margen colapsado es el del child se genera un margen adentro del elemento hijo que empuja al parent y todos los children hacia abajo</strong></li>
</ul>
</li>
</ul>
<h3 id="padding">Padding</h3>
<ul>
<li>Es del color del background</li>
<li>Su <strong>%</strong> se calcula en base al ancho del <strong>contianing block</strong>.</li>
<li>A diferencia del margen, no puede ser negativo</li>
</ul>
<p>Tiene las siguientes caracteristicas:</p>
<blockquote>
<p><strong>Value:</strong> length | percentage |auto | inherit| inherit<br>
<strong>Initial:</strong> 0<br>
<strong>Applies to:</strong> all elements except table-row-group, table-header-group, table-footer-group, table-row, table-column-group and table-column<br>
<strong>Inherited:</strong> no<br>
<strong>Percentages:</strong> refer to width of containing block<br>
<strong>Media:</strong> <a href="https://www.w3.org/TR/CSS2/media.html#visual-media-group">visual</a><br>
<strong>Computed value:</strong> the percentage as specified or the absolute length</p>
</blockquote>
<h3 id="border">Border</h3>
<p>Los bordes son lineas de un color unico que van entre el margen y el padding.</p>
<h4 id="border-width"><strong>Border-Width</strong></h4>
<p>especifica el ancho del border y tiene las siguientes caracteristicas</p>
<blockquote>
<ul>
<li><strong>Value:</strong> Thin  | Medium | Thick | &lt;Length&gt; | inherit</li>
<li><strong>Initial:</strong> medium</li>
<li><strong>Applies to:</strong> all elements</li>
<li><strong>Inherited:</strong> no</li>
<li><strong>Percentages:</strong> N/A</li>
<li><strong>Media:</strong> <a href="https://www.w3.org/TR/CSS2/media.html#visual-media-group">visual</a></li>
<li><strong>Computed value:</strong> absolute length; ‘0’ if the border style is ‘none’ or ‘hidden’</li>
</ul>
</blockquote>
<h4 id="border-color"><strong>Border-Color</strong></h4>
<p>especifica el color del border y tiene las siguientes caracteristicas</p>
<blockquote>
<ul>
<li><strong>Value:</strong> &lt;color&gt; | transparent  | inherit</li>
<li><strong>Initial:</strong> see individual properties<br>
Applies to:all elements</li>
<li><strong>Inherited:</strong> no</li>
<li><strong>Percentages:</strong> N/A</li>
<li><strong>Media:</strong> <a href="https://www.w3.org/TR/CSS2/media.html#visual-media-group">visual</a></li>
<li><strong>Computed value:</strong> see individual properties</li>
</ul>
</blockquote>
<h4 id="border-style"><strong>Border-style</strong></h4>
<p>Especifica el tipo de linea del border</p>
<p><strong>none:</strong> No border; the computed border width is zero.<br>
<strong>hidden:</strong> Same as ‘none’, except in terms of <a href="https://www.w3.org/TR/CSS2/tables.html#border-conflict-resolution">border conflict resolution</a> for <a href="https://www.w3.org/TR/CSS2/tables.html">table elements</a>.<br>
<strong>dotted:</strong> The border is a series of dots.<br>
<strong>dashed:</strong> The border is a series of short line segments.<br>
<strong>solid:</strong> The border is a single line segment.<br>
<strong>double:</strong> The border is two solid lines. The sum of the two lines and the space between them equals the value of <a href="https://www.w3.org/TR/CSS2/box.html#propdef-border-width">‘border-width’</a>.<br>
<strong>groove:</strong> The border looks as though it were carved into the canvas.<br>
<strong>ridge:</strong> The opposite of ‘groove’: the border looks as though it were coming out of the canvas.<br>
<strong>inset:</strong> The border makes the box look as though it were embedded in the canvas.<br>
<strong>outset:</strong> The opposite of ‘inset’: the border makes the box look as though it were coming out of the canvas.</p>
<h2 id="visual-formatting-model">Visual formatting model</h2>
<p>Es el algoritmo por el cual CSS determina donde colocar los elementos del markup.</p>
<h3 id="terminos-1">Terminos</h3>
<ul>
<li>
<p><strong>containing block:</strong>  La caja dentro de la cual vive  un elemento, esta definida por la caja del elemento padre.</p>
</li>
<li>
<p><strong>Block-level boxes</strong> son boxes que participan del block formatting context</p>
</li>
<li>
<p><strong>Block container box</strong> osea que solo puede contener <em><strong>una</strong></em> de estas dos opciones de contenido.</p>
<ul>
<li>Solamente block-level boxes</li>
<li>Solo inline-level boxes<br>
<strong>Es decir que si tenes un elemento con blocks y inline elements los inline elements se transforman en block denominado BLOCK ANONIMO</strong></li>
</ul>
</li>
<li>
<p><strong>Line box</strong> La caja que representa un renglon con uno o mas inline elements en su interior</p>
</li>
</ul>
<h3 id="posicionamiento">Posicionamiento</h3>
<p>Hay 3 formas de posicionamiento</p>
<ul>
<li><strong>Normal flow:</strong>
<ul>
<li><strong>En Block formatting contexts (BFC)</strong></li>
<li><strong>En inline formatting contexts (IFC)</strong></li>
<li><strong>En relative positioning contexts (RPC)</strong></li>
</ul>
</li>
<li><strong>Floats:</strong> Se arma la caja como si estuviera en flow, luego se remueve de flow y se coloca a la izquierda/derecha del parent o float mas proximo</li>
<li><strong>Absolute positioning:</strong> Se remueve la caja del flow y se coloca en una posicion con respecto al container block.</li>
</ul>
<h3 id="normal-flow">Normal Flow</h3>
<p>En el normal flow <strong>cada elemento siempre pertenece a un y solo un formatting context</strong> que dictara cual es la posicion de ese elemento.</p>
<blockquote>
<p>Un elemento crea un Inline formatting context <strong>IFC</strong> si contiene solamente elementos inline, de lo contrario forma un Block formatting context <strong>BFC</strong>.</p>
</blockquote>
<p>si hay <strong>inline elements</strong> y <strong>block elements</strong> mezclados en el <strong>mismo formatting context</strong> entonces se usa el motor CSS coloca los inline elements en bloques para que participen del block formatting context. Esos blocks se denominan <strong>anonymous blocks</strong> y en su interior puede existir un <strong>IFC</strong></p>
<h4 id="block-elements">Block Elements</h4>
<p>Los block elements son elementos que:</p>
<ul>
<li><strong>se comportan como bloques</strong> (son siempre cuadrados)</li>
<li>Generalmente colocan su contenido dentro de un <strong>Block-level box</strong>, es decir que participan del <strong>BFC</strong></li>
<li>Generalmente se comporta como un <strong>Block container box</strong>, osea que su contenido sea solamente block-level boxes o inline-level boxes</li>
</ul>
<h4 id="block-formatting-context-bfc">Block Formatting Context (BFC)</h4>
<p><a href="https://www.smashingmagazine.com/2017/12/understanding-css-layout-block-formatting-context/">Ver mas</a></p>
<p>El BFC  es <strong>el area donde varios block  elements (parent,siblings, children, etc) estan contenidos e interactuan entre si</strong>.</p>
<p>En un BFC:</p>
<ul>
<li><strong>LAYOUT:</strong>
<ul>
<li>los elementos van <strong>uno encima del otro.</strong> y <strong>ocupan todo el ancho</strong></li>
<li>Los elementos <strong>tocan el borde izquierdo</strong> del contenedor, aun si hay floats</li>
<li>Los elementos <strong>inline SE TRANFORMAN EN BLOCKS</strong> mediante <strong>anonymous box generation</strong></li>
</ul>
</li>
<li><strong>COLLAPSING MARGINS:</strong> Solo los <strong>margenes</strong> de los elementos dentro del BFC pueden <strong>colapsar</strong> entre si</li>
</ul>
<p>Algunas propiedades de CSS hacen que un elemento pueda crear su propio BFC.</p>
<ul>
<li><code>overflow: auto</code></li>
<li><code>display: flow-root</code> - <a href="https://caniuse.com/#search=display:%20flow-root">ver support</a></li>
</ul>
<h4 id="anonymous-box-generation">Anonymous box generation</h4>
<p>Un <strong>BFC</strong> organiza todos los elementos en su interior como Blocks, sin embargo es obvio que podes tener un elemento con childs que sean inline y blocks mezclados.</p>
<p>Cuando pasa esto <strong>el BFC genera cajas alrededor de los inline elements</strong> para poder tratarlos como blocks. estas cajas no pueden ser seleccionadas con selectores, por eso se las llama <strong>anonymous boxes</strong></p>
<p><img src="https://lh3.googleusercontent.com/6HHOcEXZOGCGZaLLmVILN10fBSsdlwTgcjSNKYmXpttNk3UPKcowHE03Cjab-poZXA9BhPU7n2Or" alt="enter image description here"></p>
<h4 id="inline-elements">Inline elements</h4>
<p>Son aquellos elementos que</p>
<ul>
<li>Se distribuyen <strong>Horizontalmente</strong> uno al lado del otro</li>
<li>Participan del <strong>inline formatting context</strong></li>
<li><strong>Su alto y ancho</strong> estan totalmente definidos por el contenido y <strong>NO PUEDEN MODIFICARSE</strong></li>
<li><strong>Se distribuyen en renglones llamados line box</strong> que contienen uno o mas inline elements (ej texto y alguna palabra con negritas son line elements separados pero estan en el mismo renglon)</li>
</ul>
<p>Generalmente el texto y los links son inline elements</p>
<ul>
<li><strong>Inline-Block</strong> es un block colocado como si fuera un inline element.</li>
</ul>
<h4 id="inline-formatting-context-ifc">Inline Formatting Context (IFC)</h4>
<p>El IFCes <strong>el area donde varios inline elements estan contenidos e interactuan entre si</strong>. Se distribuye el contenido de derecha a izquierda hasta llegar al final del contenedor (o del contenido) y se lo coloca en un <strong>line box</strong>, luego se continua con ese proceso en un <strong>line box</strong> inmediatamente por debajo del al anterior .</p>
<p>Entonces <strong>un parrafo es una pila de line boxes</strong>.</p>
<p><strong>En un IFC:</strong></p>
<ul>
<li><strong>Los elementos van uno a la derecha del otro</strong> en normal flow, comenzando desde el lado superior izquierdo del containing box.</li>
<li><strong>Se agrupan en un LINE BOX por cada renglon</strong>. un Line box puede tener uno o mas inline elements (ej texto y negritas)
<ul>
<li><strong>Los elementos en un LINE BOX pueden ser alineados verticalmente</strong> de formas diferentes (ej: textos de diferentes tamaños alineados centrado quedan mal, los alineas en baseline para que queden en el mismo renglon)</li>
</ul>
</li>
</ul>
<p>Cada renglon es un <strong>line box:</strong><br>
<img src="https://lh3.googleusercontent.com/LF-qMyJATr4tKbLvzjCnab0L7Qv1kSLAusVHMn-apAwi9YuF-Nv0KQXtI-OifhH3Ycz5sWJ6pABn" alt="enter image description here"></p>
<p>Cada <strong>line box</strong> tiene uno o varios <strong>inline elements</strong><br>
<img src="https://lh3.googleusercontent.com/_a6ZSJrsRblNZx_mkxnYc0Vfz6b3tcUIOrg5gcgwoz1HDalJTFAqt-OFSY2MWb-5CwyM57aMByvF" alt="enter image description here"></p>
<p>Algunas propiedades de CSS hacen que un elemento pueda crear su propio BFC.</p>
<ul>
<li><code>overflow: auto</code></li>
<li><code>display: flow-root</code> - <a href="https://caniuse.com/#search=display:%20flow-root">ver support</a></li>
</ul>
<h3 id="relative-positioning">Relative positioning</h3>
<p>El Relative positioning es una forma de posicionamiento que coloca los objetos <strong>de manera relativa al lugar donde irian en su normal flow</strong> pero esto <strong>No afecta la posicion de los elementos a su alrededor</strong> y <strong>preserva el lugar originalmente  destinado al elemento</strong></p>
<blockquote>
<p><strong>El tamaño del elemento no puede cambiar cmo resultado del posicionamiento relativo!</strong></p>
</blockquote>
<p><strong>Posicionamiento:</strong></p>
<ul>
<li><strong>Left y Right:</strong> Son para posicionar el elemento. Solo podes usar <strong>una de las dos propiedades a la vez</strong> ya que el tamaño del elemento no puede cambiarse</li>
<li><strong>Top y bottom</strong> tambien son para posicionar el lemento y solo puede usarse <strong>una de las dos</strong> ya que el tamaño del elemento no puede cambiarse</li>
<li>Usar <strong>auto</strong> como valor equivale a usar 0.</li>
</ul>
<h3 id="float">Float</h3>
<p>El proposito de un float es que el contenido (blocks o inlines) pueda fluir a a lo largo de su altura.</p>
<h4 id="funcionamiento">Funcionamiento</h4>
<ul>
<li>
<p><strong>Un float:</strong></p>
<ul>
<li><strong>Se corre</strong> a la derecha o izquierda hasta tocar el borde de su contenedor o del float mas proximo</li>
<li><strong>Si no entra a la derecha o izquierda del float mas proximo</strong>, se coloca debajo de este y tocando el borde del contenedor</li>
<li>No forma parte del <strong>Normal flow</strong> pero tampoco <strong>sale del flow</strong> entonces <strong>El parent no puede deterinar su altura solo usando los floats</strong></li>
<li><strong>Permite que el contenido fluya a su alrededor</strong> osea que los bloques o inline elements quedaran al costado del float (si entran)</li>
</ul>
</li>
<li>
<p><strong>El contenido circundante:</strong></p>
<ul>
<li>Su box siempre <strong>pasa por atras del float</strong> para estar <strong>tocando el left side del contenedor</strong> siempre que el ancho maximo del elemento lo permita (sino pasa a la siguiente linea).</li>
<li>Los inline elements se colocan al costado del float siempre que formen parte del mismo BFC (no necesitan ser siblings grandparents, etc, se puede dar con cualquier jerarquia)</li>
</ul>
</li>
<li>
<p><strong>Cuaquiera de los dos</strong></p>
<ul>
<li><strong>Si tiene clear left o right</strong> El elemento no puede estar a continuacion de un float (dentro del mismo BFC)</li>
</ul>
</li>
</ul>
<h4 id="el-famoso-clearfix---wip">El famoso clearfix --WIP</h4>
<p><a href="https://www.youtube.com/watch?v=IiJzbXzOdHQ">https://www.youtube.com/watch?v=IiJzbXzOdHQ</a></p>
<p><a href="https://www.youtube.com/watch?v=F86kgfhS-Vk">https://www.youtube.com/watch?v=F86kgfhS-Vk</a></p>
<h2 id="rules">Rules</h2>
<h2 id="rules-1">@ Rules</h2>

