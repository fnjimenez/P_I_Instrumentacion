<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>II PF</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="🎛️-proyecto-integrador-–-unidad-iii-instrumentación-industrial">🎛️ Proyecto Integrador – Unidad III: Instrumentación Industrial</h1>
<h2 id="sistema-completo-de-sensores-transmisores-actuadores-control-automático-y-calibración">Sistema Completo de Sensores, Transmisores, Actuadores, Control Automático y Calibración</h2>
<h3 id="integrando-actividad-9-y-actividad-10-en-un-solo-proyecto-profesional"><em>Integrando Actividad 9 y Actividad 10 en un solo proyecto profesional</em></h3>
<hr>
<h1 id="🏫-universidad-sabes-–-ingeniería-industrial">🏫 <strong>Universidad SABES – Ingeniería Industrial</strong></h1>
<h2 id="unidad-iii-instrumentación-industrial"><strong>Unidad III: Instrumentación Industrial</strong></h2>
<h3 id="competencia-específica"><strong>Competencia Específica:</strong></h3>
<blockquote>
<p><em>“Selecciona, configura y opera instrumentos de medición y control para el monitoreo y regulación automatizada de procesos industriales, aplicando principios metrológicos y estándares de calibración.”</em></p>
</blockquote>
<hr>
<h1 id="📘-1.-introducción-general-y-definiciones-conceptuales">📘 1. INTRODUCCIÓN GENERAL Y DEFINICIONES CONCEPTUALES</h1>
<h2 id="¿qué-es-la-instrumentación-industrial">1.1 ¿Qué es la Instrumentación Industrial?</h2>
<p><strong>Instrumentación Industrial</strong> es la disciplina que se encarga del estudio, selección, instalación, configuración y mantenimiento de todos los dispositivos utilizados para medir, transmitir, controlar y registrar variables físicas en procesos industriales.</p>
<h2 id="conceptos-fundamentales">1.2 Conceptos Fundamentales</h2>
<h3 id="variable-de-proceso"><strong>Variable de Proceso</strong></h3>
<p>Magnitud física o química que se desea medir y controlar en un proceso industrial.</p>
<ul>
<li><strong>Ejemplos</strong>: Temperatura, presión, nivel, caudal, pH, conductividad</li>
</ul>
<h3 id="sensortransductor"><strong>Sensor/Transductor</strong></h3>
<p>Dispositivo que detecta una variable física y la convierte en una señal eléctrica.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Ejemplo conceptual</span>
Variable Física → Sensor → Señal Eléctrica
Temperatura → RTD → Resistencia <span class="token punctuation">(</span>Ω<span class="token punctuation">)</span>
</code></pre>
<h3 id="transmisor"><strong>Transmisor</strong></h3>
<p>Equipo que acondiciona la señal del sensor y la convierte a un estándar industrial.</p>
<pre class=" language-python"><code class="prism  language-python">Señal <span class="token keyword">del</span> Sensor → Transmisor → Señal Estándar
Resistencia <span class="token punctuation">(</span>Ω<span class="token punctuation">)</span> → Transmisor → <span class="token number">4</span><span class="token operator">-</span><span class="token number">20</span> mA
</code></pre>
<h3 id="controlador"><strong>Controlador</strong></h3>
<p>Dispositivo que compara la variable medida con un setpoint y calcula una acción correctiva.</p>
<h3 id="actuador"><strong>Actuador</strong></h3>
<p>Elemento final que recibe la señal de control y modifica el proceso.</p>
<pre class=" language-python"><code class="prism  language-python">Señal Control → Actuador → Acción Física
<span class="token number">4</span><span class="token operator">-</span><span class="token number">20</span> mA → Válvula → Apertura<span class="token operator">/</span>Cierre
</code></pre>
<h2 id="características-metrológicas-fundamentales">1.3 Características Metrológicas Fundamentales</h2>
<h3 id="exactitud-accuracy"><strong>Exactitud (Accuracy)</strong></h3>
<p>Grado de concordancia entre el valor medido y el valor verdadero.</p>
<pre class=" language-python"><code class="prism  language-python">Error <span class="token operator">=</span> Valor Verdadero <span class="token operator">-</span> Valor Medido
Exactitud <span class="token operator">=</span> <span class="token number">1</span> <span class="token operator">-</span> <span class="token operator">|</span>Error<span class="token operator">|</span> <span class="token operator">/</span> Valor Verdadero
</code></pre>
<h3 id="precisión-precision"><strong>Precisión (Precision)</strong></h3>
<p>Capacidad del instrumento para dar el mismo resultado en mediciones repetidas.</p>
<h3 id="resolución"><strong>Resolución</strong></h3>
<p>Cambio más pequeño en la variable que puede detectar el instrumento.</p>
<h3 id="sensibilidad"><strong>Sensibilidad</strong></h3>
<p>Relación entre la salida del instrumento y el cambio en la variable medida.</p>
<h3 id="histéresis"><strong>Histéresis</strong></h3>
<p>Diferencia en la salida para el mismo valor de entrada, dependiendo si la variable aumenta o disminuye.</p>
<h3 id="linealidad"><strong>Linealidad</strong></h3>
<p>Grado en que la curva de calibración se aproxima a una línea recta.</p>
<h3 id="rango-span"><strong>Rango (Span)</strong></h3>
<p>Diferencia entre los valores máximo y mínimo que puede medir el instrumento.</p>
<pre class=" language-python"><code class="prism  language-python">Span <span class="token operator">=</span> Upper Range Value <span class="token operator">-</span> Lower Range Value
Ejemplo<span class="token punctuation">:</span> <span class="token number">0</span><span class="token operator">-</span><span class="token number">100</span>°C → Span <span class="token operator">=</span> <span class="token number">100</span>°C
</code></pre>
<h3 id="zona-muerta-dead-band"><strong>Zona Muerta (Dead Band)</strong></h3>
<p>Rango de valores en los cuales la variable puede cambiar sin que el instrumento detecte el cambio.</p>
<hr>
<h1 id="🧩-2.-semana-8-–-definiciones-y-transmisores-conceptos-detallados">🧩 2. SEMANA 8 – DEFINICIONES Y TRANSMISORES: CONCEPTOS DETALLADOS</h1>
<h2 id="tipos-de-señales-en-instrumentación">2.1 Tipos de Señales en Instrumentación</h2>
<h3 id="señales-analógicas"><strong>Señales Analógicas</strong></h3>
<ul>
<li><strong>4-20 mA</strong>: Estándar industrial más común
<ul>
<li><strong>4 mA</strong>: Cero de la variable o falla</li>
<li><strong>20 mA</strong>: Máximo de la variable</li>
<li><strong>Ventajas</strong>: Inmune a ruido, detección de fallas</li>
</ul>
</li>
<li><strong>0-10 VDC</strong>: Usada en aplicaciones cortas</li>
<li><strong>0-5 VDC</strong>: Común en sistemas de adquisición de datos</li>
</ul>
<h3 id="señales-digitales"><strong>Señales Digitales</strong></h3>
<ul>
<li><strong>HART (Highway Addressable Remote Transducer)</strong>
<ul>
<li>Señal digital superpuesta sobre 4-20 mA</li>
<li>Permite configuración remota y diagnóstico</li>
</ul>
</li>
<li><strong>Foundation Fieldbus</strong></li>
<li><strong>Profibus PA/DP</strong></li>
</ul>
<h2 id="estructura-de-un-sistema-de-instrumentación">2.2 Estructura de un Sistema de Instrumentación</h2>
<pre><code>Variable → Sensor → Transmisor → Controlador → Actuador → Proceso
         (Medición) (Acondicionamiento) (Decisión)  (Acción)
