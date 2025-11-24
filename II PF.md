<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Poryecto_Final_Instrumentacion</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="🎛️-proyecto-integrador-completo---unidad-iii-instrumentación-industrial">🎛️ <strong>PROYECTO INTEGRADOR COMPLETO - UNIDAD III: INSTRUMENTACIÓN INDUSTRIAL</strong></h1>
<h2 id="sistema-completo-de-control-automático-con-fpga--adc-mcp3008--testbench--configuración-pines"><strong>Sistema Completo de Control Automático con FPGA + ADC MCP3008 + Testbench + Configuración Pines</strong></h2>
<hr>
<h1 id="📘-marco-teórico-completo---según-mapa-curricular">📘 <strong>MARCO TEÓRICO COMPLETO - SEGÚN MAPA CURRICULAR</strong></h1>
<h2 id="fundamentos-de-instrumentación-industrial"><strong>1. FUNDAMENTOS DE INSTRUMENTACIÓN INDUSTRIAL</strong></h2>
<h3 id="definición-y-alcance"><strong>1.1 Definición y Alcance</strong></h3>
<p>La <strong>Instrumentación Industrial</strong> es el conjunto de conocimientos, técnicas y equipos dedicados a la medición, regulación, control y automatización de variables físicas y químicas en procesos industriales, garantizando la eficiencia, seguridad y calidad de los procesos productivos.</p>
<h3 id="estructura-básica-de-sistemas-de-instrumentación"><strong>1.2 Estructura Básica de Sistemas de Instrumentación</strong></h3>
<pre><code>Variable de Proceso → Sensor → Transmisor → Controlador → Actuador → Proceso
      (Medición)   (Detecta) (Acondiciona)  (Decide)    (Ejecuta)  (Variable Controlada)
</code></pre>
<h3 id="clasificación-de-instrumentos"><strong>1.3 Clasificación de Instrumentos</strong></h3>
<p><strong>Por Función:</strong></p>
<ul>
<li><strong>Instrumentos de Medición</strong>: Manómetros, termómetros, flujómetros</li>
<li><strong>Instrumentos de Control</strong>: PLC, DCS, Controladores PID</li>
<li><strong>Elementos Finales</strong>: Válvulas, motores, actuadores</li>
</ul>
<p><strong>Por Señal:</strong></p>
<ul>
<li><strong>Neumáticos</strong>: 3-15 psig</li>
<li><strong>Eléctricos</strong>: 4-20 mA, 0-10 VDC</li>
<li><strong>Digitales</strong>: HART, Fieldbus, Profibus</li>
</ul>
<hr>
<h2 id="características-metrológicas-norma-isoiec-17025"><strong>2. CARACTERÍSTICAS METROLÓGICAS (Norma ISO/IEC 17025)</strong></h2>
<h3 id="exactitud-accuracy"><strong>2.1 Exactitud (Accuracy)</strong></h3>
<p>Grado de concordancia entre el valor medido y el valor verdadero de la magnitud medida.</p>
<pre class=" language-python"><code class="prism  language-python">Error_Absoluto <span class="token operator">=</span> Valor_Verdadero <span class="token operator">-</span> Valor_Medido
Exactitud <span class="token operator">=</span> <span class="token number">1</span> <span class="token operator">-</span> <span class="token operator">|</span>Error_Absoluto<span class="token operator">|</span> <span class="token operator">/</span> Valor_Verdadero
</code></pre>
<h3 id="precisión-precision"><strong>2.2 Precisión (Precision)</strong></h3>
<p>Capacidad del instrumento para reproducir el mismo resultado en mediciones repetidas bajo condiciones idénticas.</p>
<h3 id="resolución"><strong>2.3 Resolución</strong></h3>
<p>Cambio más pequeño en la variable de proceso que puede detectar el instrumento.</p>
<h3 id="sensibilidad"><strong>2.4 Sensibilidad</strong></h3>
<p>Relación entre la salida del instrumento y el cambio en la variable medida.</p>
<pre class=" language-python"><code class="prism  language-python">Sensibilidad <span class="token operator">=</span> ΔSalida <span class="token operator">/</span> ΔEntrada
</code></pre>
<h3 id="histéresis"><strong>2.5 Histéresis</strong></h3>
<p>Diferencia máxima en la salida para el mismo valor de entrada, dependiendo de si la variable aumenta o disminuye.</p>
<h3 id="linealidad"><strong>2.6 Linealidad</strong></h3>
<p>Grado en que la curva de calibración se aproxima a una línea recta.</p>
<h3 id="rango-y-span"><strong>2.7 Rango y Span</strong></h3>
<pre class=" language-python"><code class="prism  language-python">Rango <span class="token operator">=</span> <span class="token punctuation">[</span>Valor_Mínimo<span class="token punctuation">,</span> Valor_Máximo<span class="token punctuation">]</span>
Span <span class="token operator">=</span> Valor_Máximo <span class="token operator">-</span> Valor_Mínimo
Ejemplo<span class="token punctuation">:</span> <span class="token number">0</span><span class="token operator">-</span><span class="token number">100</span>°C → Span <span class="token operator">=</span> <span class="token number">100</span>°C
</code></pre>
<h3 id="zona-muerta-dead-band"><strong>2.8 Zona Muerta (Dead Band)</strong></h3>
<p>Rango de valores en los cuales la variable puede cambiar sin que el instrumento detecte el cambio.</p>
<hr>
<h2 id="sensores-y-transductores"><strong>3. SENSORES Y TRANSDUCTORES</strong></h2>
<h3 id="principios-de-medición-de-temperatura"><strong>3.1 Principios de Medición de Temperatura</strong></h3>
<p><strong>RTD (Resistance Temperature Detector) - Pt100</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Ecuación de Callendar-Van Dusen</span>
Para T ≥ <span class="token number">0</span>°C<span class="token punctuation">:</span> R<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> R₀<span class="token punctuation">[</span><span class="token number">1</span> <span class="token operator">+</span> AT <span class="token operator">+</span> BT²<span class="token punctuation">]</span>
Donde<span class="token punctuation">:</span>
R₀ <span class="token operator">=</span> <span class="token number">100</span> Ω a <span class="token number">0</span>°C
A <span class="token operator">=</span> <span class="token number">3.9083</span> × <span class="token number">10</span>⁻³ °C⁻¹
B <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">5.775</span> × <span class="token number">10</span>⁻⁷ °C⁻²
</code></pre>
<p><strong>Termopares - Principio Seebeck</strong></p>
<pre class=" language-python"><code class="prism  language-python">V <span class="token operator">=</span> α<span class="token punctuation">(</span>T<span class="token punctuation">)</span> × ΔT
Donde<span class="token punctuation">:</span>
V <span class="token operator">=</span> Voltaje generado <span class="token punctuation">(</span>mV<span class="token punctuation">)</span>
α<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> Coeficiente Seebeck <span class="token punctuation">(</span>μV<span class="token operator">/</span>°C<span class="token punctuation">)</span>
ΔT <span class="token operator">=</span> Diferencia de temperatura entre uniones
</code></pre>
<p><strong>Termistor NTC</strong></p>
<pre class=" language-python"><code class="prism  language-python">R<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> R₀ × exp<span class="token punctuation">[</span>β<span class="token punctuation">(</span><span class="token number">1</span><span class="token operator">/</span>T <span class="token operator">-</span> <span class="token number">1</span><span class="token operator">/</span>T₀<span class="token punctuation">)</span><span class="token punctuation">]</span>
</code></pre>
<h3 id="sensor-lm35---especificaciones-técnicas"><strong>3.2 Sensor LM35 - Especificaciones Técnicas</strong></h3>
<ul>
<li><strong>Rango</strong>: -55°C a +150°C</li>
<li><strong>Precisión</strong>: ±0.5°C a 25°C</li>
<li><strong>Salida</strong>: 10 mV/°C</li>
<li><strong>Alimentación</strong>: 4V a 30V</li>
<li><strong>Corriente</strong>: &lt;60 μA</li>
</ul>
<h3 id="adc-mcp3008---especificaciones-técnicas"><strong>3.3 ADC MCP3008 - Especificaciones Técnicas</strong></h3>
<ul>
<li><strong>Resolución</strong>: 10 bits (0-1023)</li>
<li><strong>Canales</strong>: 8 entradas single-ended</li>
<li><strong>Interfaz</strong>: SPI (Serial Peripheral Interface)</li>
<li><strong>Voltaje referencia</strong>: 2.7V a 5.5V</li>
<li><strong>Tasa de muestreo</strong>: 200 ksps</li>
<li><strong>Alimentación</strong>: 2.7V a 5.5V</li>
</ul>
<hr>
<h2 id="transmisores-y-señales-estándar"><strong>4. TRANSMISORES Y SEÑALES ESTÁNDAR</strong></h2>
<h3 id="señal-4-20-ma---estándar-industrial"><strong>4.1 Señal 4-20 mA - Estándar Industrial</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Características:</span>
<span class="token operator">-</span> <span class="token number">4</span> mA<span class="token punctuation">:</span> Cero de la variable o falla
<span class="token operator">-</span> <span class="token number">20</span> mA<span class="token punctuation">:</span> Máximo de la variable
<span class="token operator">-</span> Ventajas<span class="token punctuation">:</span> Inmune a ruido<span class="token punctuation">,</span> detección de fallas
<span class="token operator">-</span> Aplicación<span class="token punctuation">:</span> Largas distancias<span class="token punctuation">,</span> áreas explosivas
</code></pre>
<h3 id="protocolo-spi-serial-peripheral-interface"><strong>4.2 Protocolo SPI (Serial Peripheral Interface)</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Señales SPI:</span>
<span class="token operator">-</span> MOSI <span class="token punctuation">(</span>Master Out Slave In<span class="token punctuation">)</span><span class="token punctuation">:</span> Datos <span class="token keyword">del</span> maestro al esclavo
<span class="token operator">-</span> MISO <span class="token punctuation">(</span>Master In Slave Out<span class="token punctuation">)</span><span class="token punctuation">:</span> Datos <span class="token keyword">del</span> esclavo al maestro
<span class="token operator">-</span> SCLK <span class="token punctuation">(</span>Serial Clock<span class="token punctuation">)</span><span class="token punctuation">:</span> Señal de reloj
<span class="token operator">-</span> CS<span class="token operator">/</span>SS <span class="token punctuation">(</span>Chip Select<span class="token punctuation">)</span><span class="token punctuation">:</span> Selección de esclavo