</code></pre>
<h2 id="clasificación-de-instrumentos">2.3 Clasificación de Instrumentos</h2>
<h3 id="por-función"><strong>Por Función</strong></h3>
<ul>
<li><strong>Instrumentos de Medición</strong>: Indicadores, registradores</li>
<li><strong>Instrumentos de Control</strong>: Controladores, PLCs, DCS</li>
<li><strong>Elementos Finales</strong>: Válvulas, motores, calefactores</li>
</ul>
<h3 id="por-señal-de-salida"><strong>Por Señal de Salida</strong></h3>
<ul>
<li><strong>Neumáticos</strong>: 3-15 psi</li>
<li><strong>Eléctricos</strong>: 4-20 mA, 0-10 V</li>
<li><strong>Digitales</strong>: HART, Fieldbus, Profibus</li>
</ul>
<h3 id="por-aplicación"><strong>Por Aplicación</strong></h3>
<ul>
<li><strong>Campo</strong>: Sensores, transmisores, actuadores</li>
<li><strong>Sala de Control</strong>: Controladores, indicadores</li>
<li><strong>Analíticos</strong>: pH, conductividad, analizadores de gases</li>
</ul>
<hr>
<h1 id="📘-semana-9-–-medición-de-variables-industriales-conceptos-detallados">📘 SEMANA 9 – MEDICIÓN DE VARIABLES INDUSTRIALES: CONCEPTOS DETALLADOS</h1>
<h2 id="medición-de-temperatura">3.1 Medición de Temperatura</h2>
<h3 id="principios-físicos"><strong>Principios Físicos</strong></h3>
<ul>
<li><strong>Dilatación térmica</strong>: Termómetros bimetálicos</li>
<li><strong>Resistencia eléctrica</strong>: RTD, termistores</li>
<li><strong>Efecto termoeléctrico</strong>: Termopares</li>
<li><strong>Radiación infrarroja</strong>: Pirómetros</li>
</ul>
<h3 id="rtd-resistance-temperature-detector"><strong>RTD (Resistance Temperature Detector)</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Ecuación de Callendar-Van Dusen para RTD Pt100</span>
R<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> R₀<span class="token punctuation">[</span><span class="token number">1</span> <span class="token operator">+</span> AT <span class="token operator">+</span> BT² <span class="token operator">+</span> C<span class="token punctuation">(</span>T<span class="token number">-100</span><span class="token punctuation">)</span>T³<span class="token punctuation">]</span> para T <span class="token operator">&lt;</span> <span class="token number">0</span>°C
R<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> R₀<span class="token punctuation">(</span><span class="token number">1</span> <span class="token operator">+</span> AT <span class="token operator">+</span> BT²<span class="token punctuation">)</span> para T ≥ <span class="token number">0</span>°C
Donde<span class="token punctuation">:</span>
R₀ <span class="token operator">=</span> <span class="token number">100</span> Ω a <span class="token number">0</span>°C
A <span class="token operator">=</span> <span class="token number">3.9083</span> × <span class="token number">10</span>⁻³
B <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">5.775</span> × <span class="token number">10</span>⁻⁷
C <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">4.183</span> × <span class="token number">10</span>⁻¹² <span class="token punctuation">(</span>solo para T <span class="token operator">&lt;</span> <span class="token number">0</span>°C<span class="token punctuation">)</span>
</code></pre>
<h3 id="termopares"><strong>Termopares</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Principio de Seebeck</span>
V <span class="token operator">=</span> α<span class="token punctuation">(</span>T<span class="token punctuation">)</span> × ΔT
Donde<span class="token punctuation">:</span>
V <span class="token operator">=</span> Voltaje generado
α<span class="token punctuation">(</span>T<span class="token punctuation">)</span> <span class="token operator">=</span> Coeficiente Seebeck <span class="token punctuation">(</span>depende <span class="token keyword">del</span> material<span class="token punctuation">)</span>
ΔT <span class="token operator">=</span> Diferencia de temperatura entre uniones
</code></pre>
<p><strong>Tipos Comunes:</strong></p>
<ul>
<li><strong>Tipo J</strong>: Hierro-Constantán (-210 a 1200°C)</li>
<li><strong>Tipo K</strong>: Cromel-Alumel (-270 a 1372°C)</li>
<li><strong>Tipo T</strong>: Cobre-Constantán (-270 a 400°C)</li>
<li><strong>Tipo E</strong>: Cromel-Constantán (-270 a 1000°C)</li>
</ul>
<h2 id="medición-de-presión">3.2 Medición de Presión</h2>
<h3 id="unidades-de-presión"><strong>Unidades de Presión</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token number">1</span> bar <span class="token operator">=</span> <span class="token number">100</span> kPa <span class="token operator">=</span> <span class="token number">14.5</span> psi <span class="token operator">=</span> <span class="token number">750.06</span> mmHg <span class="token operator">=</span> <span class="token number">10.197</span> mH₂O
<span class="token number">1</span> atm <span class="token operator">=</span> <span class="token number">101.325</span> kPa <span class="token operator">=</span> <span class="token number">14.696</span> psi
</code></pre>
<h3 id="tipos-de-presión"><strong>Tipos de Presión</strong></h3>
<ul>
<li><strong>Presión absoluta</strong>: Referencia al vacío perfecto</li>
<li><strong>Presión manométrica</strong>: Referencia a presión atmosférica</li>
<li><strong>Presión diferencial</strong>: Diferencia entre dos puntos</li>
</ul>
<h3 id="instrumentos-de-medición"><strong>Instrumentos de Medición</strong></h3>
<ul>
<li><strong>Manómetros de tubo Bourdon</strong></li>
<li><strong>Transductores de presión</strong>: Strain gages, capacitivos</li>
<li><strong>Celdas de carga</strong>: Para medición de fuerza/peso</li>
</ul>
<h2 id="medición-de-nivel">3.3 Medición de Nivel</h2>
<h3 id="métodos-de-medición"><strong>Métodos de Medición</strong></h3>
<ul>
<li><strong>Directos</strong>: Visual, flotador, sonda capacitiva</li>
<li><strong>Indirectos</strong>: Presión hidrostática, ultrasónico, radar</li>
</ul>
<h3 id="principio-de-presión-hidrostática"><strong>Principio de Presión Hidrostática</strong></h3>
<pre class=" language-python"><code class="prism  language-python">P <span class="token operator">=</span> ρ × g × h
Donde<span class="token punctuation">:</span>
P <span class="token operator">=</span> Presión hidrostática <span class="token punctuation">(</span>Pa<span class="token punctuation">)</span>
ρ <span class="token operator">=</span> Densidad <span class="token keyword">del</span> fluido <span class="token punctuation">(</span>kg<span class="token operator">/</span>m³<span class="token punctuation">)</span>
g <span class="token operator">=</span> Gravedad <span class="token punctuation">(</span><span class="token number">9.81</span> m<span class="token operator">/</span>s²<span class="token punctuation">)</span>
h <span class="token operator">=</span> Altura <span class="token keyword">del</span> líquido <span class="token punctuation">(</span>m<span class="token punctuation">)</span>
</code></pre>
<h2 id="medición-de-caudal">3.4 Medición de Caudal</h2>
<h3 id="tipos-de-flujómetros"><strong>Tipos de Flujómetros</strong></h3>
<ul>
<li><strong>Diferencial de presión</strong>: Placa orificio, tubo Venturi</li>
<li><strong>Magnéticos</strong>: Ley de Faraday</li>
<li><strong>Másicos</strong>: Coriolis, térmicos</li>
<li><strong>Turbina</strong>: Velocidad del fluido</li>
</ul>
<h3 id="ecuación-de-placa-orificio"><strong>Ecuación de Placa Orificio</strong></h3>
<pre class=" language-python"><code class="prism  language-python">Q <span class="token operator">=</span> C × A × √<span class="token punctuation">(</span><span class="token number">2</span> × ΔP <span class="token operator">/</span> ρ<span class="token punctuation">)</span>
Donde<span class="token punctuation">:</span>
Q <span class="token operator">=</span> Caudal
C <span class="token operator">=</span> Coeficiente de descarga
A <span class="token operator">=</span> Área <span class="token keyword">del</span> orificio
ΔP <span class="token operator">=</span> Diferencial de presión
ρ <span class="token operator">=</span> Densidad <span class="token keyword">del</span> fluido
</code></pre>
<hr>
<h1 id="📘-semana-10-–-elementos-finales-de-control-conceptos-detallados">📘 SEMANA 10 – ELEMENTOS FINALES DE CONTROL: CONCEPTOS DETALLADOS</h1>
<h2 id="válvulas-de-control">4.1 Válvulas de Control</h2>
<h3 id="componentes-principales"><strong>Componentes Principales</strong></h3>
<ul>
<li><strong>Cuerpo de válvula</strong>: Contiene el elemento de control</li>
<li><strong>Actuador</strong>: Convierte señal en movimiento</li>
<li><strong>Posicionador</strong>: Asegura posición correcta</li>
<li><strong>Accesorios</strong>: Transductores, limit switches</li>
</ul>
<h3 id="tipos-de-cuerpos-de-válvula"><strong>Tipos de Cuerpos de Válvula</strong></h3>
<ul>
<li><strong>Globo</strong>: Control preciso, alta rangabilidad</li>
<li><strong>Mariposa</strong>: Bajo costo, alto caudal</li>
<li><strong>Bola</strong>: Cierre hermético, rápido</li>
<li><strong>Diafragma</strong>: Para fluidos corrosivos</li>
</ul>
<h3 id="características-de-flujo"><strong>Características de Flujo</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Característica Lineal</span>
Q<span class="token operator">/</span>Q_max <span class="token operator">=</span> C_v × <span class="token punctuation">(</span>ΔP<span class="token operator">/</span>ΔP_max<span class="token punctuation">)</span>

<span class="token comment"># Característica de Igual Porcentaje</span>
Q<span class="token operator">/</span>Q_max <span class="token operator">=</span> R<span class="token operator">^</span><span class="token punctuation">(</span>L<span class="token operator">/</span>L_max <span class="token operator">-</span> <span class="token number">1</span><span class="token punctuation">)</span>
Donde<span class="token punctuation">:</span>
Q <span class="token operator">=</span> Caudal
C_v <span class="token operator">=</span> Coeficiente de válvula
R <span class="token operator">=</span> Rangabilidad <span class="token punctuation">(</span>typically <span class="token number">25</span><span class="token operator">-</span><span class="token number">50</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="actuadores">4.2 Actuadores</h2>
<h3 id="actuadores-neumáticos"><strong>Actuadores Neumáticos</strong></h3>
<ul>
<li><strong>Ventajas</strong>: Simple, seguro en áreas explosivas</li>
<li><strong>Desventajas</strong>: Requiere aire comprimido</li>
<li><strong>Señal estándar</strong>: 3-15 psig</li>
</ul>
<h3 id="actuadores-eléctricos"><strong>Actuadores Eléctricos</strong></h3>
<ul>
<li><strong>Ventajas</strong>: Precisos, fácil control</li>
<li><strong>Desventajas</strong>: Más lentos, riesgo en explosivos</li>
</ul>
<h3 id="actuadores-hidráulicos"><strong>Actuadores Hidráulicos</strong></h3>
<ul>
<li><strong>Ventajas</strong>: Alta fuerza, rápida respuesta</li>
<li><strong>Desventajas</strong>: Complejos, mantenimiento</li>
</ul>
<h2 id="cálculo-de-sizing-de-válvulas">4.3 Cálculo de Sizing de Válvulas</h2>
<h3 id="coeficiente-cv"><strong>Coeficiente Cv</strong></h3>
<pre class=" language-python"><code class="prism  language-python">C_v <span class="token operator">=</span> Q × √<span class="token punctuation">(</span>SG <span class="token operator">/</span> ΔP<span class="token punctuation">)</span>
Donde<span class="token punctuation">:</span>
Q <span class="token operator">=</span> Caudal <span class="token punctuation">(</span>GPM<span class="token punctuation">)</span>
SG <span class="token operator">=</span> Gravedad específica
ΔP <span class="token operator">=</span> Caída de presión <span class="token punctuation">(</span>psi<span class="token punctuation">)</span>
</code></pre>
<h3 id="factor-de-ruido-y-cavitación"><strong>Factor de Ruido y Cavitación</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Factor de cavitación inicial</span>
σ_i <span class="token operator">=</span> <span class="token punctuation">(</span>P_1 <span class="token operator">-</span> P_v<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token punctuation">(</span>P_1 <span class="token operator">-</span> P_2<span class="token punctuation">)</span>

<span class="token comment"># Factor de ruido</span>
N <span class="token operator">=</span> L <span class="token operator">-</span> L_1 <span class="token punctuation">(</span>debe ser <span class="token operator">&gt;</span> <span class="token number">4</span><span class="token operator">-</span><span class="token number">6</span> dBA para aceptable<span class="token punctuation">)</span>
</code></pre>
<hr>
<h1 id="📘-semana-11-–-regulación-automática-conceptos-detallados">📘 SEMANA 11 – REGULACIÓN AUTOMÁTICA: CONCEPTOS DETALLADOS</h1>
<h2 id="controladores-pid">5.1 Controladores PID</h2>
<h3 id="ecuación-del-pid-ideal"><strong>Ecuación del PID Ideal</strong></h3>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> K_p × e<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">+</span> K_i × ∫e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>dt <span class="token operator">+</span> K_d × de<span class="token punctuation">(</span>t<span class="token punctuation">)</span><span class="token operator">/</span>dt
Donde<span class="token punctuation">:</span>
u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Señal de control
e<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> Error <span class="token punctuation">(</span>SP <span class="token operator">-</span> PV<span class="token punctuation">)</span>
K_p <span class="token operator">=</span> Ganancia proporcional
K_i <span class="token operator">=</span> Ganancia integral <span class="token punctuation">(</span><span class="token number">1</span><span class="token operator">/</span>T_i<span class="token punctuation">)</span>
K_d <span class="token operator">=</span> Ganancia derivativa <span class="token punctuation">(</span>T_d<span class="token punctuation">)</span>
</code></pre>
<h3 id="acción-proporcional-p"><strong>Acción Proporcional §</strong></h3>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> K_p × e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>
<span class="token comment"># Efecto: Respuesta rápida pero error estacionario</span>
</code></pre>
<h3 id="acción-integral-i"><strong>Acción Integral (I)</strong></h3>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> K_i × ∫e<span class="token punctuation">(</span>t<span class="token punctuation">)</span>dt
<span class="token comment"># Efecto: Elimina error estacionario pero puede causar oscilaciones</span>
</code></pre>
<h3 id="acción-derivativa-d"><strong>Acción Derivativa (D)</strong></h3>
<pre class=" language-python"><code class="prism  language-python">u<span class="token punctuation">(</span>t<span class="token punctuation">)</span> <span class="token operator">=</span> K_d × de<span class="token punctuation">(</span>t<span class="token punctuation">)</span><span class="token operator">/</span>dt
<span class="token comment"># Efecto: Anticipa tendencias, reduce overshoot</span>
</code></pre>
<h2 id="métodos-de-sintonización">5.2 Métodos de Sintonización</h2>
<h3 id="método-de-ziegler-nichols-respuesta-al-escalón"><strong>Método de Ziegler-Nichols (Respuesta al Escalón)</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Basado en curva de reacción</span>
K_p <span class="token operator">=</span> <span class="token number">1.2</span> × <span class="token punctuation">(</span>T <span class="token operator">/</span> <span class="token punctuation">(</span>K × τ<span class="token punctuation">)</span><span class="token punctuation">)</span>
T_i <span class="token operator">=</span> <span class="token number">2.0</span> × τ
T_d <span class="token operator">=</span> <span class="token number">0.5</span> × τ
</code></pre>
<h3 id="método-de-cohen-coon"><strong>Método de Cohen-Coon</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Para procesos con gran retardo</span>
K_p <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">1</span><span class="token operator">/</span>K<span class="token punctuation">)</span> × <span class="token punctuation">(</span>τ<span class="token operator">/</span>T<span class="token punctuation">)</span> × <span class="token punctuation">(</span><span class="token number">1.33</span> <span class="token operator">+</span> T<span class="token operator">/</span><span class="token punctuation">(</span><span class="token number">4</span>τ<span class="token punctuation">)</span><span class="token punctuation">)</span>
T_i <span class="token operator">=</span> τ × <span class="token punctuation">(</span><span class="token number">32</span> <span class="token operator">+</span> 6T<span class="token operator">/</span>τ<span class="token punctuation">)</span> <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">13</span> <span class="token operator">+</span> 8T<span class="token operator">/</span>τ<span class="token punctuation">)</span>
T_d <span class="token operator">=</span> τ × <span class="token number">4</span> <span class="token operator">/</span> <span class="token punctuation">(</span><span class="token number">11</span> <span class="token operator">+</span> 2T<span class="token operator">/</span>τ<span class="token punctuation">)</span>
</code></pre>
<h2 id="estabilidad-del-sistema">5.3 Estabilidad del Sistema</h2>
<h3 id="criterio-de-routh-hurwitz"><strong>Criterio de Routh-Hurwitz</strong></h3>
<p>Método para determinar estabilidad sin calcular raíces.</p>
<h3 id="margen-de-ganancia-y-fase"><strong>Margen de Ganancia y Fase</strong></h3>
<ul>
<li><strong>Margen de Ganancia</strong>: Factor que puede aumentar ganancia antes de inestabilidad</li>
<li><strong>Margen de Fase</strong>: Fase adicional que puede añadirse antes de inestabilidad</li>
</ul>
<hr>
<h1 id="📘-semana-12-–-calibración-de-instrumentos-conceptos-detallados">📘 SEMANA 12 – CALIBRACIÓN DE INSTRUMENTOS: CONCEPTOS DETALLADOS</h1>
<h2 id="fundamentos-de-metrología">6.1 Fundamentos de Metrología</h2>
<h3 id="trazabilidad-metrológica"><strong>Trazabilidad Metrológica</strong></h3>
<pre class=" language-python"><code class="prism  language-python">Instrumento → Patrón interno → Patrón nacional → SI
</code></pre>
<h3 id="incertidumbre-de-medición"><strong>Incertidumbre de Medición</strong></h3>
<pre class=" language-python"><code class="prism  language-python">Incertidumbre Expandida <span class="token operator">=</span> k × u_c
Donde<span class="token punctuation">:</span>
k <span class="token operator">=</span> Factor de cobertura <span class="token punctuation">(</span>generalmente <span class="token number">2</span> para <span class="token number">95</span><span class="token operator">%</span><span class="token punctuation">)</span>
u_c <span class="token operator">=</span> Incertidumbre combinada
</code></pre>
<h2 id="tipos-de-error">6.2 Tipos de Error</h2>
<h3 id="error-sistemático"><strong>Error Sistemático</strong></h3>
<p>Error constante o predecible</p>
<pre class=" language-python"><code class="prism  language-python">Error Sistemático <span class="token operator">=</span> Valor Medio <span class="token operator">-</span> Valor Verdadero
</code></pre>
<h3 id="error-aleatorio"><strong>Error Aleatorio</strong></h3>
<p>Variaciones impredecibles en mediciones repetidas</p>
<h3 id="curva-de-calibración"><strong>Curva de Calibración</strong></h3>
<pre class=" language-python"><code class="prism  language-python">y <span class="token operator">=</span> a <span class="token operator">+</span> bx <span class="token operator">+</span> ε
Donde<span class="token punctuation">:</span>
y <span class="token operator">=</span> Valor indicado
x <span class="token operator">=</span> Valor patrón
a <span class="token operator">=</span> Intercepto <span class="token punctuation">(</span>error de cero<span class="token punctuation">)</span>
b <span class="token operator">=</span> Pendiente <span class="token punctuation">(</span>error de span<span class="token punctuation">)</span>
ε <span class="token operator">=</span> Error residual
</code></pre>
<h2 id="procedimiento-de-calibración">6.3 Procedimiento de Calibración</h2>
<h3 id="puntos-de-calibración"><strong>Puntos de Calibración</strong></h3>
<ul>
<li><strong>Cero</strong>: Punto inferior del rango</li>
<li><strong>Span</strong>: Punto superior del rango</li>
<li><strong>Puntos intermedios</strong>: Para verificar linealidad</li>
</ul>
<h3 id="ajuste-de-cero-y-span"><strong>Ajuste de Cero y Span</strong></h3>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># Ajuste de cero</span>
Salida_real <span class="token operator">=</span> Salida_medida <span class="token operator">-</span> Offset

<span class="token comment"># Ajuste de span</span>
Salida_corregida <span class="token operator">=</span> <span class="token punctuation">(</span>Salida_real <span class="token operator">-</span> Zero<span class="token punctuation">)</span> × <span class="token punctuation">(</span>Span_nominal <span class="token operator">/</span> Span_actual<span class="token punctuation">)</span>
</code></pre>
<h2 id="normativas-de-calibración">6.4 Normativas de Calibración</h2>
<h3 id="iso-90012015"><strong>ISO 9001:2015</strong></h3>
<p>Requisitos para sistemas de gestión de calidad</p>
<h3 id="isoiec-170252017"><strong>ISO/IEC 17025:2017</strong></h3>
<p>Requisitos para laboratorios de ensayo y calibración</p>
<h3 id="ansincsl-z540.3"><strong>ANSI/NCSL Z540.3</strong></h3>
<p>Requisitos para calibración de instrumentos de medición</p>
<hr>
<h1 id="🔧-7.-implementación-práctica-sistema-completo-de-instrumentación">🔧 7. IMPLEMENTACIÓN PRÁCTICA: SISTEMA COMPLETO DE INSTRUMENTACIÓN</h1>
<h2 id="arquitectura-del-sistema-integrado">7.1 Arquitectura del Sistema Integrado</h2>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">import</span> numpy <span class="token keyword">as</span> np
<span class="token keyword">import</span> pandas <span class="token keyword">as</span> pd
<span class="token keyword">import</span> matplotlib<span class="token punctuation">.</span>pyplot <span class="token keyword">as</span> plt
<span class="token keyword">from</span> datetime <span class="token keyword">import</span> datetime<span class="token punctuation">,</span> timedelta

<span class="token keyword">class</span> <span class="token class-name">SistemaInstrumentacionCompleto</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""
    Sistema completo de instrumentación industrial que integra:
    - Sensado y transmisión
    - Control automático PID
    - Actuación
    - Calibración metrológica
    """</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token comment"># Parámetros del sistema</span>
        self<span class="token punctuation">.</span>temperatura_actual <span class="token operator">=</span> <span class="token number">25.0</span>  <span class="token comment"># °C</span>
        self<span class="token punctuation">.</span>setpoint <span class="token operator">=</span> <span class="token number">80.0</span>  <span class="token comment"># °C</span>
        self<span class="token punctuation">.</span>tiempo_simulacion <span class="token operator">=</span> <span class="token number">0</span>
        
        <span class="token comment"># Inicializar componentes</span>
        self<span class="token punctuation">.</span>sensor <span class="token operator">=</span> SensorTemperatura<span class="token punctuation">(</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>transmisor <span class="token operator">=</span> Transmisor4_20mA<span class="token punctuation">(</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>controlador <span class="token operator">=</span> PIDController<span class="token punctuation">(</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>actuador <span class="token operator">=</span> ActuadorCalefactor<span class="token punctuation">(</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>calibrador <span class="token operator">=</span> SistemaCalibracion<span class="token punctuation">(</span><span class="token punctuation">)</span>
        
        <span class="token comment"># Historial de datos</span>
        self<span class="token punctuation">.</span>historial <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
    
    <span class="token keyword">def</span> <span class="token function">ejecutar_ciclo_control</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> dt<span class="token operator">=</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""Ejecuta un ciclo completo de control"""</span>
        
        <span class="token comment"># 1. MEDICIÓN (Sensor)</span>
        temp_medida <span class="token operator">=</span> self<span class="token punctuation">.</span>sensor<span class="token punctuation">.</span>medir<span class="token punctuation">(</span>self<span class="token punctuation">.</span>temperatura_actual<span class="token punctuation">)</span>
        
        <span class="token comment"># 2. TRANSMISIÓN (Transmisor)</span>
        señal_4_20mA <span class="token operator">=</span> self<span class="token punctuation">.</span>transmisor<span class="token punctuation">.</span>convertir<span class="token punctuation">(</span>temp_medida<span class="token punctuation">)</span>
        
        <span class="token comment"># 3. CONTROL (PID)</span>
        señal_control <span class="token operator">=</span> self<span class="token punctuation">.</span>controlador<span class="token punctuation">.</span>update<span class="token punctuation">(</span>temp_medida<span class="token punctuation">)</span>
        
        <span class="token comment"># 4. ACTUACIÓN</span>
        potencia_real <span class="token operator">=</span> self<span class="token punctuation">.</span>actuador<span class="token punctuation">.</span>set_potencia<span class="token punctuation">(</span>señal_control<span class="token punctuation">,</span> dt<span class="token punctuation">)</span>
        
        <span class="token comment"># 5. DINÁMICA DEL PROCESO</span>
        self<span class="token punctuation">.</span>simular_proceso_termico<span class="token punctuation">(</span>potencia_real<span class="token punctuation">,</span> dt<span class="token punctuation">)</span>
        
        <span class="token comment"># 6. REGISTRO</span>
        self<span class="token punctuation">.</span>registrar_datos<span class="token punctuation">(</span>temp_medida<span class="token punctuation">,</span> señal_4_20mA<span class="token punctuation">,</span> señal_control<span class="token punctuation">,</span> potencia_real<span class="token punctuation">)</span>
        
        <span class="token keyword">return</span> <span class="token punctuation">{</span>
            <span class="token string">'temperatura'</span><span class="token punctuation">:</span> temp_medida<span class="token punctuation">,</span>
            <span class="token string">'senal_4_20mA'</span><span class="token punctuation">:</span> señal_4_20mA<span class="token punctuation">,</span>
            <span class="token string">'control'</span><span class="token punctuation">:</span> señal_control<span class="token punctuation">,</span>
            <span class="token string">'potencia'</span><span class="token punctuation">:</span> potencia_real
        <span class="token punctuation">}</span>
    
    <span class="token keyword">def</span> <span class="token function">simular_proceso_termico</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> potencia<span class="token punctuation">,</span> dt<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""Simula la dinámica del proceso térmico"""</span>
        <span class="token comment"># Modelo de primer orden con ganancia y constante de tiempo</span>
        K <span class="token operator">=</span> <span class="token number">0.8</span>    <span class="token comment"># Ganancia del proceso (°C/kW)</span>
        tau <span class="token operator">=</span> <span class="token number">120</span>   <span class="token comment"># Constante de tiempo (segundos)</span>
        
        <span class="token comment"># Ecuación diferencial: dT/dt = (K*P - (T - T_amb)) / tau</span>
        T_amb <span class="token operator">=</span> <span class="token number">25.0</span>  <span class="token comment"># Temperatura ambiente</span>
        
        dT_dt <span class="token operator">=</span> <span class="token punctuation">(</span>K <span class="token operator">*</span> potencia <span class="token operator">-</span> <span class="token punctuation">(</span>self<span class="token punctuation">.</span>temperatura_actual <span class="token operator">-</span> T_amb<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">/</span> tau
        self<span class="token punctuation">.</span>temperatura_actual <span class="token operator">+=</span> dT_dt <span class="token operator">*</span> dt
        
        <span class="token comment"># Ruido de proceso</span>
        self<span class="token punctuation">.</span>temperatura_actual <span class="token operator">+=</span> np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>normal<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0.1</span><span class="token punctuation">)</span>
    
    <span class="token keyword">def</span> <span class="token function">registrar_datos</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temp<span class="token punctuation">,</span> señal<span class="token punctuation">,</span> control<span class="token punctuation">,</span> potencia<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""Registra datos del ciclo actual"""</span>
        registro <span class="token operator">=</span> <span class="token punctuation">{</span>
            <span class="token string">'timestamp'</span><span class="token punctuation">:</span> datetime<span class="token punctuation">.</span>now<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
            <span class="token string">'tiempo_simulacion'</span><span class="token punctuation">:</span> self<span class="token punctuation">.</span>tiempo_simulacion<span class="token punctuation">,</span>
            <span class="token string">'temperatura_medida'</span><span class="token punctuation">:</span> temp<span class="token punctuation">,</span>
            <span class="token string">'senal_4_20mA'</span><span class="token punctuation">:</span> señal<span class="token punctuation">,</span>
            <span class="token string">'senal_control'</span><span class="token punctuation">:</span> control<span class="token punctuation">,</span>
            <span class="token string">'potencia_actuador'</span><span class="token punctuation">:</span> potencia<span class="token punctuation">,</span>
            <span class="token string">'setpoint'</span><span class="token punctuation">:</span> self<span class="token punctuation">.</span>setpoint<span class="token punctuation">,</span>
            <span class="token string">'error'</span><span class="token punctuation">:</span> self<span class="token punctuation">.</span>setpoint <span class="token operator">-</span> temp
        <span class="token punctuation">}</span>
        self<span class="token punctuation">.</span>historial<span class="token punctuation">.</span>append<span class="token punctuation">(</span>registro<span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>tiempo_simulacion <span class="token operator">+=</span> <span class="token number">1</span>

<span class="token keyword">class</span> <span class="token class-name">SensorTemperatura</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""Simula un sensor de temperatura RTD Pt100"""</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>deriva <span class="token operator">=</span> <span class="token number">0.0</span>  <span class="token comment"># Deriva del sensor</span>
        self<span class="token punctuation">.</span>ruido <span class="token operator">=</span> <span class="token number">0.2</span>   <span class="token comment"># Desviación estándar del ruido</span>
    
    <span class="token keyword">def</span> <span class="token function">medir</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temperatura_real<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""Simula la medición de temperatura con errores"""</span>
        <span class="token comment"># Error sistemático (deriva)</span>
        error_sistematico <span class="token operator">=</span> self<span class="token punctuation">.</span>deriva <span class="token operator">*</span> temperatura_real <span class="token operator">/</span> <span class="token number">100</span>
        
        <span class="token comment"># Error aleatorio (ruido)</span>
        error_aleatorio <span class="token operator">=</span> np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>normal<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> self<span class="token punctuation">.</span>ruido<span class="token punctuation">)</span>
        
        <span class="token comment"># Temperatura medida</span>
        temp_medida <span class="token operator">=</span> temperatura_real <span class="token operator">+</span> error_sistematico <span class="token operator">+</span> error_aleatorio
        
        <span class="token keyword">return</span> temp_medida

<span class="token keyword">class</span> <span class="token class-name">Transmisor4_20mA</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""Simula un transmisor 4-20 mA"""</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> rango_min<span class="token operator">=</span><span class="token number">0</span><span class="token punctuation">,</span> rango_max<span class="token operator">=</span><span class="token number">100</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>rango_min <span class="token operator">=</span> rango_min
        self<span class="token punctuation">.</span>rango_max <span class="token operator">=</span> rango_max
    
    <span class="token keyword">def</span> <span class="token function">convertir</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temperatura<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""Convierte temperatura a señal 4-20 mA"""</span>
        <span class="token keyword">if</span> temperatura <span class="token operator">&lt;=</span> self<span class="token punctuation">.</span>rango_min<span class="token punctuation">:</span>
            <span class="token keyword">return</span> <span class="token number">4.0</span>
        <span class="token keyword">elif</span> temperatura <span class="token operator">&gt;=</span> self<span class="token punctuation">.</span>rango_max<span class="token punctuation">:</span>
            <span class="token keyword">return</span> <span class="token number">20.0</span>
        <span class="token keyword">else</span><span class="token punctuation">:</span>
            <span class="token comment"># Conversión lineal</span>
            span <span class="token operator">=</span> self<span class="token punctuation">.</span>rango_max <span class="token operator">-</span> self<span class="token punctuation">.</span>rango_min
            mA <span class="token operator">=</span> <span class="token number">4.0</span> <span class="token operator">+</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>temperatura <span class="token operator">-</span> self<span class="token punctuation">.</span>rango_min<span class="token punctuation">)</span> <span class="token operator">/</span> span<span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">16.0</span>
            <span class="token keyword">return</span> <span class="token builtin">round</span><span class="token punctuation">(</span>mA<span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span>

<span class="token keyword">class</span> <span class="token class-name">PIDController</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""
    Controlador PID con anti-windup y limitaciones
    """</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> Kp<span class="token operator">=</span><span class="token number">2.0</span><span class="token punctuation">,</span> Ki<span class="token operator">=</span><span class="token number">0.1</span><span class="token punctuation">,</span> Kd<span class="token operator">=</span><span class="token number">1.0</span><span class="token punctuation">,</span> setpoint<span class="token operator">=</span><span class="token number">80.0</span><span class="token punctuation">,</span> output_limits<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">100</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>Kp <span class="token operator">=</span> Kp
        self<span class="token punctuation">.</span>Ki <span class="token operator">=</span> Ki
        self<span class="token punctuation">.</span>Kd <span class="token operator">=</span> Kd
        self<span class="token punctuation">.</span>setpoint <span class="token operator">=</span> setpoint
        self<span class="token punctuation">.</span>output_limits <span class="token operator">=</span> output_limits
        
        self<span class="token punctuation">.</span>previous_error <span class="token operator">=</span> <span class="token number">0.0</span>
        self<span class="token punctuation">.</span>integral <span class="token operator">=</span> <span class="token number">0.0</span>
        self<span class="token punctuation">.</span>derivative <span class="token operator">=</span> <span class="token number">0.0</span>
        self<span class="token punctuation">.</span>last_time <span class="token operator">=</span> <span class="token boolean">None</span>
        
        <span class="token comment"># Anti-windup</span>
        self<span class="token punctuation">.</span>integral_limit <span class="token operator">=</span> <span class="token number">50.0</span>
        
    <span class="token keyword">def</span> <span class="token function">update</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> current_value<span class="token punctuation">,</span> current_time<span class="token operator">=</span><span class="token boolean">None</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Calcula la acción de control PID
        """</span>
        <span class="token keyword">if</span> current_time <span class="token keyword">is</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
            current_time <span class="token operator">=</span> datetime<span class="token punctuation">.</span>now<span class="token punctuation">(</span><span class="token punctuation">)</span>
            
        error <span class="token operator">=</span> self<span class="token punctuation">.</span>setpoint <span class="token operator">-</span> current_value
        
        <span class="token comment"># Tiempo delta (para derivada e integral)</span>
        <span class="token keyword">if</span> self<span class="token punctuation">.</span>last_time <span class="token keyword">is</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
            dt <span class="token operator">=</span> <span class="token number">1.0</span>
        <span class="token keyword">else</span><span class="token punctuation">:</span>
            dt <span class="token operator">=</span> <span class="token punctuation">(</span>current_time <span class="token operator">-</span> self<span class="token punctuation">.</span>last_time<span class="token punctuation">)</span><span class="token punctuation">.</span>total_seconds<span class="token punctuation">(</span><span class="token punctuation">)</span>
        
        <span class="token comment"># Término proporcional</span>
        P <span class="token operator">=</span> self<span class="token punctuation">.</span>Kp <span class="token operator">*</span> error
        
        <span class="token comment"># Término integral con anti-windup</span>
        self<span class="token punctuation">.</span>integral <span class="token operator">+=</span> error <span class="token operator">*</span> dt
        <span class="token comment"># Limitar integral para prevenir windup</span>
        self<span class="token punctuation">.</span>integral <span class="token operator">=</span> <span class="token builtin">max</span><span class="token punctuation">(</span><span class="token operator">-</span>self<span class="token punctuation">.</span>integral_limit<span class="token punctuation">,</span> <span class="token builtin">min</span><span class="token punctuation">(</span>self<span class="token punctuation">.</span>integral_limit<span class="token punctuation">,</span> self<span class="token punctuation">.</span>integral<span class="token punctuation">)</span><span class="token punctuation">)</span>
        I <span class="token operator">=</span> self<span class="token punctuation">.</span>Ki <span class="token operator">*</span> self<span class="token punctuation">.</span>integral
        
        <span class="token comment"># Término derivativo</span>
        <span class="token keyword">if</span> dt <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">:</span>
            self<span class="token punctuation">.</span>derivative <span class="token operator">=</span> <span class="token punctuation">(</span>error <span class="token operator">-</span> self<span class="token punctuation">.</span>previous_error<span class="token punctuation">)</span> <span class="token operator">/</span> dt
        D <span class="token operator">=</span> self<span class="token punctuation">.</span>Kd <span class="token operator">*</span> self<span class="token punctuation">.</span>derivative
        
        <span class="token comment"># Salida del controlador</span>
        output <span class="token operator">=</span> P <span class="token operator">+</span> I <span class="token operator">+</span> D
        
        <span class="token comment"># Aplicar límites de salida</span>
        output <span class="token operator">=</span> <span class="token builtin">max</span><span class="token punctuation">(</span>self<span class="token punctuation">.</span>output_limits<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token builtin">min</span><span class="token punctuation">(</span>self<span class="token punctuation">.</span>output_limits<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">,</span> output<span class="token punctuation">)</span><span class="token punctuation">)</span>
        
        <span class="token comment"># Actualizar estados para siguiente iteración</span>
        self<span class="token punctuation">.</span>previous_error <span class="token operator">=</span> error
        self<span class="token punctuation">.</span>last_time <span class="token operator">=</span> current_time
        
        <span class="token keyword">return</span> output

<span class="token keyword">class</span> <span class="token class-name">ActuadorCalefactor</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""
    Simula un actuador de calefacción industrial
    """</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> potencia_max_kw<span class="token operator">=</span><span class="token number">10</span><span class="token punctuation">,</span> tiempo_respuesta<span class="token operator">=</span><span class="token number">30</span><span class="token punctuation">,</span> eficiencia<span class="token operator">=</span><span class="token number">0.85</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>potencia_max <span class="token operator">=</span> potencia_max_kw
        self<span class="token punctuation">.</span>tiempo_respuesta <span class="token operator">=</span> tiempo_respuesta  <span class="token comment"># segundos para respuesta completa</span>
        self<span class="token punctuation">.</span>eficiencia <span class="token operator">=</span> eficiencia
        self<span class="token punctuation">.</span>potencia_actual <span class="token operator">=</span> <span class="token number">0.0</span>
        self<span class="token punctuation">.</span>historial_potencia <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        
    <span class="token keyword">def</span> <span class="token function">set_potencia</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> señal_control<span class="token punctuation">,</span> dt<span class="token operator">=</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Convierte señal de control (0-100%) a potencia real
        Considera tiempo de respuesta y eficiencia
        """</span>
        <span class="token comment"># Limitación de rango</span>
        señal_control <span class="token operator">=</span> <span class="token builtin">max</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token builtin">min</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">,</span> señal_control<span class="token punctuation">)</span><span class="token punctuation">)</span>
        
        <span class="token comment"># Simulación de dinámica de primer orden</span>
        tau <span class="token operator">=</span> self<span class="token punctuation">.</span>tiempo_respuesta  <span class="token comment"># constante de tiempo</span>
        potencia_deseada <span class="token operator">=</span> <span class="token punctuation">(</span>señal_control <span class="token operator">/</span> <span class="token number">100</span><span class="token punctuation">)</span> <span class="token operator">*</span> self<span class="token punctuation">.</span>potencia_max
        
        <span class="token comment"># Ecuación diferencial: dp/dt = (Pdeseada - Pactual) / tau</span>
        self<span class="token punctuation">.</span>potencia_actual <span class="token operator">+=</span> <span class="token punctuation">(</span>potencia_deseada <span class="token operator">-</span> self<span class="token punctuation">.</span>potencia_actual<span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token punctuation">(</span>dt <span class="token operator">/</span> tau<span class="token punctuation">)</span>
        
        <span class="token comment"># Aplicar eficiencia</span>
        potencia_real <span class="token operator">=</span> self<span class="token punctuation">.</span>potencia_actual <span class="token operator">*</span> self<span class="token punctuation">.</span>eficiencia
        
        self<span class="token punctuation">.</span>historial_potencia<span class="token punctuation">.</span>append<span class="token punctuation">(</span><span class="token punctuation">{</span>
            <span class="token string">'timestamp'</span><span class="token punctuation">:</span> datetime<span class="token punctuation">.</span>now<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
            <span class="token string">'senal_control'</span><span class="token punctuation">:</span> señal_control<span class="token punctuation">,</span>
            <span class="token string">'potencia_deseada'</span><span class="token punctuation">:</span> potencia_deseada<span class="token punctuation">,</span>
            <span class="token string">'potencia_real'</span><span class="token punctuation">:</span> potencia_real
        <span class="token punctuation">}</span><span class="token punctuation">)</span>
        
        <span class="token keyword">return</span> potencia_real

<span class="token keyword">class</span> <span class="token class-name">SistemaCalibracion</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""
    Sistema de calibración para sensor de temperatura
    """</span>
    
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>patrones_calibracion <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        self<span class="token punctuation">.</span>curva_calibracion <span class="token operator">=</span> <span class="token boolean">None</span>
        self<span class="token punctuation">.</span>incertidumbre <span class="token operator">=</span> <span class="token number">0.0</span>
        
    <span class="token keyword">def</span> <span class="token function">generar_patrones</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temp_min<span class="token operator">=</span><span class="token number">0</span><span class="token punctuation">,</span> temp_max<span class="token operator">=</span><span class="token number">100</span><span class="token punctuation">,</span> num_puntos<span class="token operator">=</span><span class="token number">6</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Genera puntos de calibración con patrón de referencia
        """</span>
        temperaturas_reales <span class="token operator">=</span> np<span class="token punctuation">.</span>linspace<span class="token punctuation">(</span>temp_min<span class="token punctuation">,</span> temp_max<span class="token punctuation">,</span> num_puntos<span class="token punctuation">)</span>
        
        <span class="token keyword">for</span> temp_real <span class="token keyword">in</span> temperaturas_reales<span class="token punctuation">:</span>
            <span class="token comment"># Simular medición del sensor con error</span>
            temp_medida <span class="token operator">=</span> temp_real <span class="token operator">+</span> np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>normal<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0.5</span><span class="token punctuation">)</span>  <span class="token comment"># Error aleatorio</span>
            <span class="token comment"># Deriva del sensor (error sistemático)</span>
            deriva <span class="token operator">=</span> <span class="token number">0.02</span> <span class="token operator">*</span> temp_real  <span class="token comment"># 2% de deriva</span>
            
            temp_medida_con_deriva <span class="token operator">=</span> temp_medida <span class="token operator">+</span> deriva
            
            self<span class="token punctuation">.</span>patrones_calibracion<span class="token punctuation">.</span>append<span class="token punctuation">(</span><span class="token punctuation">{</span>
                <span class="token string">'temperatura_real'</span><span class="token punctuation">:</span> temp_real<span class="token punctuation">,</span>
                <span class="token string">'temperatura_medida'</span><span class="token punctuation">:</span> temp_medida_con_deriva<span class="token punctuation">,</span>
                <span class="token string">'incertidumbre_patron'</span><span class="token punctuation">:</span> <span class="token number">0.1</span>  <span class="token comment"># Incertidumbre del patrón</span>
            <span class="token punctuation">}</span><span class="token punctuation">)</span>
        
        <span class="token keyword">return</span> self<span class="token punctuation">.</span>patrones_calibracion
    
    <span class="token keyword">def</span> <span class="token function">calcular_curva_calibracion</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Calcula curva de calibración por regresión lineal
        """</span>
        <span class="token keyword">if</span> <span class="token operator">not</span> self<span class="token punctuation">.</span>patrones_calibracion<span class="token punctuation">:</span>
            <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Primero generar patrones de calibración"</span><span class="token punctuation">)</span>
            <span class="token keyword">return</span> <span class="token boolean">None</span>
            
        temps_reales <span class="token operator">=</span> <span class="token punctuation">[</span>p<span class="token punctuation">[</span><span class="token string">'temperatura_real'</span><span class="token punctuation">]</span> <span class="token keyword">for</span> p <span class="token keyword">in</span> self<span class="token punctuation">.</span>patrones_calibracion<span class="token punctuation">]</span>
        temps_medidas <span class="token operator">=</span> <span class="token punctuation">[</span>p<span class="token punctuation">[</span><span class="token string">'temperatura_medida'</span><span class="token punctuation">]</span> <span class="token keyword">for</span> p <span class="token keyword">in</span> self<span class="token punctuation">.</span>patrones_calibracion<span class="token punctuation">]</span>
        
        <span class="token comment"># Regresión lineal: T_real = m * T_medida + b</span>
        coeficientes <span class="token operator">=</span> np<span class="token punctuation">.</span>polyfit<span class="token punctuation">(</span>temps_medidas<span class="token punctuation">,</span> temps_reales<span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>curva_calibracion <span class="token operator">=</span> <span class="token punctuation">{</span>
            <span class="token string">'pendiente'</span><span class="token punctuation">:</span> coeficientes<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
            <span class="token string">'intercepto'</span><span class="token punctuation">:</span> coeficientes<span class="token punctuation">[</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
            <span class="token string">'r_cuadrado'</span><span class="token punctuation">:</span> np<span class="token punctuation">.</span>corrcoef<span class="token punctuation">(</span>temps_medidas<span class="token punctuation">,</span> temps_reales<span class="token punctuation">)</span><span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">]</span><span class="token operator">**</span><span class="token number">2</span>
        <span class="token punctuation">}</span>
        
        <span class="token comment"># Calcular incertidumbre</span>
        residuals <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        <span class="token keyword">for</span> i<span class="token punctuation">,</span> temp_med <span class="token keyword">in</span> <span class="token builtin">enumerate</span><span class="token punctuation">(</span>temps_medidas<span class="token punctuation">)</span><span class="token punctuation">:</span>
            temp_corregida <span class="token operator">=</span> self<span class="token punctuation">.</span>corregir_temperatura<span class="token punctuation">(</span>temp_med<span class="token punctuation">)</span>
            residual <span class="token operator">=</span> temps_reales<span class="token punctuation">[</span>i<span class="token punctuation">]</span> <span class="token operator">-</span> temp_corregida
            residuals<span class="token punctuation">.</span>append<span class="token punctuation">(</span>residual<span class="token punctuation">)</span>
        
        self<span class="token punctuation">.</span>incertidumbre <span class="token operator">=</span> np<span class="token punctuation">.</span>std<span class="token punctuation">(</span>residuals<span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">2</span>  <span class="token comment"># Incertidumbre expandida (k=2)</span>
        
        <span class="token keyword">return</span> self<span class="token punctuation">.</span>curva_calibracion
    
    <span class="token keyword">def</span> <span class="token function">corregir_temperatura</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temperatura_medida<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Aplica corrección de calibración a medición
        """</span>
        <span class="token keyword">if</span> self<span class="token punctuation">.</span>curva_calibracion <span class="token keyword">is</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
            <span class="token keyword">return</span> temperatura_medida
            
        m <span class="token operator">=</span> self<span class="token punctuation">.</span>curva_calibracion<span class="token punctuation">[</span><span class="token string">'pendiente'</span><span class="token punctuation">]</span>
        b <span class="token operator">=</span> self<span class="token punctuation">.</span>curva_calibracion<span class="token punctuation">[</span><span class="token string">'intercepto'</span><span class="token punctuation">]</span>
        
        <span class="token keyword">return</span> m <span class="token operator">*</span> temperatura_medida <span class="token operator">+</span> b
    
    <span class="token keyword">def</span> <span class="token function">generar_certificado_calibracion</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token triple-quoted-string string">"""
        Genera certificado de calibración formal
        """</span>
        <span class="token keyword">if</span> self<span class="token punctuation">.</span>curva_calibracion <span class="token keyword">is</span> <span class="token boolean">None</span><span class="token punctuation">:</span>
            <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Primero calcular curva de calibración"</span><span class="token punctuation">)</span>
            <span class="token keyword">return</span>
            
        <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"=== CERTIFICADO DE CALIBRACIÓN ==="</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Fecha: {datetime.now().strftime('%Y-%m-%d %H:%M')}"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Equipo calibrado: Sensor de Temperatura RTD"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Rango de calibración: 0°C a 100°C"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Ecuación de corrección: T_real = {self.curva_calibracion['pendiente']:.4f} * T_medida + {self.curva_calibracion['intercepto']:.4f}"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Coeficiente de determinación (R²): {self.curva_calibracion['r_cuadrado']:.4f}"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Incertidumbre expandida (k=2): ±{self.incertidumbre:.2f}°C"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Trazabilidad: Patrón nacional de temperatura"</span><span class="token punctuation">)</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"====================================="</span><span class="token punctuation">)</span>

<span class="token keyword">def</span> <span class="token function">demostracion_completa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token triple-quoted-string string">"""Demostración completa del sistema de instrumentación"""</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"=== SISTEMA COMPLETO DE INSTRUMENTACIÓN INDUSTRIAL ==="</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Inicializando componentes..."</span><span class="token punctuation">)</span>
    
    <span class="token comment"># Crear sistema completo</span>
    sistema <span class="token operator">=</span> SistemaInstrumentacionCompleto<span class="token punctuation">(</span><span class="token punctuation">)</span>
    
    <span class="token comment"># Ejecutar simulación</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"Ejecutando simulación de control..."</span><span class="token punctuation">)</span>
    <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span><span class="token number">300</span><span class="token punctuation">)</span><span class="token punctuation">:</span>  <span class="token comment"># 5 minutos de simulación</span>
        resultado <span class="token operator">=</span> sistema<span class="token punctuation">.</span>ejecutar_ciclo_control<span class="token punctuation">(</span><span class="token punctuation">)</span>
        
        <span class="token keyword">if</span> i <span class="token operator">%</span> <span class="token number">30</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">:</span>  <span class="token comment"># Mostrar cada 30 segundos</span>
            <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"T: {i}s - Temp: {resultado['temperatura']:.1f}°C - "</span>
                  f<span class="token string">"Control: {resultado['control']:.1f}% - "</span>
                  f<span class="token string">"mA: {resultado['senal_4_20mA']:.1f}mA"</span><span class="token punctuation">)</span>
    
    <span class="token comment"># Análisis de resultados</span>
    df <span class="token operator">=</span> pd<span class="token punctuation">.</span>DataFrame<span class="token punctuation">(</span>sistema<span class="token punctuation">.</span>historial<span class="token punctuation">)</span>
    
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n=== ANÁLISIS DE RESULTADOS ==="</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Temperatura final: {df['temperatura_medida'].iloc[-1]:.1f}°C"</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Setpoint: {sistema.setpoint}°C"</span><span class="token punctuation">)</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"Error estacionario: {df['error'].iloc[-50:].mean():.2f}°C"</span><span class="token punctuation">)</span>
    
    <span class="token comment"># Gráficas</span>
    plt<span class="token punctuation">.</span>figure<span class="token punctuation">(</span>figsize<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">15</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
    
    plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'tiempo_simulacion'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> df<span class="token punctuation">[</span><span class="token string">'temperatura_medida'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token string">'b-'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Temperatura'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'tiempo_simulacion'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> df<span class="token punctuation">[</span><span class="token string">'setpoint'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token string">'r--'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Setpoint'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>ylabel<span class="token punctuation">(</span><span class="token string">'Temperatura (°C)'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>title<span class="token punctuation">(</span><span class="token string">'Respuesta del Sistema de Control'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>legend<span class="token punctuation">(</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">)</span>
    
    plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'tiempo_simulacion'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> df<span class="token punctuation">[</span><span class="token string">'senal_control'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token string">'g-'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Señal Control'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>ylabel<span class="token punctuation">(</span><span class="token string">'Control (%)'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>legend<span class="token punctuation">(</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">)</span>
    
    plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>df<span class="token punctuation">[</span><span class="token string">'tiempo_simulacion'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> df<span class="token punctuation">[</span><span class="token string">'senal_4_20mA'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> <span class="token string">'m-'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Señal 4-20 mA'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>ylabel<span class="token punctuation">(</span><span class="token string">'Corriente (mA)'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>xlabel<span class="token punctuation">(</span><span class="token string">'Tiempo (s)'</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>legend<span class="token punctuation">(</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">)</span>
    
    plt<span class="token punctuation">.</span>tight_layout<span class="token punctuation">(</span><span class="token punctuation">)</span>
    plt<span class="token punctuation">.</span>show<span class="token punctuation">(</span><span class="token punctuation">)</span>
    
    <span class="token comment"># Demostración de calibración</span>
    <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n=== DEMOSTRACIÓN DE CALIBRACIÓN ==="</span><span class="token punctuation">)</span>
    sistema<span class="token punctuation">.</span>calibrador<span class="token punctuation">.</span>generar_patrones<span class="token punctuation">(</span><span class="token punctuation">)</span>
    sistema<span class="token punctuation">.</span>calibrador<span class="token punctuation">.</span>calcular_curva_calibracion<span class="token punctuation">(</span><span class="token punctuation">)</span>
    sistema<span class="token punctuation">.</span>calibrador<span class="token punctuation">.</span>generar_certificado_calibracion<span class="token punctuation">(</span><span class="token punctuation">)</span>
    
    <span class="token keyword">return</span> sistema

<span class="token comment"># Ejecutar demostración</span>
<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span class="token punctuation">:</span>
    sistema <span class="token operator">=</span> demostracion_completa<span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre>
<h2 id="flujo-de-información-completo-del-sistema">7.2 Flujo de Información Completo del Sistema</h2>
<pre class=" language-mermaid"><svg id="mermaid-svg-zTbYlwg7ktdMVgGU" width="100%" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" height="546.2954711914062" style="max-width: 516.7102661132812px;" viewBox="0 0.0000019073486328125 516.7102661132812 546.2954711914062"><style>#mermaid-svg-zTbYlwg7ktdMVgGU{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;fill:#000000;}#mermaid-svg-zTbYlwg7ktdMVgGU .error-icon{fill:#552222;}#mermaid-svg-zTbYlwg7ktdMVgGU .error-text{fill:#552222;stroke:#552222;}#mermaid-svg-zTbYlwg7ktdMVgGU .edge-thickness-normal{stroke-width:2px;}#mermaid-svg-zTbYlwg7ktdMVgGU .edge-thickness-thick{stroke-width:3.5px;}#mermaid-svg-zTbYlwg7ktdMVgGU .edge-pattern-solid{stroke-dasharray:0;}#mermaid-svg-zTbYlwg7ktdMVgGU .edge-pattern-dashed{stroke-dasharray:3;}#mermaid-svg-zTbYlwg7ktdMVgGU .edge-pattern-dotted{stroke-dasharray:2;}#mermaid-svg-zTbYlwg7ktdMVgGU .marker{fill:#666;stroke:#666;}#mermaid-svg-zTbYlwg7ktdMVgGU .marker.cross{stroke:#666;}#mermaid-svg-zTbYlwg7ktdMVgGU svg{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;}#mermaid-svg-zTbYlwg7ktdMVgGU .label{font-family:"trebuchet ms",verdana,arial,sans-serif;color:#000000;}#mermaid-svg-zTbYlwg7ktdMVgGU .cluster-label text{fill:#333;}#mermaid-svg-zTbYlwg7ktdMVgGU .cluster-label span{color:#333;}#mermaid-svg-zTbYlwg7ktdMVgGU .label text,#mermaid-svg-zTbYlwg7ktdMVgGU span{fill:#000000;color:#000000;}#mermaid-svg-zTbYlwg7ktdMVgGU .node rect,#mermaid-svg-zTbYlwg7ktdMVgGU .node circle,#mermaid-svg-zTbYlwg7ktdMVgGU .node ellipse,#mermaid-svg-zTbYlwg7ktdMVgGU .node polygon,#mermaid-svg-zTbYlwg7ktdMVgGU .node path{fill:#eee;stroke:#999;stroke-width:1px;}#mermaid-svg-zTbYlwg7ktdMVgGU .node .label{text-align:center;}#mermaid-svg-zTbYlwg7ktdMVgGU .node.clickable{cursor:pointer;}#mermaid-svg-zTbYlwg7ktdMVgGU .arrowheadPath{fill:#333333;}#mermaid-svg-zTbYlwg7ktdMVgGU .edgePath .path{stroke:#666;stroke-width:1.5px;}#mermaid-svg-zTbYlwg7ktdMVgGU .flowchart-link{stroke:#666;fill:none;}#mermaid-svg-zTbYlwg7ktdMVgGU .edgeLabel{background-color:white;text-align:center;}#mermaid-svg-zTbYlwg7ktdMVgGU .edgeLabel rect{opacity:0.5;background-color:white;fill:white;}#mermaid-svg-zTbYlwg7ktdMVgGU .cluster rect{fill:hsl(210,66.6666666667%,95%);stroke:#26a;stroke-width:1px;}#mermaid-svg-zTbYlwg7ktdMVgGU .cluster text{fill:#333;}#mermaid-svg-zTbYlwg7ktdMVgGU .cluster span{color:#333;}#mermaid-svg-zTbYlwg7ktdMVgGU div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:12px;background:hsl(-160,0%,93.3333333333%);border:1px solid #26a;border-radius:2px;pointer-events:none;z-index:100;}#mermaid-svg-zTbYlwg7ktdMVgGU:root{--mermaid-font-family:"trebuchet ms",verdana,arial,sans-serif;}#mermaid-svg-zTbYlwg7ktdMVgGU flowchart{fill:apa;}</style><g><g class="output"><g class="clusters"></g><g class="edgePaths"><g class="edgePath LS-A LE-B" style="opacity: 1;" id="L-A-B"><path class="path" d="M296.73011779785156,45.759469977153145L459.1931838989258,79.71590805053711L459.1931838989258,104.71590805053711" marker-end="url(https://stackedit.io/app#arrowhead28)" style="fill:none"></path><defs><marker id="arrowhead28" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-B LE-C" style="opacity: 1;" id="L-B-C"><path class="path" d="M459.1931838989258,151.43181610107422L459.1931838989258,176.43181610107422L412.6695665436065,201.43181610107422" marker-end="url(https://stackedit.io/app#arrowhead29)" style="fill:none"></path><defs><marker id="arrowhead29" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-C LE-D" style="opacity: 1;" id="L-C-D"><path class="path" d="M369.2017059326172,248.14772415161133L369.2017059326172,273.1477241516113L322.3388217424888,298.1477241516113" marker-end="url(https://stackedit.io/app#arrowhead30)" style="fill:none"></path><defs><marker id="arrowhead30" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-D LE-E" style="opacity: 1;" id="L-D-E"><path class="path" d="M212.09943389892578,344.83927045099375L140.8295440673828,369.86363220214844L114.60465870147961,394.86363220214844" marker-end="url(https://stackedit.io/app#arrowhead31)" style="fill:none"></path><defs><marker id="arrowhead31" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-E LE-A" style="opacity: 1;" id="L-E-A"><path class="path" d="M85.27205237364059,394.86363220214844L80.1022720336914,369.86363220214844L80.1022720336914,321.5056781768799L80.1022720336914,273.1477241516113L80.1022720336914,224.78977012634277L80.1022720336914,176.43181610107422L80.1022720336914,128.07386207580566L80.1022720336914,79.71590805053711L158.9232940673828,53.913654089368634" marker-end="url(https://stackedit.io/app#arrowhead32)" style="fill:none"></path><defs><marker id="arrowhead32" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-F LE-C" style="opacity: 1;" id="L-F-C"><path class="path" d="M279.2102279663086,151.43181610107422L279.2102279663086,176.43181610107422L325.7338453216279,201.43181610107422" marker-end="url(https://stackedit.io/app#arrowhead33)" style="fill:none"></path><defs><marker id="arrowhead33" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-G LE-D" style="opacity: 1;" id="L-G-D"><path class="path" d="M175.2045440673828,248.14772415161133L175.2045440673828,273.1477241516113L228.63393121893728,298.1477241516113" marker-end="url(https://stackedit.io/app#arrowhead34)" style="fill:none"></path><defs><marker id="arrowhead34" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-D LE-H" style="opacity: 1;" id="L-D-H"><path class="path" d="M300.69477169361164,344.86363220214844L324.39204597473145,369.86363220214844L324.39204597473145,394.86363220214844" marker-end="url(https://stackedit.io/app#arrowhead35)" style="fill:none"></path><defs><marker id="arrowhead35" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g><g class="edgePath LS-H LE-I" style="opacity: 1;" id="L-H-I"><path class="path" d="M324.39204597473145,441.57954025268555L324.39204597473145,466.57954025268555L324.39204597473145,491.57954025268555" marker-end="url(https://stackedit.io/app#arrowhead36)" style="fill:none"></path><defs><marker id="arrowhead36" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1; stroke-dasharray: 1, 0;"></path></marker></defs></g></g><g class="edgeLabels"><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-A-B" class="edgeLabel L-LS-A' L-LE-B"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-B-C" class="edgeLabel L-LS-B' L-LE-C"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-C-D" class="edgeLabel L-LS-C' L-LE-D"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-D-E" class="edgeLabel L-LS-D' L-LE-E"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-E-A" class="edgeLabel L-LS-E' L-LE-A"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-F-C" class="edgeLabel L-LS-F' L-LE-C"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-G-D" class="edgeLabel L-LS-G' L-LE-D"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-D-H" class="edgeLabel L-LS-D' L-LE-H"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-H-I" class="edgeLabel L-LS-H' L-LE-I"></span></div></foreignObject></g></g></g><g class="nodes"><g class="node default" style="opacity: 1;" id="flowchart-A-126" transform="translate(227.8267059326172,31.357954025268555)"><rect rx="0" ry="0" x="-68.90341186523438" y="-23.35795497894287" width="137.80682373046875" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-58.903411865234375,-13.357954978942871)"><foreignObject width="117.80682373046875" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Proceso Térmico</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-B-127" transform="translate(459.1931838989258,128.07386207580566)"><rect rx="0" ry="0" x="-49.51704788208008" y="-23.35795497894287" width="99.03409576416016" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-39.51704788208008,-13.357954978942871)"><foreignObject width="79.03409576416016" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Sensor RTD</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-C-129" transform="translate(369.2017059326172,224.78977012634277)"><rect rx="0" ry="0" x="-77.54545593261719" y="-23.35795497894287" width="155.09091186523438" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-67.54545593261719,-13.357954978942871)"><foreignObject width="135.09091186523438" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Transmisor 4-20mA</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-D-131" transform="translate(278.5539779663086,321.5056781768799)"><rect rx="0" ry="0" x="-66.45454788208008" y="-23.35795497894287" width="132.90909576416016" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-56.45454788208008,-13.357954978942871)"><foreignObject width="112.90909576416016" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Controlador PID</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-E-133" transform="translate(90.1022720336914,418.221586227417)"><rect rx="0" ry="0" x="-82.1022720336914" y="-23.35795497894287" width="164.2045440673828" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-72.1022720336914,-13.357954978942871)"><foreignObject width="144.2045440673828" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Actuador Calefactor</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-F-136" transform="translate(279.2102279663086,128.07386207580566)"><rect rx="0" ry="0" x="-80.46591186523438" y="-23.35795497894287" width="160.93182373046875" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-70.46591186523438,-13.357954978942871)"><foreignObject width="140.93182373046875" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Sistema Calibración</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-G-138" transform="translate(175.2045440673828,224.78977012634277)"><rect rx="0" ry="0" x="-53.75" y="-23.35795497894287" width="107.5" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-43.75,-13.357954978942871)"><foreignObject width="87.5" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Interfaz HMI</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-H-141" transform="translate(324.39204597473145,418.221586227417)"><rect rx="0" ry="0" x="-61.028411865234375" y="-23.35795497894287" width="122.05682373046875" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-51.028411865234375,-13.357954978942871)"><foreignObject width="102.05682373046875" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Registro Datos</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-I-143" transform="translate(324.39204597473145,514.9374942779541)"><rect rx="0" ry="0" x="-80.1022720336914" y="-23.35795497894287" width="160.2045440673828" height="46.71590995788574" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-70.1022720336914,-13.357954978942871)"><foreignObject width="140.2045440673828" height="26.715909957885742"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Análisis Desempeño</div></foreignObject></g></g></g></g></g></g></svg></pre>
<hr>
<h1 id="🎯-8.-evaluación-y-rúbrica-del-proyecto">🎯 8. EVALUACIÓN Y RÚBRICA DEL PROYECTO</h1>
<h2 id="criterios-de-evaluación">8.1 Criterios de Evaluación</h2>

<table>
<thead>
<tr>
<th>Categoría</th>
<th>Ponderación</th>
<th>Elementos Evaluados</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Funcionalidad del Sistema</strong></td>
<td>30%</td>
<td>Operación correcta del sistema integrado</td>
</tr>
<tr>
<td><strong>Exactitud y Precisión</strong></td>
<td>25%</td>
<td>Precisión en control y calibración</td>
</tr>
<tr>
<td><strong>Documentación Técnica</strong></td>
<td>20%</td>
<td>Reporte técnico y certificados</td>
</tr>
<tr>
<td><strong>Análisis de Resultados</strong></td>
<td>15%</td>
<td>Interpretación de resultados</td>
</tr>
<tr>
<td><strong>Innovación y Mejoras</strong></td>
<td>10%</td>
<td>Mejoras e innovaciones propuestas</td>
</tr>
</tbody>
</table><h2 id="entregables-requeridos">8.2 Entregables Requeridos</h2>
<ol>
<li><strong>Código completo</strong> del sistema integrado</li>
<li><strong>Dataset completo</strong> de variables del proceso</li>
<li><strong>Certificado de calibración</strong> generado</li>
<li><strong>Reporte técnico</strong> con análisis de resultados</li>
<li><strong>Presentación ejecutiva</strong> de funcionamiento del sistema</li>
</ol>
<hr>
<h1 id="🔬-9.-aplicaciones-industriales-y-extensiones">🔬 9. APLICACIONES INDUSTRIALES Y EXTENSIONES</h1>
<h2 id="aplicaciones-industriales-reales">9.1 Aplicaciones Industriales Reales</h2>
<ul>
<li><strong>Control de temperatura</strong> en reactores químicos</li>
<li><strong>Sistemas de pasteurización</strong> en industria alimentaria</li>
<li><strong>Hornos industriales</strong> en manufactura</li>
<li><strong>Sistemas de climatización</strong> en edificios inteligentes</li>
<li><strong>Control de procesos</strong> en industria farmacéutica</li>
</ul>
<h2 id="extensiones-avanzadas">9.2 Extensiones Avanzadas</h2>
<ul>
<li><strong>Control en cascada</strong> para procesos con múltiples variables</li>
<li><strong>Redes de sensores</strong> inalámbricos (WirelessHART)</li>
<li><strong>Predictive maintenance</strong> usando datos históricos</li>
<li><strong>Interfaz HMI</strong> profesional con SCADA</li>
<li><strong>Comunicación OPC-UA</strong> para Industria 4.0</li>
</ul>
<hr>
<h1 id="📚-10.-referencias-bibliográficas-apa-7ma-edición">📚 10. REFERENCIAS BIBLIOGRÁFICAS (APA 7ma Edición)</h1>
<p>Bell, S. (2020). <em>Measurement Good Practice Guide No. 42: Calibration of Temperature and Humidity Sensors</em>. National Physical Laboratory.</p>
<p>Bentley, J. P. (2020). <em>Principles of Measurement Systems</em> (5th ed.). Pearson Education.</p>
<p>Doebelin, E., &amp; Manik, D. (2017). <em>Measurement Systems: Application and Design</em> (7th ed.). McGraw-Hill Education.</p>
<p>Johnson, R. D. (2019). <em>Process Control Instrumentation Technology</em> (10th ed.). Prentice Hall.</p>
<p>National Institute of Standards and Technology. (2019). <em>Guidelines for Evaluating and Expressing the Uncertainty of NIST Measurement Results</em> (NIST Technical Note 1900). U.S. Department of Commerce.</p>
<p>Ogata, K. (2010). <em>Modern Control Engineering</em> (5th ed.). Prentice Hall.</p>
<p>Smith, C. A., &amp; Corripio, A. B. (2006). <em>Principles and Practice of Automatic Process Control</em> (3rd ed.). John Wiley &amp; Sons.</p>
<hr>
<h1 id="🎓-11.-competencias-desarrolladas">🎓 11. COMPETENCIAS DESARROLLADAS</h1>
<p>Al completar este proyecto integrador, el estudiante habrá desarrollado las siguientes competencias:</p>
<h2 id="competencias-técnicas"><strong>Competencias Técnicas</strong></h2>
<ul>
<li>Selección y especificación de instrumentos de medición</li>
<li>Configuración de transmisores y señales estándar</li>
<li>Programación de estrategias de control automático</li>
<li>Operación de actuadores y elementos finales de control</li>
<li>Ejecución de procedimientos de calibración metrológica</li>
</ul>
<h2 id="competencias-analíticas"><strong>Competencias Analíticas</strong></h2>
<ul>
<li>Análisis de desempeño de sistemas de control</li>
<li>Interpretación de curvas de calibración</li>
<li>Cálculo de incertidumbre de medición</li>
<li>Diagnóstico de problemas en instrumentación</li>
</ul>
<h2 id="competencias-profesionales"><strong>Competencias Profesionales</strong></h2>
<ul>
<li>Documentación técnica según normas internacionales</li>
<li>Comunicación efectiva de resultados técnicos</li>
<li>Trabajo en equipo en proyectos de ingeniería</li>
<li>Aplicación de normas de calidad y seguridad</li>
</ul>
<hr>
<p><strong>¡Proyecto integrador completo listo para implementación en el curso de Instrumentación Industrial!</strong> 🎓🔧</p>
<p><em>“La instrumentación es los sentidos y las manos de la automatización industrial”</em></p>
</div>
</body>

</html>