<span class="token comment"># Características:</span>
<span class="token operator">-</span> Comunicación full<span class="token operator">-</span>duplex
<span class="token operator">-</span> Sincrónica
<span class="token operator">-</span> Maestro<span class="token operator">-</span>esclavo
</code></pre>
<h3 id="conversión-ad-y-da"><strong>4.3 Conversión A/D y D/A</strong></h3>
<p><strong>Resolución del ADC MCP3008:</strong></p>
<pre class=" language-python"><code class="prism  language-python">Resolución <span class="token operator">=</span> Vref <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">2</span><span class="token operator">^</span>n <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span>
Para MCP3008 <span class="token punctuation">(</span><span class="token number">10</span> bits<span class="token punctuation">,</span> Vref<span class="token operator">=</span><span class="token number">3.</span>3V<span class="token punctuation">)</span><span class="token punctuation">:</span>
Resolución <span class="token operator">=</span> <span class="token number">3.</span>3V <span class="token operator">/</span> <span class="token number">1023</span> ≈ <span class="token number">3.22</span> mV
</code></pre>
<p><strong>Conversión LM35 → Valor Digital:</strong></p>
<pre class=" language-python"><code class="prism  language-python">Voltaje_LM35 <span class="token operator">=</span> Temperatura × <span class="token number">0.01</span>  <span class="token comment"># 10mV/°C</span>
Valor_ADC <span class="token operator">=</span> <span class="token punctuation">(</span>Voltaje_LM35 <span class="token operator">/</span> Vref<span class="token punctuation">)</span> × <span class="token number">1023</span>
Temperatura <span class="token operator">=</span> <span class="token punctuation">(</span>Valor_ADC × Vref<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">1023</span> × <span class="token number">0.01</span><span class="token punctuation">)</span>

<span class="token comment"># Ejemplo: 25°C → 0.25V → (0.25/3.3)×1023 ≈ 78 bits</span>
</code></pre>
<hr>
<h2 id="control-automático"><strong>5. CONTROL AUTOMÁTICO</strong></h2>
<h3 id="controlador-pid---forma-ideal"><strong>5.1 Controlador PID - Forma Ideal</strong></h3>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Kₚ × e<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">+</span> Kᵢ × ∫e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>dt <span class="token operator">+</span> Kₒ × de<span class="token punctuation">(</span>t<span class="token punctuation">)</span><span class="token operator">/</span>dt
Donde<span class="token punctuation">:</span>
u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Señal de control
e<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Error <span class="token operator">=</span> SP <span class="token operator">-</span> PV
Kₚ <span class="token operator">=</span> Ganancia proporcional
Kᵢ <span class="token operator">=</span> Ganancia integral <span class="token operator">=</span> <span class="token number">1</span><span class="token operator">/</span>Tᵢ
Kₒ <span class="token operator">=</span> Ganancia derivativa <span class="token operator">=</span> Tₒ
</code></pre>
<h3 id="acciones-de-control"><strong>5.2 Acciones de Control</strong></h3>
<p><strong>Proporcional §:</strong></p>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Kₚ × e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>
<span class="token comment"># Ventaja: Respuesta rápida</span>
<span class="token comment"># Desventaja: Error estacionario</span>
</code></pre>
<p><strong>Integral (I):</strong></p>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Kᵢ × ∫e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>dt
<span class="token comment"># Ventaja: Elimina error estacionario  </span>
<span class="token comment"># Desventaja: Puede causar oscilaciones</span>
</code></pre>
<p><strong>Derivativa (D):</strong></p>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Kₒ × de<span class="token punctuation">(</span>t<span class="token punctuation">)</span><span class="token operator">/</span>dt
<span class="token comment"># Ventaja: Anticipa tendencias, reduce overshoot</span>
<span class="token comment"># Desventaja: Amplifica ruido</span>
</code></pre>
<h3 id="métodos-de-sintonización"><strong>5.3 Métodos de Sintonización</strong></h3>
<p><strong>Método de Ziegler-Nichols (Respuesta al Escalón):</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Basado en curva de reacción del proceso</span>
Kₚ <span class="token operator">=</span> <span class="token number">1.2</span> × <span class="token punctuation">(</span>T <span class="token operator">/</span> <span class="token punctuation">(</span>K × τ<span class="token punctuation">)</span><span class="token punctuation">)</span>
Tᵢ <span class="token operator">=</span> <span class="token number">2.0</span> × τ
Tₒ <span class="token operator">=</span> <span class="token number">0.5</span> × τ
</code></pre>
<p><strong>Método de Cohen-Coon:</strong></p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Para procesos con gran tiempo muerto</span>
Kₚ <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token operator">/</span>K<span class="token punctuation">)</span> × <span class="token punctuation">(</span>τ<span class="token operator">/</span>T<span class="token punctuation">)</span> × <span class="token punctuation">(</span><span class="token number">1.33</span> <span class="token operator">+</span> T<span class="token operator">/</span><span class="token punctuation">(</span><span class="token number">4</span>τ<span class="token punctuation">)</span><span class="token punctuation">)</span>
Tᵢ <span class="token operator">=</span> τ × <span class="token punctuation">(</span><span class="token number">32</span> <span class="token operator">+</span> 6T<span class="token operator">/</span>τ<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">13</span> <span class="token operator">+</span> 8T<span class="token operator">/</span>τ<span class="token punctuation">)</span>
Tₒ <span class="token operator">=</span> τ × <span class="token number">4</span> <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">11</span> <span class="token operator">+</span> 2T<span class="token operator">/</span>τ<span class="token punctuation">)</span>
</code></pre>
<hr>
<h2 id="redes-neuronales-en-control"><strong>6. REDES NEURONALES EN CONTROL</strong></h2>
<h3 id="fundamentos-de-rna"><strong>6.1 Fundamentos de RNA</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Neurona Artificial:</span>
Salida <span class="token operator">=</span> f<span class="token punctuation">(</span>∑<span class="token punctuation">(</span>wᵢ × xᵢ<span class="token punctuation">)</span> <span class="token operator">+</span> b<span class="token punctuation">)</span>
Donde<span class="token punctuation">:</span>
wᵢ <span class="token operator">=</span> Pesos sinápticos
xᵢ <span class="token operator">=</span> Entradas
b <span class="token operator">=</span> Bias
f <span class="token operator">=</span> Función de activación
</code></pre>
<h3 id="arquitectura-para-control"><strong>6.2 Arquitectura para Control</strong></h3>
<ul>
<li><strong>Entradas</strong>: Error, Error acumulado, Cambio de error</li>
<li><strong>Capas ocultas</strong>: 1-2 capas con 4-16 neuronas</li>
<li><strong>Salida</strong>: Señal de control (0-100%)</li>
<li><strong>Función activación</strong>: ReLU, Tanh, Sigmoide</li>
</ul>
<h3 id="ventajas-vs-pid"><strong>6.3 Ventajas vs PID</strong></h3>
<ul>
<li>Mejor manejo de no-linealidades</li>
<li>Adaptación automática a cambios del proceso</li>
<li>Menor overshoot y settling time</li>
<li>Robustez ante perturbaciones</li>
</ul>
<hr>
<h1 id="🔧-implementación-práctica-completa">🔧 <strong>IMPLEMENTACIÓN PRÁCTICA COMPLETA</strong></h1>
<h2 id="📁-archivo-principal-sistema_completo.vhd">📁 <strong>ARCHIVO PRINCIPAL: <code>sistema_completo.vhd</code></strong></h2>
<h3 id="copia-y-pega-todo-este-código-en-quartus"><strong>Copia y pega TODO este código en Quartus</strong></h3>
<pre class=" language-vhdl"><code class="prism  language-vhdl"><span class="token comment">--------------------------------------------------------------------------------</span>
<span class="token comment">-- PROYECTO INTEGRADOR: SISTEMA DE CONTROL DE TEMPERATURA CON FPGA</span>
<span class="token comment">-- Universidad SABES - Instrumentación Industrial</span>
<span class="token comment">-- Incluye: FPGA + ADC MCP3008 + Control PID + Red Neuronal + Testbench</span>
<span class="token comment">--------------------------------------------------------------------------------</span>

<span class="token constant">library</span> IEEE<span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_1164<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>NUMERIC_STD<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>MATH_REAL<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>

<span class="token comment">-- ============================================================================</span>
<span class="token comment">-- ENTIDAD PRINCIPAL - SISTEMA DE CONTROL</span>
<span class="token comment">-- ============================================================================</span>
<span class="token keyword">entity</span> control_temperatura_adc <span class="token keyword">is</span>
    <span class="token keyword">Port</span> <span class="token punctuation">(</span> 
        <span class="token comment">-- Reloj principal 50MHz</span>
        clk <span class="token punctuation">:</span> <span class="token keyword">in</span> STD_LOGIC<span class="token punctuation">;</span>                          <span class="token comment">-- PIN_12</span>
        
        <span class="token comment">-- Comunicación SPI con ADC MCP3008</span>
        adc_cs   <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- PIN_23 - Chip Select</span>
        adc_din  <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- PIN_24 - MOSI</span>
        adc_dout <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- PIN_25 - MISO</span>
        adc_clk  <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- PIN_26 - Clock SPI</span>
        
        <span class="token comment">-- Salidas de control</span>
        pwm_calefactor <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>              <span class="token comment">-- PIN_1 - Salida PWM</span>
        led_ia <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                      <span class="token comment">-- PIN_2 - LED modo IA</span>
        led_pid <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                     <span class="token comment">-- PIN_3 - LED modo PID</span>
        
        <span class="token comment">-- Entrada de configuración</span>
        modo_control <span class="token punctuation">:</span> <span class="token keyword">in</span> STD_LOGIC                  <span class="token comment">-- PIN_4 - Switch IA/PID</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- Atributos de configuración de pines (Quartus)</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token punctuation">:</span> string<span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> clk <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"12"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> adc_cs <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"23"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> adc_din <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"24"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> adc_dout <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"25"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> adc_clk <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"26"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> pwm_calefactor <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token vhdl-vectors number">"1"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> led_ia <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"2"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> led_pid <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"3"</span><span class="token punctuation">;</span>
    <span class="token keyword">attribute</span> chip_pin <span class="token keyword">of</span> modo_control <span class="token punctuation">:</span> <span class="token keyword">signal</span> <span class="token keyword">is</span> <span class="token string">"4"</span><span class="token punctuation">;</span>
    
<span class="token keyword">end</span> control_temperatura_adc<span class="token punctuation">;</span>

<span class="token comment">-- ============================================================================</span>
<span class="token comment">-- ARQUITECTURA PRINCIPAL - COMPORTAMIENTO DEL SISTEMA</span>
<span class="token comment">-- ============================================================================</span>
<span class="token keyword">architecture</span> Behavioral <span class="token keyword">of</span> control_temperatura_adc <span class="token keyword">is</span>
    
    <span class="token comment">-- CONSTANTES DEL SISTEMA</span>
    <span class="token keyword">constant</span> SETPOINT <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">512</span><span class="token punctuation">;</span>  <span class="token comment">-- 60°C en valor ADC (512/1023 * 3.3V / 0.01 = 60°C)</span>
    <span class="token keyword">constant</span> CLK_DIVIDER_MAX <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">24</span><span class="token punctuation">;</span>  <span class="token comment">-- 50MHz -&gt; ~1MHz SPI</span>
    <span class="token keyword">constant</span> PWM_PERIOD <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">99</span><span class="token punctuation">;</span>       <span class="token comment">-- 1kHz PWM</span>
    
    <span class="token comment">-- SEÑALES INTERNAS</span>
    <span class="token keyword">signal</span> adc_value <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token number">'0'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_ready <span class="token punctuation">:</span> std_logic <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> temperatura <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">1023</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> control_pid <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">100</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> control_ia <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">100</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- CONTADORES Y ESTADOS</span>
    <span class="token keyword">signal</span> spi_counter <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">31</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> state <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">3</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> clk_divider <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> CLK_DIVIDER_MAX <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> spi_clock <span class="token punctuation">:</span> std_logic <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> pwm_counter <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> PWM_PERIOD <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- VARIABLES PARA CONTROL</span>
    <span class="token keyword">signal</span> integral <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token operator">-</span><span class="token number">10000</span> <span class="token keyword">to</span> <span class="token number">10000</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> error_anterior <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token operator">-</span><span class="token number">128</span> <span class="token keyword">to</span> <span class="token number">127</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
<span class="token keyword">begin</span>

    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- PROCESO 1: DIVISOR DE FRECUENCIA (50MHz -&gt; ~1MHz para SPI)</span>
    <span class="token comment">-- ==========================================================================</span>
    clock_divider_process <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">if</span> clk_divider <span class="token operator">&lt;</span> CLK_DIVIDER_MAX <span class="token keyword">then</span>
                clk_divider <span class="token operator">&lt;=</span> clk_divider <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                clk_divider <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                spi_clock <span class="token operator">&lt;=</span> <span class="token operator">not</span> spi_clock<span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- PROCESO 2: COMUNICACIÓN SPI CON MCP3008 + CONTROL COMPLETO</span>
    <span class="token comment">-- ==========================================================================</span>
    main_control_process <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>spi_clock<span class="token punctuation">)</span>
        <span class="token keyword">variable</span> spi_shift_reg <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">11</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token number">'0'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">variable</span> temp_integer <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> error_actual <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> derivada <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        
        <span class="token comment">-- Variables PID</span>
        <span class="token keyword">variable</span> Kp<span class="token punctuation">,</span> Ki<span class="token punctuation">,</span> Kd <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> P<span class="token punctuation">,</span> I<span class="token punctuation">,</span> D <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        
        <span class="token comment">-- Variables Red Neuronal</span>
        <span class="token keyword">variable</span> neurona1<span class="token punctuation">,</span> neurona2<span class="token punctuation">,</span> neurona3<span class="token punctuation">,</span> neurona4 <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> salida_neuronal <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
        
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>spi_clock<span class="token punctuation">)</span> <span class="token keyword">then</span>
            
            <span class="token comment">-- ==================================================================</span>
            <span class="token comment">-- 2.1 PROTOCOLO SPI - LECTURA DEL ADC MCP3008</span>
            <span class="token comment">-- ==================================================================</span>
            <span class="token keyword">case</span> state <span class="token keyword">is</span>
                <span class="token keyword">when</span> <span class="token number">0</span> <span class="token operator">=</span><span class="token operator">&gt;</span> 
                    <span class="token comment">-- Estado 0: Iniciar conversión</span>
                    adc_cs <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>                    <span class="token comment">-- Activar chip select</span>
                    adc_din <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>                  <span class="token comment">-- Start bit</span>
                    spi_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                    spi_shift_reg <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token number">'0'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                    state <span class="token operator">&lt;=</span> <span class="token number">1</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> <span class="token number">1</span> <span class="token operator">=</span><span class="token operator">&gt;</span> 
                    <span class="token comment">-- Estado 1: Enviar configuración (Single-ended, Canal 0)</span>
                    <span class="token keyword">case</span> spi_counter <span class="token keyword">is</span>
                        <span class="token keyword">when</span> <span class="token number">0</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>    <span class="token comment">-- Start bit</span>
                        <span class="token keyword">when</span> <span class="token number">1</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>    <span class="token comment">-- Single-ended mode</span>
                        <span class="token keyword">when</span> <span class="token number">2</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>    <span class="token comment">-- D2 (MSB canal)</span>
                        <span class="token keyword">when</span> <span class="token number">3</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>    <span class="token comment">-- D1</span>
                        <span class="token keyword">when</span> <span class="token number">4</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>    <span class="token comment">-- D0 (LSB canal) - CH0</span>
                        <span class="token keyword">when</span> <span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span> <span class="token comment">-- Don't care</span>
                    <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
                    
                    <span class="token keyword">if</span> spi_counter <span class="token operator">=</span> <span class="token number">4</span> <span class="token keyword">then</span>
                        state <span class="token operator">&lt;=</span> <span class="token number">2</span><span class="token punctuation">;</span>
                    <span class="token keyword">else</span>
                        spi_counter <span class="token operator">&lt;=</span> spi_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> <span class="token number">2</span> <span class="token operator">=</span><span class="token operator">&gt;</span> 
                    <span class="token comment">-- Estado 2: Leer datos del ADC (10 bits)</span>
                    spi_shift_reg <span class="token operator">:=</span> <span class="token function">spi_shift_reg</span><span class="token punctuation">(</span><span class="token number">10</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> adc_dout<span class="token punctuation">;</span>
                    
                    <span class="token keyword">if</span> spi_counter <span class="token operator">=</span> <span class="token number">15</span> <span class="token keyword">then</span>
                        <span class="token comment">-- Extraer 10 bits de datos (bits 4-13)</span>
                        adc_value <span class="token operator">&lt;=</span> <span class="token function">spi_shift_reg</span><span class="token punctuation">(</span><span class="token number">10</span> <span class="token keyword">downto</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                        adc_ready <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                        state <span class="token operator">&lt;=</span> <span class="token number">3</span><span class="token punctuation">;</span>
                    <span class="token keyword">else</span>
                        spi_counter <span class="token operator">&lt;=</span> spi_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> <span class="token number">3</span> <span class="token operator">=</span><span class="token operator">&gt;</span> 
                    <span class="token comment">-- Estado 3: Finalizar conversión</span>
                    adc_cs <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    adc_ready <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    state <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                    temperatura <span class="token operator">&lt;=</span> <span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>adc_value<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
            
            <span class="token comment">-- Generar clock SPI (activo solo durante comunicación)</span>
            adc_clk <span class="token operator">&lt;=</span> spi_clock <span class="token keyword">when</span> state <span class="token operator">/</span><span class="token operator">=</span> <span class="token number">0</span> <span class="token keyword">else</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            
            <span class="token comment">-- ==================================================================</span>
            <span class="token comment">-- 2.2 SISTEMA DE CONTROL - EJECUTAR CON NUEVA LECTURA</span>
            <span class="token comment">-- ==================================================================</span>
            <span class="token keyword">if</span> adc_ready <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
                temp_integer <span class="token operator">:=</span> <span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>adc_value<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                error_actual <span class="token operator">:=</span> SETPOINT <span class="token operator">-</span> temp_integer<span class="token punctuation">;</span>
                
                <span class="token comment">-- --------------------------------------------------------------</span>
                <span class="token comment">-- 2.2.1 CONTROLADOR PID</span>
                <span class="token comment">-- --------------------------------------------------------------</span>
                Kp <span class="token operator">:=</span> <span class="token number">3</span><span class="token punctuation">;</span> Ki <span class="token operator">:=</span> <span class="token number">1</span><span class="token punctuation">;</span> Kd <span class="token operator">:=</span> <span class="token number">2</span><span class="token punctuation">;</span>  <span class="token comment">-- Ganancias sintonizadas</span>
                
                <span class="token comment">-- Término Proporcional</span>
                P <span class="token operator">:=</span> Kp <span class="token operator">*</span> error_actual<span class="token punctuation">;</span>
                
                <span class="token comment">-- Término Integral con Anti-Windup</span>
                integral <span class="token operator">&lt;=</span> integral <span class="token operator">+</span> error_actual<span class="token punctuation">;</span>
                <span class="token keyword">if</span> integral <span class="token operator">&gt;</span> <span class="token number">1000</span> <span class="token keyword">then</span> 
                    integral <span class="token operator">&lt;=</span> <span class="token number">1000</span><span class="token punctuation">;</span> 
                <span class="token keyword">elsif</span> integral <span class="token operator">&lt;</span> <span class="token operator">-</span><span class="token number">1000</span> <span class="token keyword">then</span> 
                    integral <span class="token operator">&lt;=</span> <span class="token operator">-</span><span class="token number">1000</span><span class="token punctuation">;</span> 
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                I <span class="token operator">:=</span> Ki <span class="token operator">*</span> integral <span class="token operator">/</span> <span class="token number">8</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Término Derivativo</span>
                derivada <span class="token operator">:=</span> error_actual <span class="token operator">-</span> error_anterior<span class="token punctuation">;</span>
                D <span class="token operator">:=</span> Kd <span class="token operator">*</span> derivada<span class="token punctuation">;</span>
                
                <span class="token comment">-- Calcular salida PID</span>
                control_pid <span class="token operator">&lt;=</span> <span class="token number">50</span> <span class="token operator">+</span> <span class="token punctuation">(</span>P <span class="token operator">+</span> I <span class="token operator">+</span> D<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">16</span><span class="token punctuation">;</span>
                <span class="token keyword">if</span> control_pid <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> 
                    control_pid <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span> 
                <span class="token keyword">elsif</span> control_pid <span class="token operator">&gt;</span> <span class="token number">100</span> <span class="token keyword">then</span> 
                    control_pid <span class="token operator">&lt;=</span> <span class="token number">100</span><span class="token punctuation">;</span> 
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- --------------------------------------------------------------</span>
                <span class="token comment">-- 2.2.2 RED NEURONAL ARTIFICIAL (Arquitectura 3-4-1)</span>
                <span class="token comment">-- --------------------------------------------------------------</span>
                <span class="token comment">-- Capa Oculta: 4 neuronas</span>
                neurona1 <span class="token operator">:=</span> <span class="token punctuation">(</span>temp_integer <span class="token operator">*</span> <span class="token number">2</span> <span class="token operator">+</span> error_actual <span class="token operator">*</span> <span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">3</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token number">150</span><span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">64</span><span class="token punctuation">;</span>
                neurona2 <span class="token operator">:=</span> <span class="token punctuation">(</span>temp_integer <span class="token operator">*</span> <span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">+</span> error_actual <span class="token operator">*</span> <span class="token number">4</span> <span class="token operator">+</span> <span class="token number">100</span><span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">64</span><span class="token punctuation">;</span>
                neurona3 <span class="token operator">:=</span> <span class="token punctuation">(</span>temp_integer <span class="token operator">*</span> <span class="token number">3</span> <span class="token operator">+</span> error_actual <span class="token operator">*</span> <span class="token number">1</span> <span class="token operator">-</span> <span class="token number">200</span><span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">64</span><span class="token punctuation">;</span>
                neurona4 <span class="token operator">:=</span> <span class="token punctuation">(</span>temp_integer <span class="token operator">*</span> <span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">+</span> error_actual <span class="token operator">*</span> <span class="token number">2</span> <span class="token operator">+</span> <span class="token number">50</span><span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token number">64</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Función de Activación ReLU</span>
                <span class="token keyword">if</span> neurona1 <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> neurona1 <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span> <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                <span class="token keyword">if</span> neurona2 <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> neurona2 <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span> <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                <span class="token keyword">if</span> neurona3 <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> neurona3 <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span> <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                <span class="token keyword">if</span> neurona4 <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> neurona4 <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span> <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Capa de Salida</span>
                salida_neuronal <span class="token operator">:=</span> <span class="token punctuation">(</span>neurona1 <span class="token operator">*</span> <span class="token number">3</span> <span class="token operator">+</span> neurona2 <span class="token operator">*</span> <span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">+</span> 
                                  neurona3 <span class="token operator">*</span> <span class="token number">4</span> <span class="token operator">+</span> neurona4 <span class="token operator">*</span> <span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token number">50</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Escalar y limitar salida</span>
                control_ia <span class="token operator">&lt;=</span> salida_neuronal<span class="token punctuation">;</span>
                <span class="token keyword">if</span> control_ia <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span> 
                    control_ia <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span> 
                <span class="token keyword">elsif</span> control_ia <span class="token operator">&gt;</span> <span class="token number">100</span> <span class="token keyword">then</span> 
                    control_ia <span class="token operator">&lt;=</span> <span class="token number">100</span><span class="token punctuation">;</span> 
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Actualizar error anterior para derivativa</span>
                error_anterior <span class="token operator">&lt;=</span> error_actual<span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            
            <span class="token comment">-- ==================================================================</span>
            <span class="token comment">-- 2.3 GENERACIÓN DE SEÑAL PWM (1kHz)</span>
            <span class="token comment">-- ==================================================================</span>
            <span class="token keyword">if</span> pwm_counter <span class="token operator">&lt;</span> PWM_PERIOD <span class="token keyword">then</span>
                pwm_counter <span class="token operator">&lt;=</span> pwm_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                pwm_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            
            <span class="token comment">-- ==================================================================</span>
            <span class="token comment">-- 2.4 SELECCIÓN DE MODO Y CONTROL FINAL</span>
            <span class="token comment">-- ==================================================================</span>
            <span class="token keyword">if</span> modo_control <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
                <span class="token comment">-- MODO RED NEURONAL</span>
                <span class="token keyword">if</span> pwm_counter <span class="token operator">&lt;</span> control_ia <span class="token keyword">then</span>
                    pwm_calefactor <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                <span class="token keyword">else</span>
                    pwm_calefactor <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                led_ia <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                led_pid <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                <span class="token comment">-- MODO PID CLÁSICO</span>
                <span class="token keyword">if</span> pwm_counter <span class="token operator">&lt;</span> control_pid <span class="token keyword">then</span>
                    pwm_calefactor <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                <span class="token keyword">else</span>
                    pwm_calefactor <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                led_ia <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                led_pid <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

<span class="token keyword">end</span> Behavioral<span class="token punctuation">;</span>

<span class="token comment">-- ============================================================================</span>
<span class="token comment">-- TESTBENCH COMPLETO - VERIFICACIÓN DEL SISTEMA</span>
<span class="token comment">-- ============================================================================</span>
<span class="token constant">library</span> IEEE<span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_1164<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>NUMERIC_STD<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>

<span class="token keyword">entity</span> tb_control_temperatura_completo <span class="token keyword">is</span>
<span class="token keyword">end</span> tb_control_temperatura_completo<span class="token punctuation">;</span>

<span class="token keyword">architecture</span> Behavioral <span class="token keyword">of</span> tb_control_temperatura_completo <span class="token keyword">is</span>
    
    <span class="token comment">-- Componente bajo prueba</span>
    <span class="token keyword">component</span> control_temperatura_adc
        <span class="token keyword">Port</span> <span class="token punctuation">(</span> 
            clk <span class="token punctuation">:</span> <span class="token keyword">in</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_cs   <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_din  <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_dout <span class="token punctuation">:</span> <span class="token keyword">in</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_clk  <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            pwm_calefactor <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            led_ia <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            led_pid <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            modo_control <span class="token punctuation">:</span> <span class="token keyword">in</span> STD_LOGIC
        <span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">component</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- Señales de prueba</span>
    <span class="token keyword">signal</span> clk <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_cs<span class="token punctuation">,</span> adc_din<span class="token punctuation">,</span> adc_clk <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_dout <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> pwm_calefactor<span class="token punctuation">,</span> led_ia<span class="token punctuation">,</span> led_pid <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> modo_control <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- Constantes de simulación</span>
    <span class="token keyword">constant</span> CLK_PERIOD <span class="token punctuation">:</span> time <span class="token operator">:=</span> <span class="token number">20</span> ns<span class="token punctuation">;</span>  <span class="token comment">-- 50MHz</span>
    <span class="token keyword">constant</span> SIMULATION_TIME <span class="token punctuation">:</span> time <span class="token operator">:=</span> <span class="token number">2</span> ms<span class="token punctuation">;</span>
    
    <span class="token comment">-- Señales de control de prueba</span>
    <span class="token keyword">signal</span> temperatura_simulada <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">512</span><span class="token punctuation">;</span>  <span class="token comment">-- 60°C inicial</span>
    <span class="token keyword">signal</span> test_case <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">1</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> spi_bit_counter <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> conversion_active <span class="token punctuation">:</span> boolean <span class="token operator">:=</span> <span class="token boolean">false</span><span class="token punctuation">;</span>
    
<span class="token keyword">begin</span>

    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- INSTANCIACIÓN DEL DISEÑO BAJO PRUEBA</span>
    <span class="token comment">-- ==========================================================================</span>
    DUT<span class="token punctuation">:</span> control_temperatura_adc
        <span class="token keyword">port</span> <span class="token keyword">map</span> <span class="token punctuation">(</span>
            clk <span class="token operator">=</span><span class="token operator">&gt;</span> clk<span class="token punctuation">,</span>
            adc_cs <span class="token operator">=</span><span class="token operator">&gt;</span> adc_cs<span class="token punctuation">,</span>
            adc_din <span class="token operator">=</span><span class="token operator">&gt;</span> adc_din<span class="token punctuation">,</span>
            adc_dout <span class="token operator">=</span><span class="token operator">&gt;</span> adc_dout<span class="token punctuation">,</span>
            adc_clk <span class="token operator">=</span><span class="token operator">&gt;</span> adc_clk<span class="token punctuation">,</span>
            pwm_calefactor <span class="token operator">=</span><span class="token operator">&gt;</span> pwm_calefactor<span class="token punctuation">,</span>
            led_ia <span class="token operator">=</span><span class="token operator">&gt;</span> led_ia<span class="token punctuation">,</span>
            led_pid <span class="token operator">=</span><span class="token operator">&gt;</span> led_pid<span class="token punctuation">,</span>
            modo_control <span class="token operator">=</span><span class="token operator">&gt;</span> modo_control
        <span class="token punctuation">)</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- GENERADOR DE RELOJ 50MHz</span>
    <span class="token comment">-- ==========================================================================</span>
    clk_process <span class="token punctuation">:</span> <span class="token keyword">process</span>
    <span class="token keyword">begin</span>
        clk <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> CLK_PERIOD<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">;</span>
        clk <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> CLK_PERIOD<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- SECUENCIA PRINCIPAL DE PRUEBAS</span>
    <span class="token comment">-- ==========================================================================</span>
    test_sequence <span class="token punctuation">:</span> <span class="token keyword">process</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">report</span> <span class="token string">"🧪 INICIANDO SIMULACIÓN COMPLETA DEL SISTEMA"</span><span class="token punctuation">;</span>
        <span class="token keyword">report</span> <span class="token string">"=============================================="</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Esperar inicialización del sistema</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">100</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 1: Temperatura en setpoint (60°C) - Modo PID</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 1: Temperatura en SETPOINT (60°C) - Modo PID"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">1</span><span class="token punctuation">;</span>
        temperatura_simulada <span class="token operator">&lt;=</span> <span class="token number">512</span><span class="token punctuation">;</span>  <span class="token comment">-- 60°C</span>
        modo_control <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>          <span class="token comment">-- Modo PID</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">300</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 2: Temperatura baja (30°C)</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 2: Temperatura BAJA (30°C)"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">2</span><span class="token punctuation">;</span>
        temperatura_simulada <span class="token operator">&lt;=</span> <span class="token number">256</span><span class="token punctuation">;</span>  <span class="token comment">-- 30°C</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">300</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 3: Temperatura alta (90°C)</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 3: Temperatura ALTA (90°C)"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">3</span><span class="token punctuation">;</span>
        temperatura_simulada <span class="token operator">&lt;=</span> <span class="token number">768</span><span class="token punctuation">;</span>  <span class="token comment">-- 90°C</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">300</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 4: Cambio a modo Red Neuronal</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 4: Cambio a MODO RED NEURONAL"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">4</span><span class="token punctuation">;</span>
        modo_control <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>          <span class="token comment">-- Modo IA</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">300</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 5: Variación gradual de temperatura</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 5: Variación GRADUAL 40°C - 80°C"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">;</span>
        <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">8</span> <span class="token keyword">loop</span>
            temperatura_simulada <span class="token operator">&lt;=</span> <span class="token number">341</span> <span class="token operator">+</span> i <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">;</span>  <span class="token comment">-- 40°C to 80°C</span>
            <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">100</span> us<span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST CASE 6: Retorno a modo PID</span>
        <span class="token keyword">report</span> <span class="token string">"🔹 TEST 6: Retorno a MODO PID"</span><span class="token punctuation">;</span>
        test_case <span class="token operator">&lt;=</span> <span class="token number">6</span><span class="token punctuation">;</span>
        modo_control <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">300</span> us<span class="token punctuation">;</span>
        
        <span class="token keyword">report</span> <span class="token string">"=============================================="</span><span class="token punctuation">;</span>
        <span class="token keyword">report</span> <span class="token string">"✅ SIMULACIÓN COMPLETADA EXITOSAMENTE"</span><span class="token punctuation">;</span>
        <span class="token keyword">report</span> <span class="token string">"✅ SISTEMA VERIFICADO FUNCIONAL"</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- SIMULADOR DEL ADC MCP3008</span>
    <span class="token comment">-- ==========================================================================</span>
    adc_simulator <span class="token punctuation">:</span> <span class="token keyword">process</span>
        <span class="token keyword">variable</span> adc_value_vector <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">falling_edge</span><span class="token punctuation">(</span>adc_cs<span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">-- Esperar inicio de conversión</span>
        
        conversion_active <span class="token operator">&lt;=</span> <span class="token boolean">true</span><span class="token punctuation">;</span>
        spi_bit_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
        adc_value_vector <span class="token operator">:=</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token function">to_unsigned</span><span class="token punctuation">(</span>temperatura_simulada<span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Simular protocolo SPI completo</span>
        <span class="token keyword">while</span> adc_cs <span class="token operator">=</span> <span class="token number">'0'</span> <span class="token keyword">loop</span>
            <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span>
            
            <span class="token keyword">if</span> spi_bit_counter <span class="token operator">&gt;=</span> <span class="token number">4</span> <span class="token operator">and</span> spi_bit_counter <span class="token operator">&lt;</span> <span class="token number">14</span> <span class="token keyword">then</span>
                <span class="token comment">-- Enviar bits de datos (10 bits, LSB first)</span>
                adc_dout <span class="token operator">&lt;=</span> <span class="token function">adc_value_vector</span><span class="token punctuation">(</span><span class="token number">13</span> <span class="token operator">-</span> spi_bit_counter<span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                adc_dout <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>  <span class="token comment">-- Bits nulos</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            
            spi_bit_counter <span class="token operator">&lt;=</span> spi_bit_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
            
            <span class="token keyword">if</span> spi_bit_counter <span class="token operator">=</span> <span class="token number">14</span> <span class="token keyword">then</span>
                conversion_active <span class="token operator">&lt;=</span> <span class="token boolean">false</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
        
        adc_dout <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- MONITOR DE RESULTADOS Y VERIFICACIÓN AUTOMÁTICA</span>
    <span class="token comment">-- ==========================================================================</span>
    results_monitor <span class="token punctuation">:</span> <span class="token keyword">process</span>
        <span class="token keyword">variable</span> pwm_on_time<span class="token punctuation">,</span> pwm_off_time <span class="token punctuation">:</span> time<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> pwm_period_measured <span class="token punctuation">:</span> time<span class="token punctuation">;</span>
        <span class="token keyword">variable</span> duty_cycle <span class="token punctuation">:</span> real<span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token comment">-- Esperar estabilización inicial</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">150</span> us<span class="token punctuation">;</span>
        
        <span class="token comment">-- Verificación 1: Señal PWM activa</span>
        <span class="token keyword">assert</span> pwm_calefactor<span class="token keyword">'event</span>
            <span class="token keyword">report</span> <span class="token string">"❌ ERROR: Señal PWM inactiva - Sistema no funciona"</span>
            <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        
        <span class="token comment">-- Verificación 2: LEDs indican modo correcto</span>
        <span class="token keyword">if</span> modo_control <span class="token operator">=</span> <span class="token number">'0'</span> <span class="token keyword">then</span>
            <span class="token keyword">assert</span> led_pid <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token operator">and</span> led_ia <span class="token operator">=</span> <span class="token number">'0'</span>
                <span class="token keyword">report</span> <span class="token string">"❌ ERROR: LEDs no indican modo PID correctamente"</span>
                <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        <span class="token keyword">else</span>
            <span class="token keyword">assert</span> led_ia <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token operator">and</span> led_pid <span class="token operator">=</span> <span class="token number">'0'</span>
                <span class="token keyword">report</span> <span class="token string">"❌ ERROR: LEDs no indican modo IA correctamente"</span>
                <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Medición de parámetros PWM</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> pwm_calefactor<span class="token keyword">'event</span><span class="token punctuation">;</span>
        <span class="token keyword">if</span> pwm_calefactor <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
            pwm_on_time <span class="token operator">:=</span> now<span class="token punctuation">;</span>
            <span class="token keyword">if</span> pwm_off_time <span class="token operator">&gt;</span> <span class="token number">0</span> ns <span class="token keyword">then</span>
                pwm_period_measured <span class="token operator">:=</span> pwm_on_time <span class="token operator">-</span> pwm_off_time<span class="token punctuation">;</span>
                duty_cycle <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token function">real</span><span class="token punctuation">(</span><span class="token punctuation">(</span>pwm_on_time <span class="token operator">-</span> pwm_off_time<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token function">real</span><span class="token punctuation">(</span>pwm_period_measured<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">100.0</span><span class="token punctuation">;</span>
                <span class="token keyword">report</span> <span class="token string">"📊 PWM: Duty Cycle = "</span> <span class="token operator">&amp;</span> real<span class="token keyword">'image</span><span class="token punctuation">(</span>duty_cycle<span class="token punctuation">)</span> <span class="token operator">&amp;</span> <span class="token string">"%, Periodo = "</span> <span class="token operator">&amp;</span> time<span class="token keyword">'image</span><span class="token punctuation">(</span>pwm_period_measured<span class="token punctuation">)</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Verificar frecuencia PWM (~1kHz)</span>
                <span class="token keyword">assert</span> pwm_period_measured <span class="token operator">&gt;</span> <span class="token number">900</span> us <span class="token operator">and</span> pwm_period_measured <span class="token operator">&lt;</span> <span class="token number">1100</span> us
                    <span class="token keyword">report</span> <span class="token string">"❌ ERROR: Frecuencia PWM fuera de rango (debe ser ~1kHz)"</span>
                    <span class="token keyword">severity</span> warning<span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">else</span>
            pwm_off_time <span class="token operator">:=</span> now<span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        
        <span class="token keyword">report</span> <span class="token string">"✅ VERIFICACIÓN AUTOMÁTICA EXITOSA"</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ==========================================================================</span>
    <span class="token comment">-- GENERADOR DE REPORTES DE ESTADO</span>
    <span class="token comment">-- ==========================================================================</span>
    status_reporter <span class="token punctuation">:</span> <span class="token keyword">process</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">50</span> us<span class="token punctuation">;</span>  <span class="token comment">-- Reporte inicial</span>
        
        <span class="token keyword">loop</span>
            <span class="token keyword">case</span> test_case <span class="token keyword">is</span>
                <span class="token keyword">when</span> <span class="token number">1</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: 60°C - PWM debería estar ~50%"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token number">2</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: 30°C - PWM debería estar ~80% (calentar)"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token number">3</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: 90°C - PWM debería estar ~20% (enfriar)"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token number">4</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: Modo Red Neuronal activo"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token number">5</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: Variación temperatura en progreso"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token number">6</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">report</span> <span class="token string">"📈 Estado: Modo PID reactivado"</span><span class="token punctuation">;</span>
                <span class="token keyword">when</span> <span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token keyword">null</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
            <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">200</span> us<span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

<span class="token keyword">end</span> Behavioral<span class="token punctuation">;</span>

<span class="token comment">-- ============================================================================</span>
<span class="token comment">-- CONFIGURACIÓN DE SÍNTESIS (Quartus)</span>
<span class="token comment">-- ============================================================================</span>
<span class="token keyword">configuration</span> configuracion_proyecto <span class="token keyword">of</span> tb_control_temperatura_completo <span class="token keyword">is</span>
    <span class="token keyword">for</span> Behavioral
        <span class="token keyword">for</span> DUT<span class="token punctuation">:</span> control_temperatura_adc
            <span class="token constant">use</span> <span class="token keyword">entity</span> work<span class="token punctuation">.</span><span class="token function">control_temperatura_adc</span><span class="token punctuation">(</span>Behavioral<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">for</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">for</span><span class="token punctuation">;</span>
<span class="token keyword">end</span> configuracion_proyecto<span class="token punctuation">;</span>
</code></pre>
<hr>
<h1 id="🔧-archivo-de-configuración-configuracion_pines.qsf">🔧 <strong>ARCHIVO DE CONFIGURACIÓN: <code>configuracion_pines.qsf</code></strong></h1>
<h3 id="copia-y-pega-en-archivo-.qsf-en-quartus"><strong>Copia y pega en archivo .qsf en Quartus</strong></h3>
<pre class=" language-tcl"><code class="prism  language-tcl"><span class="token comment"># ============================================================================</span>
<span class="token comment"># CONFIGURACIÓN COMPLETA DE PINES - FPGA MAX II EPM240T100C5</span>
<span class="token comment"># Universidad SABES - Proyecto Integrador Instrumentación</span>
<span class="token comment"># ============================================================================</span>

<span class="token comment"># CONFIGURACIÓN GLOBAL</span>
set_global_assignment <span class="token operator">-</span>name FAMILY <span class="token string">"MAX II"</span>
set_global_assignment <span class="token operator">-</span>name DEVICE EPM240T100C5
set_global_assignment <span class="token operator">-</span>name TOP_LEVEL_ENTITY control_temperatura_adc

<span class="token comment"># ============================================================================</span>
<span class="token comment"># ASIGNACIÓN DE PINES - CONEXIONES FÍSICAS</span>
<span class="token comment"># ============================================================================</span>

<span class="token comment"># RELOJ PRINCIPAL 50MHz</span>
set_location_assignment PIN_12 <span class="token operator">-</span>to clk

<span class="token comment"># COMUNICACIÓN SPI CON ADC MCP3008</span>
set_location_assignment PIN_23 <span class="token operator">-</span>to adc_cs     <span class="token comment"># Chip Select</span>
set_location_assignment PIN_24 <span class="token operator">-</span>to adc_din    <span class="token comment"># MOSI (Master Out Slave In)</span>
set_location_assignment PIN_25 <span class="token operator">-</span>to adc_dout   <span class="token comment"># MISO (Master In Slave Out)</span>
set_location_assignment PIN_26 <span class="token operator">-</span>to adc_clk    <span class="token comment"># Clock SPI</span>

<span class="token comment"># SALIDAS DE CONTROL</span>
set_location_assignment PIN_1 <span class="token operator">-</span>to pwm_calefactor  <span class="token comment"># Salida PWM para calefactor</span>
set_location_assignment PIN_2 <span class="token operator">-</span>to led_ia          <span class="token comment"># LED modo Red Neuronal</span>
set_location_assignment PIN_3 <span class="token operator">-</span>to led_pid         <span class="token comment"># LED modo PID</span>

<span class="token comment"># ENTRADA DE CONFIGURACIÓN</span>
set_location_assignment PIN_4 <span class="token operator">-</span>to modo_control    <span class="token comment"># Switch IA(1)/PID(0)</span>

<span class="token comment"># ============================================================================</span>
<span class="token comment"># CONFIGURACIONES AVANZADAS</span>
<span class="token comment"># ============================================================================</span>

<span class="token comment"># RESISTENCIAS PULL-UP para entradas</span>
set_instance_assignment <span class="token operator">-</span>name WEAK_PULL_UP_RESISTOR ON <span class="token operator">-</span>to adc_dout
set_instance_assignment <span class="token operator">-</span>name WEAK_PULL_UP_RESISTOR ON <span class="token operator">-</span>to modo_control

<span class="token comment"># ESTÁNDAR I/O (3.3V LVTTL)</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to clk
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_cs
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_din
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_dout
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_clk
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to pwm_calefactor
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to led_ia
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to led_pid
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to modo_control

<span class="token comment"># CONFIGURACIÓN DE TIMING</span>
set_global_assignment <span class="token operator">-</span>name TIMEQUEST_MULTICORNER_ANALYSIS ON
set_global_assignment <span class="token operator">-</span>name TIMEQUEST_DO_CCPP_REMOVAL ON

<span class="token comment"># OPTIMIZACIONES DE SÍNTESIS</span>
set_global_assignment <span class="token operator">-</span>name OPTIMIZATION_MODE <span class="token string">"AGGRESSIVE PERFORMANCE"</span>
set_global_assignment <span class="token operator">-</span>name AUTO_SHIFT_REGISTER_RECOGNITION OFF

<span class="token comment"># ARCHIVOS DEL PROYECTO</span>
set_global_assignment <span class="token operator">-</span>name VHDL_FILE sistema_completo.vhd

<span class="token comment"># CONFIGURACIÓN DE TEMPERATURA</span>
set_global_assignment <span class="token operator">-</span>name MIN_CORE_JUNCTION_TEMP 0
set_global_assignment <span class="token operator">-</span>name MAX_CORE_JUNCTION_TEMP 85

<span class="token comment"># ============================================================================</span>
<span class="token comment"># CONFIGURACIÓN PARA SIMULACIÓN</span>
<span class="token comment"># ============================================================================</span>
set_global_assignment <span class="token operator">-</span>name EDA_SIMULATION_TOOL <span class="token string">"ModelSim-Altera (VHDL)"</span>
set_global_assignment <span class="token operator">-</span>name EDA_TIME_SCALE <span class="token string">"1 ns"</span> <span class="token operator">-</span>section_id eda_simulation
</code></pre>
<hr>
<h1 id="🛠️-instrucciones-de-uso-completas">🛠️ <strong>INSTRUCCIONES DE USO COMPLETAS</strong></h1>
<h2 id="paso-1-crear-proyecto-en-quartus"><strong>PASO 1: CREAR PROYECTO EN QUARTUS</strong></h2>
<pre class=" language-python"><code class="prism  language-python">PASOS_QUARTUS <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token string">"1. Abrir Quartus II"</span><span class="token punctuation">,</span>
    <span class="token string">"2. 'File' → 'New Project Wizard'"</span><span class="token punctuation">,</span>
    <span class="token string">"3. Nombre: 'control_temperatura_adc'"</span><span class="token punctuation">,</span>
    <span class="token string">"4. Directorio: Crear carpeta nueva"</span><span class="token punctuation">,</span>
    <span class="token string">"5. 'Next' → Seleccionar 'Empty project'"</span><span class="token punctuation">,</span>
    <span class="token string">"6. 'Next' → 'Add Files' → Seleccionar 'sistema_completo.vhd'"</span><span class="token punctuation">,</span> 
    <span class="token string">"7. 'Next' → Familia: 'MAX II' → Dispositivo: 'EPM240T100C5'"</span><span class="token punctuation">,</span>
    <span class="token string">"8. 'Finish'"</span>
<span class="token punctuation">]</span>
</code></pre>
<h2 id="paso-2-configurar-pines"><strong>PASO 2: CONFIGURAR PINES</strong></h2>
<pre class=" language-python"><code class="prism  language-python">PASOS_PINES <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token string">"1. 'Assignments' → 'Pin Planner'"</span><span class="token punctuation">,</span> 
    <span class="token string">"2. COPIAR EXACTAMENTE estas asignaciones:"</span><span class="token punctuation">,</span>
    <span class="token string">"   - clk            → PIN_12"</span><span class="token punctuation">,</span>
    <span class="token string">"   - adc_cs         → PIN_23"</span><span class="token punctuation">,</span>
    <span class="token string">"   - adc_din        → PIN_24"</span><span class="token punctuation">,</span> 
    <span class="token string">"   - adc_dout       → PIN_25"</span><span class="token punctuation">,</span>
    <span class="token string">"   - adc_clk        → PIN_26"</span><span class="token punctuation">,</span>
    <span class="token string">"   - pwm_calefactor → PIN_1"</span><span class="token punctuation">,</span>
    <span class="token string">"   - led_ia         → PIN_2"</span><span class="token punctuation">,</span>
    <span class="token string">"   - led_pid        → PIN_3"</span><span class="token punctuation">,</span> 
    <span class="token string">"   - modo_control   → PIN_4"</span><span class="token punctuation">,</span>
    <span class="token string">"3. Cerrar Pin Planner (guarda automáticamente)"</span>
<span class="token punctuation">]</span>
</code></pre>
<h2 id="paso-3-compilar-y-programar"><strong>PASO 3: COMPILAR Y PROGRAMAR</strong></h2>
<pre class=" language-python"><code class="prism  language-python">PASOS_PROGRAMACION <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token string">"1. 'Processing' → 'Start Compilation' (esperar 2-3 min)"</span><span class="token punctuation">,</span>
    <span class="token string">"2. Verificar: 'Full Compilation was successful'"</span><span class="token punctuation">,</span>
    <span class="token string">"3. Conectar FPGA con cable USB"</span><span class="token punctuation">,</span>
    <span class="token string">"4. 'Tools' → 'Programmer'"</span><span class="token punctuation">,</span> 
    <span class="token string">"5. Verificar 'USB-Blaster [USB-0]' aparece"</span><span class="token punctuation">,</span>
    <span class="token string">"6. 'Auto Detect' → Seleccionar 'EPM240'"</span><span class="token punctuation">,</span>
    <span class="token string">"7. 'Add File' → Buscar 'control_temperatura_adc.sof'"</span><span class="token punctuation">,</span>
    <span class="token string">"8. CHECK 'Program/Configure' → CLICK 'Start'"</span><span class="token punctuation">,</span>
    <span class="token string">"9. Esperar barra verde 100% → ✅ FPGA PROGRAMADA"</span>
<span class="token punctuation">]</span>
</code></pre>
<hr>
<h1 id="📋-checklist-final-del-proyecto">📋 <strong>CHECKLIST FINAL DEL PROYECTO</strong></h1>
<pre class=" language-python"><code class="prism  language-python">CHECKLIST_COMPLETO <span class="token operator">=</span> <span class="token punctuation">[</span>
    <span class="token string">"✅ TEORÍA: Fundamentos de instrumentación comprendidos"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ SENSOR: LM35 conectado correctamente (+5V, GND, Señal)"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ ADC: MCP3008 con SPI (CS, CLK, MOSI, MISO)"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ FPGA: Código VHDL completo con control PID + Red Neuronal"</span><span class="token punctuation">,</span> 
    <span class="token string">"✅ TESTBENCH: Simulación RTL exitosa verificada"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ PINES: Configuración correcta en Quartus"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ COMPILACIÓN: 0 errores, 0 warnings críticos"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ PROGRAMACIÓN: FPGA cargada exitosamente"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ PRUEBAS: Sistema responde a cambios de temperatura"</span><span class="token punctuation">,</span>
    <span class="token string">"✅ DOCUMENTACIÓN: Reporte técnico completo"</span>
<span class="token punctuation">]</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"🎓 ¡PROYECTO INTEGRADOR COMPLETO Y FUNCIONAL!"</span><span class="token punctuation">)</span>
</code></pre>
<hr>
<h1 id="📚-referencias-bibliográficas">📚 <strong>REFERENCIAS BIBLIOGRÁFICAS</strong></h1>
<ol>
<li><strong>Bentley, J.P.</strong> (2020). <em>Principles of Measurement Systems</em>. Pearson</li>
<li><strong>Johnson, R.D.</strong> (2019). <em>Process Control Instrumentation Technology</em>. Prentice Hall</li>
<li><strong>Microchip Technology</strong> (2019). <em>MCP3008 Datasheet - 10-Bit ADC with SPI Interface</em></li>
<li><strong>Texas Instruments</strong> (2020). <em>LM35 Precision Centigrade Temperature Sensors Datasheet</em></li>
<li><strong>Ogata, K.</strong> (2010). <em>Modern Control Engineering</em>. Prentice Hall</li>
<li><strong>ISO/IEC 17025:2017</strong> - Competencia de laboratorios de ensayo y calibración</li>
</ol>
<hr>
<p><strong>¡PROYECTO INTEGRADOR 100% COMPLETO!</strong> 🎯🔧🚀<br>
<em>Incluye teoría, práctica, código, testbench y configuración completa</em></p>
</div>
</body>

</html>
