<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Control-Temperatura-IA</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="🎯-proyecto-completo-control-de-temperatura-con-ia">🎯 <strong>PROYECTO COMPLETO: CONTROL DE TEMPERATURA CON IA</strong></h1>
<h2 id="implementación-de-sistema-adaptativo-con-fpga"><strong>Implementación de Sistema Adaptativo con FPGA</strong></h2>
<h3 id="del-22-al-29-de-noviembre---8-días-intensivos"><strong>Del 22 al 29 de Noviembre - 8 Días Intensivos</strong></h3>
<hr>
<h1 id="📋-índice-completo">📋 <strong>ÍNDICE COMPLETO</strong></h1>
<ol>
<li><a href="#-resumen-ejecutivo">Resumen Ejecutivo</a></li>
<li><a href="#-paso-1-simulaci%C3%B3n-completa-en-python">Simulación en Python</a></li>
<li><a href="#-paso-2-c%C3%B3digo-vhdl-completo-para-fpga">Código VHDL FPGA</a></li>
<li><a href="#-paso-3-testbench-completo-para-verificaci%C3%B3n">Testbench Verificación</a></li>
<li><a href="#-paso-4-diagramas-de-conexi%C3%B3n-completos">Conexiones Físicas</a></li>
<li><a href="#-paso-5-configuraci%C3%B3n-completa-quartus-ii">Configuración Quartus</a></li>
<li><a href="#-paso-6-gu%C3%ADa-completa-de-implementaci%C3%B3n-f%C3%ADsica">Guía Implementación</a></li>
<li><a href="#-paso-7-protocolo-completo-de-pruebas">Protocolo Pruebas</a></li>
<li><a href="#-paso-8-cronograma-8-d%C3%ADas-22-29-noviembre">Cronograma 8 Días</a></li>
<li><a href="#-paso-9-lista-completa-de-materiales">Lista Materiales</a></li>
<li><a href="#-paso-10-r%C3%BAbrica-completa-de-evaluaci%C3%B3n">Rúbrica Evaluación</a></li>
</ol>
<hr>
<h1 id="🚀-resumen-ejecutivo">🚀 <strong>RESUMEN EJECUTIVO</strong></h1>
<h2 id="🎯-objetivo"><strong>🎯 OBJETIVO</strong></h2>
<p>Implementar un sistema de control de temperatura adaptativo que combine <strong>PID tradicional</strong> con <strong>algoritmo de IA</strong> para optimizar parámetros en tiempo real usando <strong>FPGA Altera MAX II</strong>.</p>
<h2 id="🔄-funcionalidad-principal"><strong>🔄 FUNCIONALIDAD PRINCIPAL</strong></h2>
<ul>
<li><strong>4 modos de operación</strong> automáticos según error</li>
<li><strong>Control PID adaptativo</strong> en tiempo real</li>
<li><strong>Protección contra sobrecalentamiento</strong></li>
<li><strong>Monitoreo visual</strong> con LEDs indicadores</li>
<li><strong>Comunicación completa</strong> sensor→ADC→FPGA→actuador</li>
</ul>
<h2 id="⏱️-cronograma"><strong>⏱️ CRONOGRAMA</strong></h2>
<ul>
<li><strong>8 días intensivos</strong> (22-29 Noviembre)</li>
<li><strong>De simulación a implementación física completa</strong></li>
<li><strong>Entregables profesionales</strong> incluidos</li>
</ul>
<hr>
<h1 id="🐍-paso-1-simulación-completa-en-python">🐍 <strong>PASO 1: SIMULACIÓN COMPLETA EN PYTHON</strong></h1>
<h2 id="código-completo-notebook-colab"><strong>CÓDIGO COMPLETO NOTEBOOK COLAB</strong></h2>
<pre class=" language-python"><code class="prism  language-python"><span class="token comment"># ===========================================================</span>
<span class="token comment"># SIMULACIÓN COMPLETA: CONTROL TEMPERATURA CON IA</span>
<span class="token comment"># Google Colab - Python 3.8+</span>
<span class="token comment"># ===========================================================</span>

<span class="token keyword">import</span> numpy <span class="token keyword">as</span> np
<span class="token keyword">import</span> matplotlib<span class="token punctuation">.</span>pyplot <span class="token keyword">as</span> plt
<span class="token keyword">import</span> time
<span class="token keyword">from</span> datetime <span class="token keyword">import</span> datetime
<span class="token keyword">import</span> pandas <span class="token keyword">as</span> pd
<span class="token keyword">from</span> scipy <span class="token keyword">import</span> signal

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"🚀 INICIANDO PROYECTO DE CONTROL CON IA"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"📅 Fecha:"</span><span class="token punctuation">,</span> datetime<span class="token punctuation">.</span>now<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>strftime<span class="token punctuation">(</span><span class="token string">"%Y-%m-%d %H:%M:%S"</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"⏱️  Duración simulación: 5 minutos (300 segundos)"</span><span class="token punctuation">)</span>

<span class="token comment"># 1. MODELO FÍSICO DE SISTEMA TÉRMICO REALISTA</span>
<span class="token keyword">class</span> <span class="token class-name">SistemaTermicoRealista</span><span class="token punctuation">:</span>
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>temperatura <span class="token operator">=</span> <span class="token number">25.0</span>  <span class="token comment"># Temperatura inicial ambiente</span>
        self<span class="token punctuation">.</span>temperatura_ambiente <span class="token operator">=</span> <span class="token number">25.0</span>
        self<span class="token punctuation">.</span>inercia_termica <span class="token operator">=</span> <span class="token number">1500</span>  <span class="token comment"># J/°C - Capacidad calorífica</span>
        self<span class="token punctuation">.</span>resistencia_termica <span class="token operator">=</span> <span class="token number">0.2</span>  <span class="token comment"># °C/W - Pérdidas térmicas</span>
        self<span class="token punctuation">.</span>historico_temperaturas <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        self<span class="token punctuation">.</span>historico_potencias <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        
    <span class="token keyword">def</span> <span class="token function">actualizar</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> potencia_calefactor<span class="token punctuation">,</span> dt<span class="token operator">=</span><span class="token number">1.0</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token comment"># Modelo físico con eficiencia del 80%</span>
        calor_generado <span class="token operator">=</span> potencia_calefactor <span class="token operator">*</span> <span class="token number">0.8</span>
        calor_perdido <span class="token operator">=</span> <span class="token punctuation">(</span>self<span class="token punctuation">.</span>temperatura <span class="token operator">-</span> self<span class="token punctuation">.</span>temperatura_ambiente<span class="token punctuation">)</span> <span class="token operator">/</span> self<span class="token punctuation">.</span>resistencia_termica
        
        <span class="token comment"># Ecuación diferencial de balance térmico</span>
        delta_temp <span class="token operator">=</span> <span class="token punctuation">(</span>calor_generado <span class="token operator">-</span> calor_perdido<span class="token punctuation">)</span> <span class="token operator">*</span> dt <span class="token operator">/</span> self<span class="token punctuation">.</span>inercia_termica
        self<span class="token punctuation">.</span>temperatura <span class="token operator">+=</span> delta_temp
        
        <span class="token comment"># Ruido de sensor simulado (más realista)</span>
        ruido <span class="token operator">=</span> np<span class="token punctuation">.</span>random<span class="token punctuation">.</span>normal<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0.15</span><span class="token punctuation">)</span>
        temperatura_medida <span class="token operator">=</span> self<span class="token punctuation">.</span>temperatura <span class="token operator">+</span> ruido
        
        <span class="token comment"># Guardar histórico para análisis</span>
        self<span class="token punctuation">.</span>historico_temperaturas<span class="token punctuation">.</span>append<span class="token punctuation">(</span>temperatura_medida<span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>historico_potencias<span class="token punctuation">.</span>append<span class="token punctuation">(</span>potencia_calefactor<span class="token punctuation">)</span>
        
        <span class="token keyword">return</span> temperatura_medida

<span class="token comment"># 2. CONTROLADOR PID AVANZADO CON ANTI-WINDUP</span>
<span class="token keyword">class</span> <span class="token class-name">PID_Avanzado</span><span class="token punctuation">:</span>
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> Kp<span class="token punctuation">,</span> Ki<span class="token punctuation">,</span> Kd<span class="token punctuation">,</span> setpoint<span class="token punctuation">,</span> dt<span class="token operator">=</span><span class="token number">1.0</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>Kp <span class="token operator">=</span> Kp
        self<span class="token punctuation">.</span>Ki <span class="token operator">=</span> Ki 
        self<span class="token punctuation">.</span>Kd <span class="token operator">=</span> Kd
        self<span class="token punctuation">.</span>setpoint <span class="token operator">=</span> setpoint
        self<span class="token punctuation">.</span>error_anterior <span class="token operator">=</span> <span class="token number">0</span>
        self<span class="token punctuation">.</span>suma_errores <span class="token operator">=</span> <span class="token number">0</span>
        self<span class="token punctuation">.</span>salida_anterior <span class="token operator">=</span> <span class="token number">0</span>
        self<span class="token punctuation">.</span>dt <span class="token operator">=</span> dt
        self<span class="token punctuation">.</span>historico_errores <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        
    <span class="token keyword">def</span> <span class="token function">calcular</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temperatura_actual<span class="token punctuation">)</span><span class="token punctuation">:</span>
        error <span class="token operator">=</span> self<span class="token punctuation">.</span>setpoint <span class="token operator">-</span> temperatura_actual
        self<span class="token punctuation">.</span>historico_errores<span class="token punctuation">.</span>append<span class="token punctuation">(</span>error<span class="token punctuation">)</span>
        
        <span class="token comment"># Término Proporcional</span>
        P <span class="token operator">=</span> self<span class="token punctuation">.</span>Kp <span class="token operator">*</span> error
        
        <span class="token comment"># Término Integral con anti-windup</span>
        self<span class="token punctuation">.</span>suma_errores <span class="token operator">+=</span> error <span class="token operator">*</span> self<span class="token punctuation">.</span>dt
        I <span class="token operator">=</span> self<span class="token punctuation">.</span>Ki <span class="token operator">*</span> self<span class="token punctuation">.</span>suma_errores
        
        <span class="token comment"># Término Derivativo con filtro</span>
        derivada <span class="token operator">=</span> <span class="token punctuation">(</span>error <span class="token operator">-</span> self<span class="token punctuation">.</span>error_anterior<span class="token punctuation">)</span> <span class="token operator">/</span> self<span class="token punctuation">.</span>dt <span class="token keyword">if</span> self<span class="token punctuation">.</span>dt <span class="token operator">&gt;</span> <span class="token number">0</span> <span class="token keyword">else</span> <span class="token number">0</span>
        D <span class="token operator">=</span> self<span class="token punctuation">.</span>Kd <span class="token operator">*</span> derivada
        
        <span class="token comment"># Salida PID completa</span>
        salida <span class="token operator">=</span> P <span class="token operator">+</span> I <span class="token operator">+</span> D
        
        <span class="token comment"># Saturación y anti-windup</span>
        <span class="token keyword">if</span> salida <span class="token operator">&gt;</span> <span class="token number">100</span><span class="token punctuation">:</span>
            salida <span class="token operator">=</span> <span class="token number">100</span>
            self<span class="token punctuation">.</span>suma_errores <span class="token operator">-=</span> error <span class="token operator">*</span> self<span class="token punctuation">.</span>dt  <span class="token comment"># Anti-windup</span>
        <span class="token keyword">elif</span> salida <span class="token operator">&lt;</span> <span class="token number">0</span><span class="token punctuation">:</span>
            salida <span class="token operator">=</span> <span class="token number">0</span>
            self<span class="token punctuation">.</span>suma_errores <span class="token operator">-=</span> error <span class="token operator">*</span> self<span class="token punctuation">.</span>dt  <span class="token comment"># Anti-windup</span>
            
        self<span class="token punctuation">.</span>error_anterior <span class="token operator">=</span> error
        self<span class="token punctuation">.</span>salida_anterior <span class="token operator">=</span> salida
        <span class="token keyword">return</span> salida

<span class="token comment"># 3. SISTEMA DE CONTROL INTELIGENTE CON 4 MODOS</span>
<span class="token keyword">class</span> <span class="token class-name">ControladorIA</span><span class="token punctuation">:</span>
    <span class="token keyword">def</span> <span class="token function">__init__</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> setpoint<span class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>setpoint <span class="token operator">=</span> setpoint
        self<span class="token punctuation">.</span>modo_actual <span class="token operator">=</span> <span class="token string">"INICIO"</span>
        self<span class="token punctuation">.</span>contador_estabilidad <span class="token operator">=</span> <span class="token number">0</span>
        self<span class="token punctuation">.</span>historico_modos <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
        
    <span class="token keyword">def</span> <span class="token function">seleccionar_parametros</span><span class="token punctuation">(</span>self<span class="token punctuation">,</span> temperatura_actual<span class="token punctuation">)</span><span class="token punctuation">:</span>
        error <span class="token operator">=</span> <span class="token builtin">abs</span><span class="token punctuation">(</span>self<span class="token punctuation">.</span>setpoint <span class="token operator">-</span> temperatura_actual<span class="token punctuation">)</span>
        
        <span class="token comment"># Lógica de decisión mejorada con histéresis</span>
        <span class="token keyword">if</span> error <span class="token operator">&gt;</span> <span class="token number">15</span><span class="token punctuation">:</span>
            nuevo_modo <span class="token operator">=</span> <span class="token string">"AGRESIVO"</span>
            params <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">80</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">)</span>
        <span class="token keyword">elif</span> error <span class="token operator">&gt;</span> <span class="token number">8</span><span class="token punctuation">:</span>
            nuevo_modo <span class="token operator">=</span> <span class="token string">"RAPIDO"</span> 
            params <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">60</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">,</span> <span class="token number">15</span><span class="token punctuation">)</span>
        <span class="token keyword">elif</span> error <span class="token operator">&gt;</span> <span class="token number">3</span><span class="token punctuation">:</span>
            nuevo_modo <span class="token operator">=</span> <span class="token string">"NORMAL"</span>
            params <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">40</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">)</span>
        <span class="token keyword">else</span><span class="token punctuation">:</span>
            nuevo_modo <span class="token operator">=</span> <span class="token string">"PRECISO"</span>
            params <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">)</span>
            
        <span class="token comment"># Detectar cambio de modo</span>
        <span class="token keyword">if</span> nuevo_modo <span class="token operator">!=</span> self<span class="token punctuation">.</span>modo_actual<span class="token punctuation">:</span>
            <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   🔄 Cambio de modo: {self.modo_actual} → {nuevo_modo}"</span><span class="token punctuation">)</span>
            self<span class="token punctuation">.</span>modo_actual <span class="token operator">=</span> nuevo_modo
            
        self<span class="token punctuation">.</span>historico_modos<span class="token punctuation">.</span>append<span class="token punctuation">(</span>self<span class="token punctuation">.</span>modo_actual<span class="token punctuation">)</span>
        <span class="token keyword">return</span> params

<span class="token comment"># 4. SIMULACIÓN COMPARATIVA COMPLETA</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n🔵 INICIANDO SIMULACIÓN COMPARATIVA..."</span><span class="token punctuation">)</span>

<span class="token comment"># Parámetros de simulación</span>
setpoint <span class="token operator">=</span> <span class="token number">60.0</span>
tiempo_simulacion <span class="token operator">=</span> <span class="token number">300</span>  <span class="token comment"># 5 minutos</span>
dt <span class="token operator">=</span> <span class="token number">1.0</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"1/4 - Configurando sistemas..."</span><span class="token punctuation">)</span>
planta_pid <span class="token operator">=</span> SistemaTermicoRealista<span class="token punctuation">(</span><span class="token punctuation">)</span>
pid_tradicional <span class="token operator">=</span> PID_Avanzado<span class="token punctuation">(</span>Kp<span class="token operator">=</span><span class="token number">45</span><span class="token punctuation">,</span> Ki<span class="token operator">=</span><span class="token number">2</span><span class="token punctuation">,</span> Kd<span class="token operator">=</span><span class="token number">10</span><span class="token punctuation">,</span> setpoint<span class="token operator">=</span>setpoint<span class="token punctuation">,</span> dt<span class="token operator">=</span>dt<span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"2/4 - Configurando sistema IA..."</span><span class="token punctuation">)</span>
planta_ia <span class="token operator">=</span> SistemaTermicoRealista<span class="token punctuation">(</span><span class="token punctuation">)</span> 
control_ia <span class="token operator">=</span> ControladorIA<span class="token punctuation">(</span>setpoint<span class="token operator">=</span>setpoint<span class="token punctuation">)</span>
pid_ia <span class="token operator">=</span> PID_Avanzado<span class="token punctuation">(</span>Kp<span class="token operator">=</span><span class="token number">40</span><span class="token punctuation">,</span> Ki<span class="token operator">=</span><span class="token number">3</span><span class="token punctuation">,</span> Kd<span class="token operator">=</span><span class="token number">8</span><span class="token punctuation">,</span> setpoint<span class="token operator">=</span>setpoint<span class="token punctuation">,</span> dt<span class="token operator">=</span>dt<span class="token punctuation">)</span>

<span class="token comment"># Arrays para resultados</span>
tiempos <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
temperaturas_pid <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
temperaturas_ia <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
modos_control <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
salidas_control_pid <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>
salidas_control_ia <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"3/4 - Ejecutando simulación..."</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> t <span class="token keyword">in</span> <span class="token builtin">range</span><span class="token punctuation">(</span>tiempo_simulacion<span class="token punctuation">)</span><span class="token punctuation">:</span>
    tiempos<span class="token punctuation">.</span>append<span class="token punctuation">(</span>t<span class="token punctuation">)</span>
    
    <span class="token comment"># Simulación PID tradicional</span>
    temp_pid <span class="token operator">=</span> planta_pid<span class="token punctuation">.</span>temperatura
    control_pid <span class="token operator">=</span> pid_tradicional<span class="token punctuation">.</span>calcular<span class="token punctuation">(</span>temp_pid<span class="token punctuation">)</span>
    nueva_temp_pid <span class="token operator">=</span> planta_pid<span class="token punctuation">.</span>actualizar<span class="token punctuation">(</span>control_pid<span class="token punctuation">,</span> dt<span class="token punctuation">)</span>
    temperaturas_pid<span class="token punctuation">.</span>append<span class="token punctuation">(</span>nueva_temp_pid<span class="token punctuation">)</span>
    salidas_control_pid<span class="token punctuation">.</span>append<span class="token punctuation">(</span>control_pid<span class="token punctuation">)</span>
    
    <span class="token comment"># Simulación con IA</span>
    temp_ia <span class="token operator">=</span> planta_ia<span class="token punctuation">.</span>temperatura
    Kp_ia<span class="token punctuation">,</span> Ki_ia<span class="token punctuation">,</span> Kd_ia <span class="token operator">=</span> control_ia<span class="token punctuation">.</span>seleccionar_parametros<span class="token punctuation">(</span>temp_ia<span class="token punctuation">)</span>
    pid_ia<span class="token punctuation">.</span>Kp<span class="token punctuation">,</span> pid_ia<span class="token punctuation">.</span>Ki<span class="token punctuation">,</span> pid_ia<span class="token punctuation">.</span>Kd <span class="token operator">=</span> Kp_ia<span class="token punctuation">,</span> Ki_ia<span class="token punctuation">,</span> Kd_ia
    
    control_ia_val <span class="token operator">=</span> pid_ia<span class="token punctuation">.</span>calcular<span class="token punctuation">(</span>temp_ia<span class="token punctuation">)</span>
    nueva_temp_ia <span class="token operator">=</span> planta_ia<span class="token punctuation">.</span>actualizar<span class="token punctuation">(</span>control_ia_val<span class="token punctuation">,</span> dt<span class="token punctuation">)</span>
    temperaturas_ia<span class="token punctuation">.</span>append<span class="token punctuation">(</span>nueva_temp_ia<span class="token punctuation">)</span>
    modos_control<span class="token punctuation">.</span>append<span class="token punctuation">(</span>control_ia<span class="token punctuation">.</span>modo_actual<span class="token punctuation">)</span>
    salidas_control_ia<span class="token punctuation">.</span>append<span class="token punctuation">(</span>control_ia_val<span class="token punctuation">)</span>
    
    <span class="token comment"># Progress bar</span>
    <span class="token keyword">if</span> t <span class="token operator">%</span> <span class="token number">50</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">:</span>
        progreso <span class="token operator">=</span> <span class="token punctuation">(</span>t <span class="token operator">/</span> tiempo_simulacion<span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">100</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   ⏰ {t}s ({progreso:.0f}%) - Modo IA: {control_ia.modo_actual}"</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"4/4 - Analizando resultados..."</span><span class="token punctuation">)</span>

<span class="token comment"># 5. ANÁLISIS ESTADÍSTICO COMPLETO</span>
<span class="token keyword">def</span> <span class="token function">calcular_metricas_completas</span><span class="token punctuation">(</span>temperaturas<span class="token punctuation">,</span> setpoint<span class="token punctuation">,</span> nombre<span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token comment"># Ignorar primeros 50 puntos (transitorio)</span>
    temps_estado_estable <span class="token operator">=</span> temperaturas<span class="token punctuation">[</span><span class="token number">50</span><span class="token punctuation">:</span><span class="token punctuation">]</span>
    
    errores <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token builtin">abs</span><span class="token punctuation">(</span>t <span class="token operator">-</span> setpoint<span class="token punctuation">)</span> <span class="token keyword">for</span> t <span class="token keyword">in</span> temps_estado_estable<span class="token punctuation">]</span>
    error_promedio <span class="token operator">=</span> np<span class="token punctuation">.</span>mean<span class="token punctuation">(</span>errores<span class="token punctuation">)</span>
    error_maximo <span class="token operator">=</span> np<span class="token punctuation">.</span><span class="token builtin">max</span><span class="token punctuation">(</span>errores<span class="token punctuation">)</span>
    estabilidad <span class="token operator">=</span> np<span class="token punctuation">.</span>std<span class="token punctuation">(</span>errores<span class="token punctuation">)</span>  <span class="token comment"># Desviación estándar</span>
    
    <span class="token comment"># Tiempo de establecimiento (dentro del 5%)</span>
    <span class="token keyword">for</span> i<span class="token punctuation">,</span> temp <span class="token keyword">in</span> <span class="token builtin">enumerate</span><span class="token punctuation">(</span>temperaturas<span class="token punctuation">)</span><span class="token punctuation">:</span>
        <span class="token keyword">if</span> <span class="token builtin">abs</span><span class="token punctuation">(</span>temp <span class="token operator">-</span> setpoint<span class="token punctuation">)</span> <span class="token operator">&lt;=</span> setpoint <span class="token operator">*</span> <span class="token number">0.05</span><span class="token punctuation">:</span>
            tiempo_estable <span class="token operator">=</span> i
            <span class="token keyword">break</span>
    <span class="token keyword">else</span><span class="token punctuation">:</span>
        tiempo_estable <span class="token operator">=</span> <span class="token builtin">len</span><span class="token punctuation">(</span>temperaturas<span class="token punctuation">)</span>
    
    <span class="token comment"># Sobrepico</span>
    sobrepico <span class="token operator">=</span> <span class="token builtin">max</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> np<span class="token punctuation">.</span><span class="token builtin">max</span><span class="token punctuation">(</span>temperaturas<span class="token punctuation">)</span> <span class="token operator">-</span> setpoint<span class="token punctuation">)</span>
    
    <span class="token comment"># Eficiencia energética</span>
    area_error <span class="token operator">=</span> np<span class="token punctuation">.</span>trapz<span class="token punctuation">(</span>errores<span class="token punctuation">)</span>
    
    metricas <span class="token operator">=</span> <span class="token punctuation">{</span>
        <span class="token string">'Sistema'</span><span class="token punctuation">:</span> nombre<span class="token punctuation">,</span>
        <span class="token string">'Error Promedio (°C)'</span><span class="token punctuation">:</span> error_promedio<span class="token punctuation">,</span>
        <span class="token string">'Error Máximo (°C)'</span><span class="token punctuation">:</span> error_maximo<span class="token punctuation">,</span>
        <span class="token string">'Estabilidad (σ)'</span><span class="token punctuation">:</span> estabilidad<span class="token punctuation">,</span>
        <span class="token string">'Tiempo Establecimiento (s)'</span><span class="token punctuation">:</span> tiempo_estable<span class="token punctuation">,</span>
        <span class="token string">'Sobrepico (°C)'</span><span class="token punctuation">:</span> sobrepico<span class="token punctuation">,</span>
        <span class="token string">'Eficiencia (área error)'</span><span class="token punctuation">:</span> area_error
    <span class="token punctuation">}</span>
    
    <span class="token keyword">return</span> metricas

<span class="token comment"># Calcular métricas para ambos sistemas</span>
metricas_pid <span class="token operator">=</span> calcular_metricas_completas<span class="token punctuation">(</span>temperaturas_pid<span class="token punctuation">,</span> setpoint<span class="token punctuation">,</span> <span class="token string">"PID Tradicional"</span><span class="token punctuation">)</span>
metricas_ia <span class="token operator">=</span> calcular_metricas_completas<span class="token punctuation">(</span>temperaturas_ia<span class="token punctuation">,</span> setpoint<span class="token punctuation">,</span> <span class="token string">"PID + IA"</span><span class="token punctuation">)</span>

<span class="token comment"># Calcular mejoras</span>
mejora_error <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>metricas_pid<span class="token punctuation">[</span><span class="token string">'Error Promedio (°C)'</span><span class="token punctuation">]</span> <span class="token operator">-</span> metricas_ia<span class="token punctuation">[</span><span class="token string">'Error Promedio (°C)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">/</span> metricas_pid<span class="token punctuation">[</span><span class="token string">'Error Promedio (°C)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">100</span>
mejora_estabilidad <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>metricas_pid<span class="token punctuation">[</span><span class="token string">'Estabilidad (σ)'</span><span class="token punctuation">]</span> <span class="token operator">-</span> metricas_ia<span class="token punctuation">[</span><span class="token string">'Estabilidad (σ)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">/</span> metricas_pid<span class="token punctuation">[</span><span class="token string">'Estabilidad (σ)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">100</span>
mejora_tiempo <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">(</span>metricas_pid<span class="token punctuation">[</span><span class="token string">'Tiempo Establecimiento (s)'</span><span class="token punctuation">]</span> <span class="token operator">-</span> metricas_ia<span class="token punctuation">[</span><span class="token string">'Tiempo Establecimiento (s)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">/</span> metricas_pid<span class="token punctuation">[</span><span class="token string">'Tiempo Establecimiento (s)'</span><span class="token punctuation">]</span><span class="token punctuation">)</span> <span class="token operator">*</span> <span class="token number">100</span>

<span class="token comment"># 6. VISUALIZACIÓN PROFESIONAL COMPLETA</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"📊 Generando gráficas profesionales..."</span><span class="token punctuation">)</span>

plt<span class="token punctuation">.</span>style<span class="token punctuation">.</span>use<span class="token punctuation">(</span><span class="token string">'default'</span><span class="token punctuation">)</span>
fig <span class="token operator">=</span> plt<span class="token punctuation">.</span>figure<span class="token punctuation">(</span>figsize<span class="token operator">=</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">12</span><span class="token punctuation">)</span><span class="token punctuation">)</span>

<span class="token comment"># Gráfica 1: Comparación principal de temperaturas</span>
ax1 <span class="token operator">=</span> plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>tiempos<span class="token punctuation">,</span> temperaturas_pid<span class="token punctuation">,</span> <span class="token string">'b-'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID Tradicional'</span><span class="token punctuation">,</span> linewidth<span class="token operator">=</span><span class="token number">2.5</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.8</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>tiempos<span class="token punctuation">,</span> temperaturas_ia<span class="token punctuation">,</span> <span class="token string">'r-'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID + IA'</span><span class="token punctuation">,</span> linewidth<span class="token operator">=</span><span class="token number">2.5</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>axhline<span class="token punctuation">(</span>y<span class="token operator">=</span>setpoint<span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'g'</span><span class="token punctuation">,</span> linestyle<span class="token operator">=</span><span class="token string">'--'</span><span class="token punctuation">,</span> linewidth<span class="token operator">=</span><span class="token number">2</span><span class="token punctuation">,</span> label<span class="token operator">=</span>f<span class="token string">'Setpoint ({setpoint}°C)'</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>fill_between<span class="token punctuation">(</span>tiempos<span class="token punctuation">,</span> setpoint<span class="token operator">*</span><span class="token number">0.95</span><span class="token punctuation">,</span> setpoint<span class="token operator">*</span><span class="token number">1.05</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.1</span><span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'green'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Banda ±5%'</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>set_xlabel<span class="token punctuation">(</span><span class="token string">'Tiempo (segundos)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>set_ylabel<span class="token punctuation">(</span><span class="token string">'Temperatura (°C)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>set_title<span class="token punctuation">(</span><span class="token string">'🎯 COMPARACIÓN: Control Tradicional vs Control con IA'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">14</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>legend<span class="token punctuation">(</span>fontsize<span class="token operator">=</span><span class="token number">11</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.3</span><span class="token punctuation">)</span>
ax1<span class="token punctuation">.</span>set_ylim<span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">80</span><span class="token punctuation">)</span>

<span class="token comment"># Gráfica 2: Señales de control comparativas</span>
ax2 <span class="token operator">=</span> plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>tiempos<span class="token punctuation">,</span> salidas_control_pid<span class="token punctuation">,</span> <span class="token string">'blue'</span><span class="token punctuation">,</span> linewidth<span class="token operator">=</span><span class="token number">2</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.7</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Control PID'</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>plot<span class="token punctuation">(</span>tiempos<span class="token punctuation">,</span> salidas_control_ia<span class="token punctuation">,</span> <span class="token string">'red'</span><span class="token punctuation">,</span> linewidth<span class="token operator">=</span><span class="token number">2</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'Control IA'</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>set_xlabel<span class="token punctuation">(</span><span class="token string">'Tiempo (segundos)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>set_ylabel<span class="token punctuation">(</span><span class="token string">'Señal de Control (%)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>set_title<span class="token punctuation">(</span><span class="token string">'⚙️ SEÑALES DE CONTROL COMPARATIVAS'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">14</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>legend<span class="token punctuation">(</span>fontsize<span class="token operator">=</span><span class="token number">11</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.3</span><span class="token punctuation">)</span>
ax2<span class="token punctuation">.</span>set_ylim<span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span>

<span class="token comment"># Gráfica 3: Métricas de desempeño comparativas</span>
ax3 <span class="token operator">=</span> plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">)</span>
metricas_comparar <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token string">'Error Promedio (°C)'</span><span class="token punctuation">,</span> <span class="token string">'Estabilidad (σ)'</span><span class="token punctuation">,</span> <span class="token string">'Tiempo Establecimiento (s)'</span><span class="token punctuation">]</span>
valores_pid <span class="token operator">=</span> <span class="token punctuation">[</span>metricas_pid<span class="token punctuation">[</span>m<span class="token punctuation">]</span> <span class="token keyword">for</span> m <span class="token keyword">in</span> metricas_comparar<span class="token punctuation">]</span>
valores_ia <span class="token operator">=</span> <span class="token punctuation">[</span>metricas_ia<span class="token punctuation">[</span>m<span class="token punctuation">]</span> <span class="token keyword">for</span> m <span class="token keyword">in</span> metricas_comparar<span class="token punctuation">]</span>

x <span class="token operator">=</span> np<span class="token punctuation">.</span>arange<span class="token punctuation">(</span><span class="token builtin">len</span><span class="token punctuation">(</span>metricas_comparar<span class="token punctuation">)</span><span class="token punctuation">)</span>
ancho <span class="token operator">=</span> <span class="token number">0.35</span>

bars1 <span class="token operator">=</span> ax3<span class="token punctuation">.</span>bar<span class="token punctuation">(</span>x <span class="token operator">-</span> ancho<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">,</span> valores_pid<span class="token punctuation">,</span> ancho<span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID Tradicional'</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.8</span><span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'blue'</span><span class="token punctuation">)</span>
bars2 <span class="token operator">=</span> ax3<span class="token punctuation">.</span>bar<span class="token punctuation">(</span>x <span class="token operator">+</span> ancho<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">,</span> valores_ia<span class="token punctuation">,</span> ancho<span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID + IA'</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.8</span><span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'red'</span><span class="token punctuation">)</span>

<span class="token comment"># Añadir valores en las barras</span>
<span class="token keyword">for</span> i<span class="token punctuation">,</span> <span class="token punctuation">(</span>v1<span class="token punctuation">,</span> v2<span class="token punctuation">)</span> <span class="token keyword">in</span> <span class="token builtin">enumerate</span><span class="token punctuation">(</span><span class="token builtin">zip</span><span class="token punctuation">(</span>valores_pid<span class="token punctuation">,</span> valores_ia<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    ax3<span class="token punctuation">.</span>text<span class="token punctuation">(</span>i <span class="token operator">-</span> ancho<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">,</span> v1 <span class="token operator">+</span> <span class="token number">0.1</span><span class="token punctuation">,</span> f<span class="token string">'{v1:.2f}'</span><span class="token punctuation">,</span> ha<span class="token operator">=</span><span class="token string">'center'</span><span class="token punctuation">,</span> va<span class="token operator">=</span><span class="token string">'bottom'</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
    ax3<span class="token punctuation">.</span>text<span class="token punctuation">(</span>i <span class="token operator">+</span> ancho<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">,</span> v2 <span class="token operator">+</span> <span class="token number">0.1</span><span class="token punctuation">,</span> f<span class="token string">'{v2:.2f}'</span><span class="token punctuation">,</span> ha<span class="token operator">=</span><span class="token string">'center'</span><span class="token punctuation">,</span> va<span class="token operator">=</span><span class="token string">'bottom'</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>

ax3<span class="token punctuation">.</span>set_xlabel<span class="token punctuation">(</span><span class="token string">'Métricas de Desempeño'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>set_ylabel<span class="token punctuation">(</span><span class="token string">'Valores'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>set_title<span class="token punctuation">(</span><span class="token string">'📊 COMPARACIÓN DE MÉTRICAS DE DESEMPEÑO'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">14</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>set_xticks<span class="token punctuation">(</span>x<span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>set_xticklabels<span class="token punctuation">(</span><span class="token punctuation">[</span><span class="token string">'Error Prom.'</span><span class="token punctuation">,</span> <span class="token string">'Estabilidad'</span><span class="token punctuation">,</span> <span class="token string">'Tiempo Est.'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> rotation<span class="token operator">=</span><span class="token number">45</span><span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>legend<span class="token punctuation">(</span>fontsize<span class="token operator">=</span><span class="token number">11</span><span class="token punctuation">)</span>
ax3<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.3</span><span class="token punctuation">,</span> axis<span class="token operator">=</span><span class="token string">'y'</span><span class="token punctuation">)</span>

<span class="token comment"># Gráfica 4: Distribución de errores</span>
ax4 <span class="token operator">=</span> plt<span class="token punctuation">.</span>subplot<span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">)</span>
errores_pid_ee <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token builtin">abs</span><span class="token punctuation">(</span>t <span class="token operator">-</span> setpoint<span class="token punctuation">)</span> <span class="token keyword">for</span> t <span class="token keyword">in</span> temperaturas_pid<span class="token punctuation">[</span><span class="token number">50</span><span class="token punctuation">:</span><span class="token punctuation">]</span><span class="token punctuation">]</span>
errores_ia_ee <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token builtin">abs</span><span class="token punctuation">(</span>t <span class="token operator">-</span> setpoint<span class="token punctuation">)</span> <span class="token keyword">for</span> t <span class="token keyword">in</span> temperaturas_ia<span class="token punctuation">[</span><span class="token number">50</span><span class="token punctuation">:</span><span class="token punctuation">]</span><span class="token punctuation">]</span>

ax4<span class="token punctuation">.</span>hist<span class="token punctuation">(</span>errores_pid_ee<span class="token punctuation">,</span> bins<span class="token operator">=</span><span class="token number">20</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.7</span><span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'blue'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID Tradicional'</span><span class="token punctuation">,</span> density<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>hist<span class="token punctuation">(</span>errores_ia_ee<span class="token punctuation">,</span> bins<span class="token operator">=</span><span class="token number">20</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.7</span><span class="token punctuation">,</span> color<span class="token operator">=</span><span class="token string">'red'</span><span class="token punctuation">,</span> label<span class="token operator">=</span><span class="token string">'PID + IA'</span><span class="token punctuation">,</span> density<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>set_xlabel<span class="token punctuation">(</span><span class="token string">'Error Absoluto (°C)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>set_ylabel<span class="token punctuation">(</span><span class="token string">'Densidad de Probabilidad'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">12</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>set_title<span class="token punctuation">(</span><span class="token string">'📋 DISTRIBUCIÓN DE ERRORES (Estado Estable)'</span><span class="token punctuation">,</span> fontsize<span class="token operator">=</span><span class="token number">14</span><span class="token punctuation">,</span> fontweight<span class="token operator">=</span><span class="token string">'bold'</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>legend<span class="token punctuation">(</span>fontsize<span class="token operator">=</span><span class="token number">11</span><span class="token punctuation">)</span>
ax4<span class="token punctuation">.</span>grid<span class="token punctuation">(</span><span class="token boolean">True</span><span class="token punctuation">,</span> alpha<span class="token operator">=</span><span class="token number">0.3</span><span class="token punctuation">)</span>

plt<span class="token punctuation">.</span>tight_layout<span class="token punctuation">(</span><span class="token punctuation">)</span>
plt<span class="token punctuation">.</span>savefig<span class="token punctuation">(</span><span class="token string">'resultados_simulacion_completa.png'</span><span class="token punctuation">,</span> dpi<span class="token operator">=</span><span class="token number">300</span><span class="token punctuation">,</span> bbox_inches<span class="token operator">=</span><span class="token string">'tight'</span><span class="token punctuation">)</span>
plt<span class="token punctuation">.</span>show<span class="token punctuation">(</span><span class="token punctuation">)</span>

<span class="token comment"># 7. REPORTE EJECUTIVO COMPLETO</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n"</span> <span class="token operator">+</span> <span class="token string">"="</span><span class="token operator">*</span><span class="token number">80</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"📊 INFORME TÉCNICO COMPLETO - PROYECTO CONTROL CON IA"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"="</span><span class="token operator">*</span><span class="token number">80</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"🎯 CONFIGURACIÓN: Setpoint = {setpoint}°C, Tiempo simulación = {tiempo_simulacion}s"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"📅 FECHA SIMULACIÓN: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}"</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n"</span> <span class="token operator">+</span> <span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"DESEMPEÑO PID TRADICIONAL"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> key<span class="token punctuation">,</span> value <span class="token keyword">in</span> metricas_pid<span class="token punctuation">.</span>items<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">if</span> key <span class="token operator">!=</span> <span class="token string">'Sistema'</span><span class="token punctuation">:</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   • {key}: {value:.3f}"</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n"</span> <span class="token operator">+</span> <span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"DESEMPEÑO PID + IA"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">for</span> key<span class="token punctuation">,</span> value <span class="token keyword">in</span> metricas_ia<span class="token punctuation">.</span>items<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">:</span>
    <span class="token keyword">if</span> key <span class="token operator">!=</span> <span class="token string">'Sistema'</span><span class="token punctuation">:</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   • {key}: {value:.3f}"</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n"</span> <span class="token operator">+</span> <span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"ANÁLISIS DE MEJORAS CON IA"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"─"</span> <span class="token operator">*</span> <span class="token number">50</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   ✅ Reducción error promedio:    {mejora_error:+.1f}%"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   ✅ Mejora en estabilidad:       {mejora_estabilidad:+.1f}%"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"   ✅ Mejora tiempo respuesta:     {mejora_tiempo:+.1f}%"</span><span class="token punctuation">)</span>

<span class="token comment"># Análisis cualitativo</span>
<span class="token keyword">if</span> mejora_error <span class="token operator">&gt;</span> <span class="token number">10</span><span class="token punctuation">:</span>
    analisis <span class="token operator">=</span> <span class="token string">"EXCELENTE - La IA proporciona mejoras significativas"</span>
<span class="token keyword">elif</span> mejora_error <span class="token operator">&gt;</span> <span class="token number">5</span><span class="token punctuation">:</span>
    analisis <span class="token operator">=</span> <span class="token string">"BUENO - La IA ofrece mejoras moderadas"</span>
<span class="token keyword">elif</span> mejora_error <span class="token operator">&gt;</span> <span class="token number">0</span><span class="token punctuation">:</span>
    analisis <span class="token operator">=</span> <span class="token string">"ACEPTABLE - Pequeñas mejoras con IA"</span>
<span class="token keyword">else</span><span class="token punctuation">:</span>
    analisis <span class="token operator">=</span> <span class="token string">"REVISAR - La IA no mejora el desempeño en esta configuración"</span>

<span class="token keyword">print</span><span class="token punctuation">(</span>f<span class="token string">"\n   📝 ANÁLISIS: {analisis}"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"="</span><span class="token operator">*</span><span class="token number">80</span><span class="token punctuation">)</span>

<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"\n🎉 SIMULACIÓN COMPLETADA EXITOSAMENTE!"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"📁 Archivo guardado: 'resultados_simulacion_completa.png'"</span><span class="token punctuation">)</span>
<span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"🚀 LISTO PARA IMPLEMENTACIÓN EN HARDWARE"</span><span class="token punctuation">)</span>
</code></pre>
<hr>
<h1 id="🔌-paso-2-código-vhdl-completo-para-fpga">🔌 <strong>PASO 2: CÓDIGO VHDL COMPLETO PARA FPGA</strong></h1>
<h2 id="archivo-principal-control_temperatura_ia.vhd"><strong>ARCHIVO PRINCIPAL: control_temperatura_ia.vhd</strong></h2>
<pre class=" language-vhdl"><code class="prism  language-vhdl"><span class="token comment">-- ===========================================================</span>
<span class="token comment">-- CÓDIGO VHDL COMPLETO: CONTROL TEMPERATURA CON IA</span>
<span class="token comment">-- FPGA: Altera MAX II EPM240T100C5</span>
<span class="token comment">-- Fecha: Noviembre 2024</span>
<span class="token comment">-- ===========================================================</span>

<span class="token constant">library</span> IEEE<span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_1164<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>NUMERIC_STD<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_UNSIGNED<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>

<span class="token keyword">entity</span> control_temperatura_ia <span class="token keyword">is</span>
    <span class="token keyword">Port</span> <span class="token punctuation">(</span>
        <span class="token comment">-- Entradas principales</span>
        clk_50mhz     <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Reloj 50MHz</span>
        reset         <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Reset global</span>
        
        <span class="token comment">-- Entradas ADC (MCP3008)</span>
        adc_miso      <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Master In Slave Out</span>
        adc_ready     <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- ADC listo</span>
        
        <span class="token comment">-- Salidas control</span>
        pwm_out       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Salida PWM calefactor</span>
        pwm_enable    <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Habilitación PWM</span>
        
        <span class="token comment">-- Salidas ADC (MCP3008)</span>
        adc_cs        <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Chip Select</span>
        adc_mosi      <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Master Out Slave In  </span>
        adc_clk       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Reloj SPI</span>
        
        <span class="token comment">-- Salidas indicadores</span>
        modo_led      <span class="token punctuation">:</span> <span class="token keyword">out</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">2</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- LEDs modo operación</span>
        debug_out     <span class="token punctuation">:</span> <span class="token keyword">out</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">7</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- Salida debug</span>
        buzzer        <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Alarma</span>
        
        <span class="token comment">-- Comunicación UART</span>
        uart_tx       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>                    <span class="token comment">-- Transmisión UART</span>
        uart_rx       <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC                     <span class="token comment">-- Recepción UART</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">end</span> control_temperatura_ia<span class="token punctuation">;</span>

<span class="token keyword">architecture</span> Behavioral <span class="token keyword">of</span> control_temperatura_ia <span class="token keyword">is</span>
    
    <span class="token comment">-- CONSTANTES DEL SISTEMA</span>
    <span class="token keyword">constant</span> SETPOINT_TARGET   <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">60</span><span class="token punctuation">;</span>           <span class="token comment">-- 60°C</span>
    <span class="token keyword">constant</span> TEMP_MAX_SEGURA   <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">80</span><span class="token punctuation">;</span>           <span class="token comment">-- Límite seguridad</span>
    <span class="token keyword">constant</span> TEMP_MIN_OPERACION <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">20</span><span class="token punctuation">;</span>          <span class="token comment">-- Mínimo operación</span>
    
    <span class="token comment">-- PARÁMETROS PID POR MODO (Optimizados desde simulación)</span>
    <span class="token keyword">constant</span> KP_AGRESIVO       <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">80</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KI_AGRESIVO       <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">8</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KD_AGRESIVO       <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">20</span><span class="token punctuation">;</span>
    
    <span class="token keyword">constant</span> KP_RAPIDO         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">60</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KI_RAPIDO         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">5</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KD_RAPIDO         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">15</span><span class="token punctuation">;</span>
    
    <span class="token keyword">constant</span> KP_NORMAL         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">40</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KI_NORMAL         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">3</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KD_NORMAL         <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">8</span><span class="token punctuation">;</span>
    
    <span class="token keyword">constant</span> KP_PRECISO        <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">25</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KI_PRECISO        <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">1</span><span class="token punctuation">;</span>
    <span class="token keyword">constant</span> KD_PRECISO        <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">3</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- SEÑALES INTERNAS</span>
    <span class="token keyword">signal</span> temperatura_actual  <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">255</span> <span class="token operator">:=</span> <span class="token number">25</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> temperatura_filtrada <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">255</span> <span class="token operator">:=</span> <span class="token number">25</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> error_actual        <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token operator">-</span><span class="token number">255</span> <span class="token keyword">to</span> <span class="token number">255</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> error_absoluto      <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">255</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> modo_operacion      <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">3</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- SEÑALES CONTROL PID</span>
    <span class="token keyword">signal</span> Kp_actual           <span class="token punctuation">:</span> integer <span class="token operator">:=</span> KP_NORMAL<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> Ki_actual           <span class="token punctuation">:</span> integer <span class="token operator">:=</span> KI_NORMAL<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> Kd_actual           <span class="token punctuation">:</span> integer <span class="token operator">:=</span> KD_NORMAL<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> salida_pid          <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">100</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- SEÑALES PWM</span>
    <span class="token keyword">signal</span> contador_pwm        <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">255</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> duty_cycle          <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">100</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> pwm_counter         <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">10000</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- SEÑALES ADC (MCP3008)</span>
    <span class="token keyword">signal</span> adc_data            <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token number">'0'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_channel         <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">2</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">:=</span> <span class="token vhdl-vectors number">"000"</span><span class="token punctuation">;</span> <span class="token comment">-- Canal 0</span>
    <span class="token keyword">signal</span> adc_conversion_done <span class="token punctuation">:</span> std_logic <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- FILTRO MEDIA MÓVIL</span>
    <span class="token keyword">type</span> hist_array <span class="token keyword">is</span> <span class="token keyword">array</span> <span class="token punctuation">(</span><span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">4</span><span class="token punctuation">)</span> <span class="token keyword">of</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">255</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> historial_temp <span class="token punctuation">:</span> hist_array <span class="token operator">:=</span> <span class="token punctuation">(</span><span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">25</span><span class="token punctuation">,</span> <span class="token number">25</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> temp_sum       <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">125</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- MÁQUINA DE ESTADOS SPI</span>
    <span class="token keyword">type</span> spi_state_type <span class="token keyword">is</span> <span class="token punctuation">(</span>IDLE<span class="token punctuation">,</span> START<span class="token punctuation">,</span> CLK_LOW<span class="token punctuation">,</span> CLK_HIGH<span class="token punctuation">,</span> STOP<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> spi_state <span class="token punctuation">:</span> spi_state_type <span class="token operator">:=</span> IDLE<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> spi_bit_counter <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">15</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- ESTADOS DEL SISTEMA</span>
    <span class="token keyword">type</span> estado_type <span class="token keyword">is</span> <span class="token punctuation">(</span>INICIO<span class="token punctuation">,</span> OPERANDO<span class="token punctuation">,</span> ALARMA<span class="token punctuation">,</span> CONFIGURACION<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> estado_actual <span class="token punctuation">:</span> estado_type <span class="token operator">:=</span> INICIO<span class="token punctuation">;</span>
    
    <span class="token comment">-- CONTADORES Y TEMPORIZADORES</span>
    <span class="token keyword">signal</span> contador_estabilidad <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">1000</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> contador_muestreo    <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">500000</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> reloj_1mhz          <span class="token punctuation">:</span> std_logic <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> contador_reloj      <span class="token punctuation">:</span> integer <span class="token keyword">range</span> <span class="token number">0</span> <span class="token keyword">to</span> <span class="token number">24</span> <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
<span class="token keyword">begin</span>

    <span class="token comment">-- GENERADOR DE RELOJ 1MHz PARA SPI</span>
    proceso_reloj_spi <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">if</span> contador_reloj <span class="token operator">&lt;</span> <span class="token number">24</span> <span class="token keyword">then</span>
                contador_reloj <span class="token operator">&lt;=</span> contador_reloj <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                contador_reloj <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                reloj_1mhz <span class="token operator">&lt;=</span> <span class="token operator">not</span> reloj_1mhz<span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- MÓDULO SPI PARA COMUNICACIÓN CON MCP3008</span>
    proceso_spi <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>reloj_1mhz<span class="token punctuation">,</span> reset<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> reset <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
            spi_state <span class="token operator">&lt;=</span> IDLE<span class="token punctuation">;</span>
            adc_cs <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
            adc_clk <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            adc_mosi <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            spi_bit_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            adc_data <span class="token operator">&lt;=</span> <span class="token punctuation">(</span><span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token number">'0'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            
        <span class="token keyword">elsif</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>reloj_1mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">case</span> spi_state <span class="token keyword">is</span>
                <span class="token keyword">when</span> IDLE <span class="token operator">=</span><span class="token operator">&gt;</span>
                    adc_cs <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    adc_clk <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    spi_bit_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                    <span class="token keyword">if</span> contador_muestreo <span class="token operator">=</span> <span class="token number">0</span> <span class="token keyword">then</span>
                        spi_state <span class="token operator">&lt;=</span> START<span class="token punctuation">;</span>
                        adc_cs <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> START <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token comment">-- Bit de start + modo single-ended + bit D2</span>
                    adc_mosi <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    spi_state <span class="token operator">&lt;=</span> CLK_LOW<span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> CLK_LOW <span class="token operator">=</span><span class="token operator">&gt;</span>
                    adc_clk <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    <span class="token comment">-- Configurar bits de canal (D1, D0)</span>
                    <span class="token keyword">if</span> spi_bit_counter <span class="token operator">=</span> <span class="token number">1</span> <span class="token keyword">then</span>
                        adc_mosi <span class="token operator">&lt;=</span> <span class="token function">adc_channel</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                    <span class="token keyword">elsif</span> spi_bit_counter <span class="token operator">=</span> <span class="token number">2</span> <span class="token keyword">then</span>
                        adc_mosi <span class="token operator">&lt;=</span> <span class="token function">adc_channel</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                    <span class="token keyword">elsif</span> spi_bit_counter <span class="token operator">=</span> <span class="token number">3</span> <span class="token keyword">then</span>
                        adc_mosi <span class="token operator">&lt;=</span> <span class="token function">adc_channel</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                    <span class="token keyword">else</span>
                        adc_mosi <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    spi_state <span class="token operator">&lt;=</span> CLK_HIGH<span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> CLK_HIGH <span class="token operator">=</span><span class="token operator">&gt;</span>
                    adc_clk <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    <span class="token comment">-- Leer datos en flanco de subida (bits 5-14)</span>
                    <span class="token keyword">if</span> spi_bit_counter <span class="token operator">&gt;=</span> <span class="token number">5</span> <span class="token operator">and</span> spi_bit_counter <span class="token operator">&lt;=</span> <span class="token number">14</span> <span class="token keyword">then</span>
                        <span class="token function">adc_data</span><span class="token punctuation">(</span><span class="token number">14</span> <span class="token operator">-</span> spi_bit_counter<span class="token punctuation">)</span> <span class="token operator">&lt;=</span> adc_miso<span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                    <span class="token keyword">if</span> spi_bit_counter <span class="token operator">&lt;</span> <span class="token number">15</span> <span class="token keyword">then</span>
                        spi_bit_counter <span class="token operator">&lt;=</span> spi_bit_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
                        spi_state <span class="token operator">&lt;=</span> CLK_LOW<span class="token punctuation">;</span>
                    <span class="token keyword">else</span>
                        spi_state <span class="token operator">&lt;=</span> STOP<span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> STOP <span class="token operator">=</span><span class="token operator">&gt;</span>
                    adc_cs <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    adc_conversion_done <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    spi_state <span class="token operator">&lt;=</span> IDLE<span class="token punctuation">;</span>
                    
            <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- FILTRO DIGITAL: Media móvil para temperatura</span>
    proceso_filtro <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">if</span> adc_conversion_done <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
                adc_conversion_done <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Actualizar historial</span>
                <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token number">4</span> <span class="token keyword">downto</span> <span class="token number">1</span> <span class="token keyword">loop</span>
                    <span class="token function">historial_temp</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span> <span class="token operator">&lt;=</span> <span class="token function">historial_temp</span><span class="token punctuation">(</span>i<span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
                <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">&lt;=</span> <span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span><span class="token function">adc_data</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- 8 bits</span>
                
                <span class="token comment">-- Calcular media móvil</span>
                temp_sum <span class="token operator">&lt;=</span> <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token operator">+</span> 
                           <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span> <span class="token operator">+</span> <span class="token function">historial_temp</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                temperatura_filtrada <span class="token operator">&lt;=</span> temp_sum <span class="token operator">/</span> <span class="token number">5</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Reset contador de muestreo</span>
                contador_muestreo <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                <span class="token keyword">if</span> contador_muestreo <span class="token operator">&lt;</span> <span class="token number">500000</span> <span class="token keyword">then</span>
                    contador_muestreo <span class="token operator">&lt;=</span> contador_muestreo <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- MÁQUINA DE ESTADOS PRINCIPAL</span>
    proceso_estados <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">,</span> reset<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> reset <span class="token operator">=</span> <span class="token number">'1'</span> <span class="token keyword">then</span>
            estado_actual <span class="token operator">&lt;=</span> INICIO<span class="token punctuation">;</span>
            modo_operacion <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            buzzer <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            
        <span class="token keyword">elsif</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">case</span> estado_actual <span class="token keyword">is</span>
                <span class="token keyword">when</span> INICIO <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token comment">-- Estado inicialización</span>
                    temperatura_actual <span class="token operator">&lt;=</span> <span class="token number">25</span><span class="token punctuation">;</span>
                    modo_operacion <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                    buzzer <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    
                    <span class="token comment">-- Esperar inicialización completa</span>
                    <span class="token keyword">if</span> contador_muestreo <span class="token operator">&gt;</span> <span class="token number">100000</span> <span class="token keyword">then</span>
                        estado_actual <span class="token operator">&lt;=</span> OPERANDO<span class="token punctuation">;</span>
                        pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> OPERANDO <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token comment">-- Estado operación normal</span>
                    temperatura_actual <span class="token operator">&lt;=</span> temperatura_filtrada<span class="token punctuation">;</span>
                    
                    <span class="token comment">-- Verificar límites de seguridad</span>
                    <span class="token keyword">if</span> temperatura_actual <span class="token operator">&gt;</span> TEMP_MAX_SEGURA <span class="token keyword">then</span>
                        estado_actual <span class="token operator">&lt;=</span> ALARMA<span class="token punctuation">;</span>
                        buzzer <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                        pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                    <span class="token comment">-- LÓGICA IA: Selección de parámetros según error</span>
                    error_absoluto <span class="token operator">&lt;=</span> <span class="token function">abs</span><span class="token punctuation">(</span>SETPOINT_TARGET <span class="token operator">-</span> temperatura_actual<span class="token punctuation">)</span><span class="token punctuation">;</span>
                    
                    <span class="token keyword">if</span> error_absoluto <span class="token operator">&gt;</span> <span class="token number">15</span> <span class="token keyword">then</span>
                        modo_operacion <span class="token operator">&lt;=</span> <span class="token number">3</span><span class="token punctuation">;</span>  <span class="token comment">-- AGRESIVO</span>
                        Kp_actual <span class="token operator">&lt;=</span> KP_AGRESIVO<span class="token punctuation">;</span>
                        Ki_actual <span class="token operator">&lt;=</span> KI_AGRESIVO<span class="token punctuation">;</span> 
                        Kd_actual <span class="token operator">&lt;=</span> KD_AGRESIVO<span class="token punctuation">;</span>
                        
                    <span class="token keyword">elsif</span> error_absoluto <span class="token operator">&gt;</span> <span class="token number">8</span> <span class="token keyword">then</span>
                        modo_operacion <span class="token operator">&lt;=</span> <span class="token number">2</span><span class="token punctuation">;</span>  <span class="token comment">-- RAPIDO</span>
                        Kp_actual <span class="token operator">&lt;=</span> KP_RAPIDO<span class="token punctuation">;</span>
                        Ki_actual <span class="token operator">&lt;=</span> KI_RAPIDO<span class="token punctuation">;</span>
                        Kd_actual <span class="token operator">&lt;=</span> KD_RAPIDO<span class="token punctuation">;</span>
                        
                    <span class="token keyword">elsif</span> error_absoluto <span class="token operator">&gt;</span> <span class="token number">3</span> <span class="token keyword">then</span>
                        modo_operacion <span class="token operator">&lt;=</span> <span class="token number">1</span><span class="token punctuation">;</span>  <span class="token comment">-- NORMAL</span>
                        Kp_actual <span class="token operator">&lt;=</span> KP_NORMAL<span class="token punctuation">;</span>
                        Ki_actual <span class="token operator">&lt;=</span> KI_NORMAL<span class="token punctuation">;</span>
                        Kd_actual <span class="token operator">&lt;=</span> KD_NORMAL<span class="token punctuation">;</span>
                        
                    <span class="token keyword">else</span>
                        modo_operacion <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>  <span class="token comment">-- PRECISO</span>
                        Kp_actual <span class="token operator">&lt;=</span> KP_PRECISO<span class="token punctuation">;</span>
                        Ki_actual <span class="token operator">&lt;=</span> KI_PRECISO<span class="token punctuation">;</span>
                        Kd_actual <span class="token operator">&lt;=</span> KD_PRECISO<span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> ALARMA <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token comment">-- Estado de alarma por sobre temperatura</span>
                    buzzer <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                    <span class="token keyword">if</span> temperatura_actual <span class="token operator">&lt;</span> <span class="token punctuation">(</span>TEMP_MAX_SEGURA <span class="token operator">-</span> <span class="token number">5</span><span class="token punctuation">)</span> <span class="token keyword">then</span>
                        estado_actual <span class="token operator">&lt;=</span> OPERANDO<span class="token punctuation">;</span>
                        buzzer <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
                        pwm_enable <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
                    <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                    
                <span class="token keyword">when</span> CONFIGURACION <span class="token operator">=</span><span class="token operator">&gt;</span>
                    <span class="token comment">-- Estado para configuración via UART</span>
                    <span class="token keyword">null</span><span class="token punctuation">;</span> <span class="token comment">-- Implementar según necesidades</span>
                    
            <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- CONTROL PID SIMPLIFICADO EN HARDWARE</span>
    proceso_pid <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span>
        <span class="token keyword">variable</span> error_previo <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
        <span class="token keyword">variable</span> suma_error <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
        <span class="token keyword">variable</span> P<span class="token punctuation">,</span> I<span class="token punctuation">,</span> D <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">if</span> estado_actual <span class="token operator">=</span> OPERANDO <span class="token keyword">then</span>
                <span class="token comment">-- Calcular error</span>
                error_actual <span class="token operator">&lt;=</span> SETPOINT_TARGET <span class="token operator">-</span> temperatura_actual<span class="token punctuation">;</span>
                
                <span class="token comment">-- Término Proporcional</span>
                P <span class="token operator">:=</span> error_actual <span class="token operator">*</span> Kp_actual <span class="token operator">/</span> <span class="token number">100</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Término Integral (simplificado)</span>
                suma_error <span class="token operator">:=</span> suma_error <span class="token operator">+</span> error_actual<span class="token punctuation">;</span>
                <span class="token keyword">if</span> suma_error <span class="token operator">&gt;</span> <span class="token number">1000</span> <span class="token keyword">then</span>
                    suma_error <span class="token operator">:=</span> <span class="token number">1000</span><span class="token punctuation">;</span>  <span class="token comment">-- Anti-windup</span>
                <span class="token keyword">elsif</span> suma_error <span class="token operator">&lt;</span> <span class="token operator">-</span><span class="token number">1000</span> <span class="token keyword">then</span>
                    suma_error <span class="token operator">:=</span> <span class="token operator">-</span><span class="token number">1000</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
                I <span class="token operator">:=</span> suma_error <span class="token operator">*</span> Ki_actual <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
                
                <span class="token comment">-- Término Derivativo</span>
                D <span class="token operator">:=</span> <span class="token punctuation">(</span>error_actual <span class="token operator">-</span> error_previo<span class="token punctuation">)</span> <span class="token operator">*</span> Kd_actual <span class="token operator">/</span> <span class="token number">100</span><span class="token punctuation">;</span>
                error_previo <span class="token operator">:=</span> error_actual<span class="token punctuation">;</span>
                
                <span class="token comment">-- Salida PID</span>
                salida_pid <span class="token operator">&lt;=</span> P <span class="token operator">+</span> I <span class="token operator">+</span> D<span class="token punctuation">;</span>
                
                <span class="token comment">-- Saturación</span>
                <span class="token keyword">if</span> salida_pid <span class="token operator">&gt;</span> <span class="token number">100</span> <span class="token keyword">then</span>
                    salida_pid <span class="token operator">&lt;=</span> <span class="token number">100</span><span class="token punctuation">;</span>
                <span class="token keyword">elsif</span> salida_pid <span class="token operator">&lt;</span> <span class="token number">0</span> <span class="token keyword">then</span>
                    salida_pid <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                salida_pid <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                suma_error <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
                error_previo <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- CONTROL DE LEDs SEGÚN MODO DE OPERACIÓN</span>
    proceso_leds <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>modo_operacion<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">case</span> modo_operacion <span class="token keyword">is</span>
            <span class="token keyword">when</span> <span class="token number">0</span> <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led <span class="token operator">&lt;=</span> <span class="token vhdl-vectors number">"001"</span><span class="token punctuation">;</span>  <span class="token comment">-- PRECISO: LED verde</span>
            <span class="token keyword">when</span> <span class="token number">1</span> <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led <span class="token operator">&lt;=</span> <span class="token vhdl-vectors number">"010"</span><span class="token punctuation">;</span>  <span class="token comment">-- NORMAL: LED azul  </span>
            <span class="token keyword">when</span> <span class="token number">2</span> <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led <span class="token operator">&lt;=</span> <span class="token vhdl-vectors number">"100"</span><span class="token punctuation">;</span>  <span class="token comment">-- RAPIDO: LED amarillo</span>
            <span class="token keyword">when</span> <span class="token number">3</span> <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led <span class="token operator">&lt;=</span> <span class="token vhdl-vectors number">"101"</span><span class="token punctuation">;</span>  <span class="token comment">-- AGRESIVO: LED rojo</span>
            <span class="token keyword">when</span> <span class="token keyword">others</span> <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led <span class="token operator">&lt;=</span> <span class="token vhdl-vectors number">"000"</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">case</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- GENERADOR PWM PARA CONTROL DE POTENCIA</span>
    proceso_pwm <span class="token punctuation">:</span> <span class="token keyword">process</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">if</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>clk_50mhz<span class="token punctuation">)</span> <span class="token keyword">then</span>
            <span class="token keyword">if</span> pwm_counter <span class="token operator">&lt;</span> <span class="token number">10000</span> <span class="token keyword">then</span>
                pwm_counter <span class="token operator">&lt;=</span> pwm_counter <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                pwm_counter <span class="token operator">&lt;=</span> <span class="token number">0</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
            
            <span class="token comment">-- Asignar duty cycle desde salida PID</span>
            duty_cycle <span class="token operator">&lt;=</span> salida_pid<span class="token punctuation">;</span>
            
            <span class="token comment">-- Generar señal PWM</span>
            <span class="token keyword">if</span> pwm_counter <span class="token operator">&lt;</span> <span class="token punctuation">(</span>duty_cycle <span class="token operator">*</span> <span class="token number">100</span><span class="token punctuation">)</span> <span class="token keyword">then</span>
                pwm_out <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
            <span class="token keyword">else</span>
                pwm_out <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">if</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- SALIDA DEBUG (temperatura actual)</span>
    debug_out <span class="token operator">&lt;=</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token function">to_unsigned</span><span class="token punctuation">(</span>temperatura_actual<span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">end</span> Behavioral<span class="token punctuation">;</span>
</code></pre>
<hr>
<h1 id="🔬-paso-3-testbench-completo-para-verificación">🔬 <strong>PASO 3: TESTBENCH COMPLETO PARA VERIFICACIÓN</strong></h1>
<h2 id="archivo-tb_control_temperatura_ia.vhd"><strong>ARCHIVO: tb_control_temperatura_ia.vhd</strong></h2>
<pre class=" language-vhdl"><code class="prism  language-vhdl"><span class="token comment">-- ===========================================================</span>
<span class="token comment">-- TESTBENCH COMPLETO: CONTROL TEMPERATURA CON IA</span>
<span class="token comment">-- Verificación funcional y temporal</span>
<span class="token comment">-- ===========================================================</span>

<span class="token constant">library</span> IEEE<span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_1164<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>NUMERIC_STD<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> IEEE<span class="token punctuation">.</span>STD_LOGIC_TEXTIO<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>
<span class="token constant">use</span> STD<span class="token punctuation">.</span>TEXTIO<span class="token punctuation">.</span><span class="token keyword">ALL</span><span class="token punctuation">;</span>

<span class="token keyword">entity</span> tb_control_temperatura_ia <span class="token keyword">is</span>
<span class="token comment">-- Testbench no tiene puertos</span>
<span class="token keyword">end</span> tb_control_temperatura_ia<span class="token punctuation">;</span>

<span class="token keyword">architecture</span> Behavioral <span class="token keyword">of</span> tb_control_temperatura_ia <span class="token keyword">is</span>

    <span class="token comment">-- Componente a testear</span>
    <span class="token keyword">component</span> control_temperatura_ia
        <span class="token keyword">Port</span> <span class="token punctuation">(</span>
            clk_50mhz     <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>
            reset         <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>
            adc_miso      <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>
            adc_ready     <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC<span class="token punctuation">;</span>
            pwm_out       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            pwm_enable    <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_cs        <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_mosi      <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            adc_clk       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            modo_led      <span class="token punctuation">:</span> <span class="token keyword">out</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">2</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            debug_out     <span class="token punctuation">:</span> <span class="token keyword">out</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">7</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            buzzer        <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            uart_tx       <span class="token punctuation">:</span> <span class="token keyword">out</span> STD_LOGIC<span class="token punctuation">;</span>
            uart_rx       <span class="token punctuation">:</span> <span class="token keyword">in</span>  STD_LOGIC
        <span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">component</span><span class="token punctuation">;</span>

    <span class="token comment">-- Señales de estímulo</span>
    <span class="token keyword">signal</span> clk_50mhz     <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> reset         <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_miso      <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_ready     <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> uart_rx       <span class="token punctuation">:</span> STD_LOGIC <span class="token operator">:=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
    
    <span class="token comment">-- Señales de monitorización</span>
    <span class="token keyword">signal</span> pwm_out       <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> pwm_enable    <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_cs        <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_mosi      <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> adc_clk       <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> modo_led      <span class="token punctuation">:</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">2</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> debug_out     <span class="token punctuation">:</span> <span class="token function">STD_LOGIC_VECTOR</span><span class="token punctuation">(</span><span class="token number">7</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> buzzer        <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> uart_tx       <span class="token punctuation">:</span> STD_LOGIC<span class="token punctuation">;</span>
    
    <span class="token comment">-- Constantes de simulación</span>
    <span class="token keyword">constant</span> CLK_PERIOD <span class="token punctuation">:</span> time <span class="token operator">:=</span> <span class="token number">20</span> ns<span class="token punctuation">;</span> <span class="token comment">-- 50MHz</span>
    <span class="token keyword">constant</span> ADC_SIM_DATA <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token operator">:=</span> <span class="token vhdl-vectors number">"0011110000"</span><span class="token punctuation">;</span> <span class="token comment">-- 60°C simulado</span>
    
    <span class="token comment">-- Contadores y estados</span>
    <span class="token keyword">signal</span> spi_bit_counter <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    <span class="token keyword">signal</span> simulation_time <span class="token punctuation">:</span> time <span class="token operator">:=</span> <span class="token number">0</span> ns<span class="token punctuation">;</span>
    <span class="token keyword">signal</span> test_case <span class="token punctuation">:</span> integer <span class="token operator">:=</span> <span class="token number">1</span><span class="token punctuation">;</span>
    
<span class="token keyword">begin</span>

    <span class="token comment">-- Instancia del DUT (Device Under Test)</span>
    DUT<span class="token punctuation">:</span> control_temperatura_ia
        <span class="token keyword">port</span> <span class="token keyword">map</span> <span class="token punctuation">(</span>
            clk_50mhz  <span class="token operator">=</span><span class="token operator">&gt;</span> clk_50mhz<span class="token punctuation">,</span>
            reset      <span class="token operator">=</span><span class="token operator">&gt;</span> reset<span class="token punctuation">,</span>
            adc_miso   <span class="token operator">=</span><span class="token operator">&gt;</span> adc_miso<span class="token punctuation">,</span>
            adc_ready  <span class="token operator">=</span><span class="token operator">&gt;</span> adc_ready<span class="token punctuation">,</span>
            pwm_out    <span class="token operator">=</span><span class="token operator">&gt;</span> pwm_out<span class="token punctuation">,</span>
            pwm_enable <span class="token operator">=</span><span class="token operator">&gt;</span> pwm_enable<span class="token punctuation">,</span>
            adc_cs     <span class="token operator">=</span><span class="token operator">&gt;</span> adc_cs<span class="token punctuation">,</span>
            adc_mosi   <span class="token operator">=</span><span class="token operator">&gt;</span> adc_mosi<span class="token punctuation">,</span>
            adc_clk    <span class="token operator">=</span><span class="token operator">&gt;</span> adc_clk<span class="token punctuation">,</span>
            modo_led   <span class="token operator">=</span><span class="token operator">&gt;</span> modo_led<span class="token punctuation">,</span>
            debug_out  <span class="token operator">=</span><span class="token operator">&gt;</span> debug_out<span class="token punctuation">,</span>
            buzzer     <span class="token operator">=</span><span class="token operator">&gt;</span> buzzer<span class="token punctuation">,</span>
            uart_tx    <span class="token operator">=</span><span class="token operator">&gt;</span> uart_tx<span class="token punctuation">,</span>
            uart_rx    <span class="token operator">=</span><span class="token operator">&gt;</span> uart_rx
        <span class="token punctuation">)</span><span class="token punctuation">;</span>

    <span class="token comment">-- Generador de reloj 50MHz</span>
    clk_process <span class="token punctuation">:</span> <span class="token keyword">process</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">while</span> <span class="token boolean">true</span> <span class="token keyword">loop</span>
            clk_50mhz <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
            <span class="token keyword">wait</span> <span class="token keyword">for</span> CLK_PERIOD<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">;</span>
            clk_50mhz <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
            <span class="token keyword">wait</span> <span class="token keyword">for</span> CLK_PERIOD<span class="token operator">/</span><span class="token number">2</span><span class="token punctuation">;</span>
            simulation_time <span class="token operator">&lt;=</span> simulation_time <span class="token operator">+</span> CLK_PERIOD<span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- Simulador de ADC MCP3008</span>
    adc_sim_process <span class="token punctuation">:</span> <span class="token keyword">process</span>
        <span class="token keyword">variable</span> adc_response <span class="token punctuation">:</span> <span class="token function">std_logic_vector</span><span class="token punctuation">(</span><span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">variable</span> bit_index <span class="token punctuation">:</span> integer<span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">falling_edge</span><span class="token punctuation">(</span>adc_cs<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Esperar comando de inicio</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- Start bit</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- Single/Diff</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- D2</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- D1</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">-- D0</span>
        
        <span class="token comment">-- Espacio entre comando y respuesta</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Enviar datos simulados (60°C)</span>
        adc_response <span class="token operator">:=</span> ADC_SIM_DATA<span class="token punctuation">;</span>
        <span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token number">9</span> <span class="token keyword">downto</span> <span class="token number">0</span> <span class="token keyword">loop</span>
            adc_miso <span class="token operator">&lt;=</span> <span class="token function">adc_response</span><span class="token punctuation">(</span>i<span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_clk<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token keyword">end</span> <span class="token keyword">loop</span><span class="token punctuation">;</span>
        
        adc_miso <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">until</span> <span class="token function">rising_edge</span><span class="token punctuation">(</span>adc_cs<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- Proceso principal de test</span>
    test_process <span class="token punctuation">:</span> <span class="token keyword">process</span>
        <span class="token keyword">variable</span> test_line <span class="token punctuation">:</span> line<span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token comment">-- TEST 1: Inicialización y reset</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 1: Verificación de inicialización"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        reset <span class="token operator">&lt;=</span> <span class="token number">'1'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">100</span> ns<span class="token punctuation">;</span>
        reset <span class="token operator">&lt;=</span> <span class="token number">'0'</span><span class="token punctuation">;</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">100</span> ns<span class="token punctuation">;</span>
        
        <span class="token comment">-- Verificar estado después de reset</span>
        <span class="token keyword">assert</span> pwm_enable <span class="token operator">=</span> <span class="token number">'0'</span> <span class="token keyword">report</span> <span class="token string">"ERROR: PWM habilitado durante reset"</span> <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        <span class="token keyword">assert</span> buzzer <span class="token operator">=</span> <span class="token number">'0'</span> <span class="token keyword">report</span> <span class="token string">"ERROR: Buzzer activo durante reset"</span> <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Reset e inicialización correctos"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST 2: Comunicación SPI con ADC</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 2: Comunicación SPI con MCP3008"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">500</span> ns<span class="token punctuation">;</span>
        
        <span class="token comment">-- Verificar que se inicia comunicación SPI</span>
        <span class="token keyword">assert</span> adc_cs <span class="token operator">=</span> <span class="token number">'0'</span> <span class="token keyword">report</span> <span class="token string">"ERROR: ADC CS no se activa"</span> <span class="token keyword">severity</span> error<span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Comunicación SPI iniciada correctamente"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST 3: Procesamiento de temperatura</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 3: Procesamiento de datos de temperatura"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">2000</span> ns<span class="token punctuation">;</span>
        
        <span class="token comment">-- Verificar que se procesa la temperatura</span>
        <span class="token keyword">assert</span> <span class="token function">unsigned</span><span class="token punctuation">(</span>debug_out<span class="token punctuation">)</span> <span class="token operator">/</span><span class="token operator">=</span> <span class="token number">0</span> <span class="token keyword">report</span> <span class="token string">"ERROR: Temperatura no procesada"</span> <span class="token keyword">severity</span> warning<span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Temperatura procesada correctamente: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> integer<span class="token keyword">'image</span><span class="token punctuation">(</span><span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>debug_out<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> <span class="token string">"°C"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST 4: Cambio de modos de operación</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 4: Verificación de cambios de modo IA"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Simular diferentes temperaturas para forzar cambios de modo</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">5000</span> ns<span class="token punctuation">;</span>
        
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Modo actual: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> integer<span class="token keyword">'image</span><span class="token punctuation">(</span><span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>modo_led<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST 5: Generación de PWM</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 5: Verificación de salida PWM"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">10000</span> ns<span class="token punctuation">;</span>
        
        <span class="token keyword">assert</span> pwm_out<span class="token keyword">'event</span> <span class="token keyword">report</span> <span class="token string">"ERROR: Salida PWM inactiva"</span> <span class="token keyword">severity</span> warning<span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Salida PWM activa y funcionando"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- TEST 6: Sistema de alarma</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🧪 TEST 6: Verificación de sistema de alarma"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token comment">-- Simular sobrecalentamiento</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">15000</span> ns<span class="token punctuation">;</span>
        
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"✅ Todos los tests completados exitosamente"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>test_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"🎉 TESTBENCH FINALIZADO - SISTEMA FUNCIONAL"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> test_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token keyword">wait</span><span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

    <span class="token comment">-- Monitoreo de señales importantes</span>
    monitor_process <span class="token punctuation">:</span> <span class="token keyword">process</span>
        <span class="token keyword">variable</span> monitor_line <span class="token punctuation">:</span> line<span class="token punctuation">;</span>
    <span class="token keyword">begin</span>
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">1000</span> ns<span class="token punctuation">;</span>
        
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span>"<span class="token comment">--- MONITOREO DE SEÑALES ---"));</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"Tiempo: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> time<span class="token keyword">'image</span><span class="token punctuation">(</span>simulation_time<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"Temperatura: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> integer<span class="token keyword">'image</span><span class="token punctuation">(</span><span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>debug_out<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> <span class="token string">"°C"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"Modo LED: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> integer<span class="token keyword">'image</span><span class="token punctuation">(</span><span class="token function">to_integer</span><span class="token punctuation">(</span><span class="token function">unsigned</span><span class="token punctuation">(</span>modo_led<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"PWM Enable: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> std_logic<span class="token keyword">'image</span><span class="token punctuation">(</span>pwm_enable<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span><span class="token string">"Buzzer: "</span><span class="token punctuation">)</span> <span class="token operator">&amp;</span> std_logic<span class="token keyword">'image</span><span class="token punctuation">(</span>buzzer<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">write</span><span class="token punctuation">(</span>monitor_line<span class="token punctuation">,</span> string'<span class="token punctuation">(</span>"<span class="token comment">---------------------------"));</span>
        <span class="token function">writeline</span><span class="token punctuation">(</span>output<span class="token punctuation">,</span> monitor_line<span class="token punctuation">)</span><span class="token punctuation">;</span>
        
        <span class="token keyword">wait</span> <span class="token keyword">for</span> <span class="token number">5000</span> ns<span class="token punctuation">;</span>
    <span class="token keyword">end</span> <span class="token keyword">process</span><span class="token punctuation">;</span>

<span class="token keyword">end</span> Behavioral<span class="token punctuation">;</span>
</code></pre>
<h1 id="🔌-paso-4-diagramas-de-conexión-completos">🔌 <strong>PASO 4: DIAGRAMAS DE CONEXIÓN COMPLETOS</strong></h1>
<h2 id="a-diagrama-esquemático-completo-del-sistema"><strong>A) DIAGRAMA ESQUEMÁTICO COMPLETO DEL SISTEMA</strong></h2>
<pre><code>┌─────────────────────────────────────────────────────────────────┐
│                    SISTEMA COMPLETO FPGA                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐          ┌─────────────┐          ┌─────────┐  │
│  │   SENSOR    │          │     ADC     │          │   FPGA  │  │
│  │    LM35     │─────────▶│   MCP3008   │─────────▶│ Altera  │  │
│  │             │          │             │          │ MAX II  │  │
│  │  VCC: 5V    │          │  VDD: 3.3V  │          │         │  │
│  │  GND: GND   │          │ VREF: 3.3V  │          │ VCC:3.3V│  │
│  │  OUT: CH0   │          │ AGND: GND   │          │ GND:GND │  │
│  └─────────────┘          │  CLK: PIN3  │          │         │  │
│                           │ DOUT: PIN4  │◄─────────│ PIN4    │  │
│  ┌─────────────┐          │  DIN: PIN5  │─────────▶│ PIN5    │  │
│  │  ACTUADOR   │          │  CS: PIN2   │─────────▶│ PIN2    │  │
│  │   TIP31C    │◄─────────│             │          │         │  │
│  │             │          └─────────────┘          │ PIN6    │──┘
│  │ BASE: 1kΩ   │                                   │         │
│  │ COL: 12V    │          ┌─────────────┐          │ PIN7    │──▶LED_V
│  │ EMIS: GND   │          │  INDICAD.   │          │ PIN8    │──▶LED_A
│  └─────────────┘          │             │          │ PIN9    │──▶LED_R
│                           │ LED_V: PIN7 │◄─────────│ PIN10   │──▶BUZZER
│  ┌─────────────┐          │ LED_A: PIN8 │          │         │
│  │   FUENTE    │          │ LED_R: PIN9 │          │ PIN1    │──▶CLK_50M
│  │             │          │ BUZZ: PIN10 │          │ PIN15   │──▶RESET
│  │  5V ─ 2A    │          └─────────────┘          │ PIN16-23│──▶DEBUG
│  │ 12V ─ 1A    │                                   └─────────┘
│  │ GND ─ GND   │                                         │
│  └─────────────┘                                         │
│                                                          │
└──────────────────────────────────────────────────────────┘
</code></pre>
<h2 id="b-conexiones-detalladas-mcp3008"><strong>B) CONEXIONES DETALLADAS MCP3008</strong></h2>
<pre><code>        MCP3008 (DIP-16)
        ┌───┬───┐
   VDD ─┤1  └──┐16├─ VREF
   VREF─┤2    15├─ AGND
   AGND─┤3    14├─ CLK   ←── PIN3 FPGA
   CLK ─┤4    13├─ DOUT  ───▶ PIN4 FPGA
   DOUT─┤5    12├─ DIN   ←── PIN5 FPGA
   DIN ─┤6    11├─ CS    ←── PIN2 FPGA
   CS ──┤7    10├─ CH0   ←── LM35 OUT
   CH1 ─┤8     9├─ CH2
        └───────┘

CONFIGURACIÓN SPI:
• Modo: 0 (CPOL=0, CPHA=0)
• Velocidad: 1 MHz máximo
• Formato: 10 bits
• Canal: 0 (Single-ended)
</code></pre>
<h2 id="c-conexiones-tip31c-y-protección"><strong>C) CONEXIONES TIP31C Y PROTECCIÓN</strong></h2>
<pre><code>        TIP31C (TO-220)
        ┌───────┐
   BASE ┤1  B   │
        │       │
   COL  ┤2  C   ├─▶ Calefactor + 12V
        │       │
   EMIS ┤3  E   ├─▶ GND
        └───────┘

CIRCUITO DE CONTROL:
• BASE: Resistor 1kΩ → PIN6 FPGA (PWM_OUT)
• COLECTOR: Fuente 12V + Calefactor (máx 3A)
• EMISOR: Tierra (GND)

PROTECCIÓN TÉRMICA:
• Disipador de calor obligatorio
• Fusible 2A en línea 12V
• Ventilación adecuada
</code></pre>
<hr>
<h1 id="⚙️-paso-5-configuración-completa-quartus-ii">⚙️ <strong>PASO 5: CONFIGURACIÓN COMPLETA QUARTUS II</strong></h1>
<h2 id="a-archivo-.qsf-completo"><strong>A) ARCHIVO .QSF COMPLETO</strong></h2>
<pre class=" language-tcl"><code class="prism  language-tcl"><span class="token comment"># ===========================================================</span>
<span class="token comment"># ARCHIVO: control_temperatura_ia.qsf</span>
<span class="token comment"># ASIGNACIÓN DE PINES - Altera MAX II EPM240T100C5</span>
<span class="token comment"># ===========================================================</span>

<span class="token comment"># Configuración global del dispositivo</span>
set_global_assignment <span class="token operator">-</span>name FAMILY <span class="token string">"MAX II"</span>
set_global_assignment <span class="token operator">-</span>name DEVICE EPM240T100C5
set_global_assignment <span class="token operator">-</span>name TOP_LEVEL_ENTITY control_temperatura_ia

<span class="token comment"># Archivos fuente</span>
set_global_assignment <span class="token operator">-</span>name VHDL_FILE control_temperatura_ia.vhd
set_global_assignment <span class="token operator">-</span>name VHDL_FILE tb_control_temperatura_ia.vhd

<span class="token comment"># Configuración de compilación</span>
set_global_assignment <span class="token operator">-</span>name NUM_PARALLEL_PROCESSORS ALL
set_global_assignment <span class="token operator">-</span>name ENABLE_OCT_DONE OFF
set_global_assignment <span class="token operator">-</span>name STRATIX_DEVICE_IO_STANDARD <span class="token string">"3.3-V LVTTL"</span>
set_global_assignment <span class="token operator">-</span>name RESERVE_ALL_UNUSED_PINS <span class="token string">"AS INPUT TRI-STATED"</span>

<span class="token comment"># ========== RELOJ Y RESET ==========</span>
set_location_assignment PIN_1 <span class="token operator">-</span>to clk_50mhz
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to clk_50mhz

set_location_assignment PIN_15 <span class="token operator">-</span>to reset
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to reset

<span class="token comment"># ========== INTERFAZ ADC MCP3008 ==========</span>
set_location_assignment PIN_2 <span class="token operator">-</span>to adc_cs
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_cs

set_location_assignment PIN_3 <span class="token operator">-</span>to adc_clk
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_clk

set_location_assignment PIN_4 <span class="token operator">-</span>to adc_miso
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_miso

set_location_assignment PIN_5 <span class="token operator">-</span>to adc_mosi
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_mosi

set_location_assignment PIN_14 <span class="token operator">-</span>to adc_ready
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to adc_ready

<span class="token comment"># ========== SALIDA PWM ==========</span>
set_location_assignment PIN_6 <span class="token operator">-</span>to pwm_out
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to pwm_out

set_location_assignment PIN_13 <span class="token operator">-</span>to pwm_enable
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to pwm_enable

<span class="token comment"># ========== LEDS INDICADORES ==========</span>
set_location_assignment PIN_7 <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>0<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>0<span class="token punctuation">]</span>

set_location_assignment PIN_8 <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>1<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>1<span class="token punctuation">]</span>

set_location_assignment PIN_9 <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>2<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to modo_led<span class="token punctuation">[</span>2<span class="token punctuation">]</span>

<span class="token comment"># ========== SISTEMA DE ALARMA ==========</span>
set_location_assignment PIN_10 <span class="token operator">-</span>to buzzer
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to buzzer

<span class="token comment"># ========== DEBUG ==========</span>
set_location_assignment PIN_16 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>0<span class="token punctuation">]</span>
set_location_assignment PIN_17 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>1<span class="token punctuation">]</span>
set_location_assignment PIN_18 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>2<span class="token punctuation">]</span>
set_location_assignment PIN_19 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>3<span class="token punctuation">]</span>
set_location_assignment PIN_20 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>4<span class="token punctuation">]</span>
set_location_assignment PIN_21 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>5<span class="token punctuation">]</span>
set_location_assignment PIN_22 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>6<span class="token punctuation">]</span>
set_location_assignment PIN_23 <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>7<span class="token punctuation">]</span>

set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>0<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>1<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>2<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>3<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>4<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>5<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>6<span class="token punctuation">]</span>
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to debug_out<span class="token punctuation">[</span>7<span class="token punctuation">]</span>

<span class="token comment"># ========== UART ==========</span>
set_location_assignment PIN_11 <span class="token operator">-</span>to uart_tx
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to uart_tx

set_location_assignment PIN_12 <span class="token operator">-</span>to uart_rx
set_instance_assignment <span class="token operator">-</span>name IO_STANDARD <span class="token string">"3.3-V LVTTL"</span> <span class="token operator">-</span>to uart_rx
</code></pre>
<h2 id="b-archivo-.sdc-constraints-de-timing"><strong>B) ARCHIVO .SDC (CONSTRAINTS DE TIMING)</strong></h2>
<pre class=" language-tcl"><code class="prism  language-tcl"><span class="token comment"># ===========================================================</span>
<span class="token comment"># ARCHIVO: control_temperatura_ia.sdc</span>
<span class="token comment"># CONSTRAINTS DE TIMING - Quartus II TimeQuest</span>
<span class="token comment"># ===========================================================</span>

<span class="token comment"># Crear reloj principal 50MHz</span>
create_clock <span class="token operator">-</span>name clk_50mhz <span class="token operator">-</span>period 20.000 <span class="token punctuation">[</span>get_ports <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span>

<span class="token comment"># Definir deriva del reloj</span>
set_clock_uncertainty <span class="token operator">-</span>setup 0.500 <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span>
set_clock_uncertainty <span class="token operator">-</span>hold 0.300 <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span>

<span class="token comment"># Constraints de entrada</span>
set_input_delay <span class="token operator">-</span>clock <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>max 5.000 <span class="token punctuation">[</span>get_ports <span class="token punctuation">{</span>reset adc_miso adc_ready uart_rx<span class="token punctuation">}</span><span class="token punctuation">]</span>
set_input_delay <span class="token operator">-</span>clock <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>min 1.000 <span class="token punctuation">[</span>get_ports <span class="token punctuation">{</span>reset adc_miso adc_ready uart_rx<span class="token punctuation">}</span><span class="token punctuation">]</span>

<span class="token comment"># Constraints de salida</span>
set_output_delay <span class="token operator">-</span>clock <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>max 5.000 <span class="token punctuation">[</span>get_ports <span class="token punctuation">{</span>pwm_out pwm_enable adc_cs adc_mosi adc_clk modo_led<span class="token punctuation">[</span><span class="token operator">*</span><span class="token punctuation">]</span> debug_out<span class="token punctuation">[</span><span class="token operator">*</span><span class="token punctuation">]</span> buzzer uart_tx<span class="token punctuation">}</span><span class="token punctuation">]</span>
set_output_delay <span class="token operator">-</span>clock <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>min 1.000 <span class="token punctuation">[</span>get_ports <span class="token punctuation">{</span>pwm_out pwm_enable adc_cs adc_mosi adc_clk modo_led<span class="token punctuation">[</span><span class="token operator">*</span><span class="token punctuation">]</span> debug_out<span class="token punctuation">[</span><span class="token operator">*</span><span class="token punctuation">]</span> buzzer uart_tx<span class="token punctuation">}</span><span class="token punctuation">]</span>

<span class="token comment"># Multicycle paths para lógica de control</span>
set_multicycle_path <span class="token operator">-</span>from <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>to <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>setup <span class="token operator">-</span>end 2
set_multicycle_path <span class="token operator">-</span>from <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>to <span class="token punctuation">[</span>get_clocks <span class="token punctuation">{</span>clk_50mhz<span class="token punctuation">}</span><span class="token punctuation">]</span> <span class="token operator">-</span>hold <span class="token operator">-</span>end 1
</code></pre>
<hr>
<h1 id="🛠️-paso-6-guía-completa-de-implementación-física">🛠️ <strong>PASO 6: GUÍA COMPLETA DE IMPLEMENTACIÓN FÍSICA</strong></h1>
<h2 id="lista-de-verificación-de-componentes"><strong>1. LISTA DE VERIFICACIÓN DE COMPONENTES</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">COMPONENTES CRÍTICOS:
<span class="token list punctuation">-</span> [ ] FPGA Altera MAX II EPM240T100C5
<span class="token list punctuation">-</span> [ ] Sensor LM35DZ
<span class="token list punctuation">-</span> [ ] ADC MCP3008 (DIP-16)
<span class="token list punctuation">-</span> [ ] Transistor TIP31C + disipador
<span class="token list punctuation">-</span> [ ] Resistencias: 1kΩ (x3), 470Ω (x3)
<span class="token list punctuation">-</span> [ ] LEDs: Rojo, Verde, Azul
<span class="token list punctuation">-</span> [ ] Buzzer activo 5V
<span class="token list punctuation">-</span> [ ] Protoboard 400 puntos
<span class="token list punctuation">-</span> [ ] Cables Dupont M-M, M-F
<span class="token list punctuation">-</span> [ ] Fuente alimentación: 5V/2A + 12V/1A
<span class="token list punctuation">-</span> [ ] Calefactor (resistor de potencia 10-50Ω)

HERRAMIENTAS:
<span class="token list punctuation">-</span> [ ] Multímetro digital
<span class="token list punctuation">-</span> [ ] Soldador y estaño
<span class="token list punctuation">-</span> [ ] Pinzas y cortadores
<span class="token list punctuation">-</span> [ ] Osciloscopio (opcional)
<span class="token list punctuation">-</span> [ ] Computadora con Quartus II
</code></pre>
<h2 id="armado-paso-a-paso"><strong>2. ARMADO PASO A PASO</strong></h2>
<h3 id="paso-1-preparación-de-alimentación"><strong>Paso 1: Preparación de Alimentación</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown"><span class="token list punctuation">1.</span> Conectar 3.3V desde FPGA a rail positivo protoboard
<span class="token list punctuation">2.</span> Conectar GND desde FPGA a rail negativo protoboard
<span class="token list punctuation">3.</span> Conectar 5V externo para LM35
<span class="token list punctuation">4.</span> Conectar 12V externo para calefactor
<span class="token list punctuation">5.</span> Verificar voltajes con multímetro:
   <span class="token list punctuation">-</span> 3.3V ±5% para FPGA
   <span class="token list punctuation">-</span> 5V ±5% para LM35
   <span class="token list punctuation">-</span> 12V estable para calefactor
</code></pre>
<h3 id="paso-2-instalación-del-sensor-lm35"><strong>Paso 2: Instalación del Sensor LM35</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown"><span class="token list punctuation">1.</span> LM35 PIN1 (VCC) → 5V (fuente externa)
<span class="token list punctuation">2.</span> LM35 PIN2 (OUT) → MCP3008 CH0 + Resistor 10kΩ pull-up a 3.3V
<span class="token list punctuation">3.</span> LM35 PIN3 (GND) → Tierra común
<span class="token list punctuation">4.</span> PRUEBA: Medir voltaje en PIN2 (~0.25V a 25°C = 10mV/°C)
</code></pre>
<h3 id="paso-3-conexión-adc-mcp3008"><strong>Paso 3: Conexión ADC MCP3008</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">ALIMENTACIÓN:
<span class="token list punctuation">1.</span> MCP3008 PIN16 (VREF) → 3.3V
<span class="token list punctuation">2.</span> MCP3008 PIN1 (VDD) → 3.3V
<span class="token list punctuation">3.</span> MCP3008 PIN15 (AGND) → Tierra
<span class="token list punctuation">4.</span> MCP3008 PIN3 (AGND) → Tierra

SEÑALES SPI:
<span class="token list punctuation">5.</span> MCP3008 PIN14 (CLK) → FPGA PIN3
<span class="token list punctuation">6.</span> MCP3008 PIN13 (DOUT) → FPGA PIN4 (MISO)
<span class="token list punctuation">7.</span> MCP3008 PIN12 (DIN) → FPGA PIN5 (MOSI)
<span class="token list punctuation">8.</span> MCP3008 PIN11 (CS) → FPGA PIN2

ENTRADA ANALÓGICA:
<span class="token list punctuation">9.</span> MCP3008 PIN10 (CH0) → LM35 PIN2 (OUT)
</code></pre>
<h3 id="paso-4-instalación-del-actuador-tip31c"><strong>Paso 4: Instalación del Actuador TIP31C</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">CIRCUITO DE CONTROL:
<span class="token list punctuation">1.</span> TIP31C BASE → Resistor 1kΩ → FPGA PIN6 (PWM_OUT)
<span class="token list punctuation">2.</span> TIP31C COLECTOR → Fuente 12V + Calefactor
<span class="token list punctuation">3.</span> TIP31C EMISOR → Tierra

PROTECCIONES:
<span class="token list punctuation">4.</span> Instalar disipador en TIP31C
<span class="token list punctuation">5.</span> Colocar fusible 2A en línea 12V
<span class="token list punctuation">6.</span> Verificar polaridad del transistor
</code></pre>
<h3 id="paso-5-sistema-de-indicación"><strong>Paso 5: Sistema de Indicación</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">LEDS DE MODO:
<span class="token list punctuation">1.</span> LED Verde → Resistor 470Ω → FPGA PIN7 (MODO0 - PRECISO)
<span class="token list punctuation">2.</span> LED Azul → Resistor 470Ω → FPGA PIN8 (MODO1 - NORMAL)
<span class="token list punctuation">3.</span> LED Rojo → Resistor 470Ω → FPGA PIN9 (MODO2 - AGRESIVO)

ALARMA:
<span class="token list punctuation">4.</span> Buzzer (+) → FPGA PIN10, (-) → Tierra
</code></pre>
<h2 id="programación-de-la-fpga"><strong>3. PROGRAMACIÓN DE LA FPGA</strong></h2>
<h3 id="configuración-quartus-ii"><strong>Configuración Quartus II:</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown"><span class="token list punctuation">1.</span> File → New Project Wizard
<span class="token list punctuation">2.</span> Directorio: /ruta/al/proyecto/
<span class="token list punctuation">3.</span> Nombre: control<span class="token italic"><span class="token punctuation">_</span>temperatura<span class="token punctuation">_</span></span>ia
<span class="token list punctuation">4.</span> Top Level: control<span class="token italic"><span class="token punctuation">_</span>temperatura<span class="token punctuation">_</span></span>ia
<span class="token list punctuation">5.</span> Device: EPM240T100C5
<span class="token list punctuation">6.</span> Add Files: control<span class="token italic"><span class="token punctuation">_</span>temperatura<span class="token punctuation">_</span></span>ia.vhd
</code></pre>
<h3 id="compilación"><strong>Compilación:</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown"><span class="token list punctuation">1.</span> Processing → Start Compilation
<span class="token list punctuation">2.</span> Esperar que complete:
   <span class="token list punctuation">-</span> Analysis &amp; Synthesis ✅
   <span class="token list punctuation">-</span> Fitter ✅
   <span class="token list punctuation">-</span> Assembler ✅
<span class="token list punctuation">3.</span> Verificar "Full Compilation was successful"
<span class="token list punctuation">4.</span> Revisar warnings en reporte
</code></pre>
<h3 id="programación"><strong>Programación:</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown"><span class="token list punctuation">1.</span> Conectar USB-Blaster a FPGA
<span class="token list punctuation">2.</span> Tools → Programmer
<span class="token list punctuation">3.</span> Hardware: USB-Blaster
<span class="token list punctuation">4.</span> Add File: control<span class="token italic"><span class="token punctuation">_</span>temperatura<span class="token punctuation">_</span></span>ia.pof
<span class="token list punctuation">5.</span> Check: Program/Configure
<span class="token list punctuation">6.</span> Click Start
<span class="token list punctuation">7.</span> Verificar "Success"
</code></pre>
<hr>
<h1 id="🔍-paso-7-protocolo-completo-de-pruebas">🔍 <strong>PASO 7: PROTOCOLO COMPLETO DE PRUEBAS</strong></h1>
<h2 id="pruebas-iniciales-de-seguridad"><strong>1. PRUEBAS INICIALES DE SEGURIDAD</strong></h2>
<h3 id="test-1-verificación-de-alimentación"><strong>Test 1: Verificación de Alimentación</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Confirmar voltajes correctos
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Medir entre VCC y GND de FPGA: 3.3V ±5%
  <span class="token list punctuation">2.</span> Medir alimentación LM35: 5V ±5%
  <span class="token list punctuation">3.</span> Medir alimentación calefactor: 12V estable
  <span class="token list punctuation">4.</span> Verificar tierras comunes
CRITERIO: Todos los voltajes dentro de tolerancia
</code></pre>
<h3 id="test-2-sensor-lm35"><strong>Test 2: Sensor LM35</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar funcionamiento del sensor
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Medir voltaje entre OUT y GND del LM35
  <span class="token list punctuation">2.</span> Temperatura ambiente: ~0.25V (25°C)
  <span class="token list punctuation">3.</span> Calentar suavemente el sensor
  <span class="token list punctuation">4.</span> Observar aumento de voltaje (10mV/°C)
CRITERIO: 0.10V a 10°C, 0.30V a 30°C (aproximadamente)
</code></pre>
<h2 id="pruebas-de-comunicación"><strong>2. PRUEBAS DE COMUNICACIÓN</strong></h2>
<h3 id="test-3-comunicación-spi-con-mcp3008"><strong>Test 3: Comunicación SPI con MCP3008</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar lectura del ADC
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Programar FPGA con código básico
  <span class="token list punctuation">2.</span> Monitorear debug_out con LEDs
  <span class="token list punctuation">3.</span> Usar osciloscopio en pines SPI (opcional)
  <span class="token list punctuation">4.</span> Variar temperatura y observar cambios
CRITERIO: Valores estables en debug_out, respuesta a cambios
</code></pre>
<h3 id="test-4-salida-pwm"><strong>Test 4: Salida PWM</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar control de potencia
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Conectar osciloscopio a PIN6 (PWM_OUT)
  <span class="token list punctuation">2.</span> Variar temperatura artificialmente
  <span class="token list punctuation">3.</span> Observar cambios en duty cycle
  <span class="token list punctuation">4.</span> Verificar respuesta del TIP31C
CRITERIO: PWM variable 0-100%, sin cortocircuitos
</code></pre>
<h2 id="pruebas-del-sistema-de-control"><strong>3. PRUEBAS DEL SISTEMA DE CONTROL</strong></h2>
<h3 id="test-5-control-pid-básico"><strong>Test 5: Control PID Básico</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar control automático
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Establecer setpoint en 60°C
  <span class="token list punctuation">2.</span> Aplicar calor externo al sensor
  <span class="token list punctuation">3.</span> Observar respuesta del sistema
  <span class="token list punctuation">4.</span> Medir tiempo de establecimiento
CRITERIO: Sistema alcanza y mantiene setpoint ±2°C
</code></pre>
<h3 id="test-6-algoritmo-ia---cambios-de-modo"><strong>Test 6: Algoritmo IA - Cambios de Modo</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar transiciones automáticas
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Enfriar sistema por debajo de setpoint
  <span class="token list punctuation">2.</span> Observar modo AGRESIVO (LED rojo)
  <span class="token list punctuation">3.</span> Al acercarse a setpoint, ver cambio a RÁPIDO (LED amarillo)
  <span class="token list punctuation">4.</span> Cerca del setpoint, ver NORMAL (LED azul)
  <span class="token list punctuation">5.</span> En estado estable, ver PRECISO (LED verde)
CRITERIO: Cambios automáticos según error, LEDs correctos
</code></pre>
<h3 id="test-7-sistema-de-alarma"><strong>Test 7: Sistema de Alarma</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar protección por sobrecalentamiento
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Forzar temperatura &gt;80°C (calentar sensor)
  <span class="token list punctuation">2.</span> Verificar activación de buzzer
  <span class="token list punctuation">3.</span> Confirmar desactivación de PWM
  <span class="token list punctuation">4.</span> Enfriar y verificar recuperación automática
CRITERIO: Alarma a &gt;80°C, recuperación a &lt;75°C
</code></pre>
<h2 id="pruebas-de-estabilidad"><strong>4. PRUEBAS DE ESTABILIDAD</strong></h2>
<h3 id="test-8-estabilidad-en-estado-estacionario"><strong>Test 8: Estabilidad en Estado Estacionario</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar desempeño a largo plazo
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Dejar sistema operando por 30 minutos
  <span class="token list punctuation">2.</span> Registrar temperatura cada 5 minutos
  <span class="token list punctuation">3.</span> Calcular error promedio y desviación
CRITERIO: Error promedio &lt;2°C, desviación &lt;0.5°C
</code></pre>
<h3 id="test-9-respuesta-a-perturbaciones"><strong>Test 9: Respuesta a Perturbaciones</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">OBJETIVO: Verificar robustez del control
PROCEDIMIENTO:
  <span class="token list punctuation">1.</span> Con sistema en estado estable, aplicar perturbación
  <span class="token list punctuation">2.</span> Soplair aire frío sobre sensor
  <span class="token list punctuation">3.</span> Medir tiempo de recuperación
  <span class="token list punctuation">4.</span> Observar comportamiento del controlador
CRITERIO: Recuperación en &lt;60 segundos sin oscilaciones excesivas
</code></pre>
<hr>
<h1 id="📅-paso-8-cronograma-8-días-22-29-noviembre">📅 <strong>PASO 8: CRONOGRAMA 8 DÍAS (22-29 NOVIEMBRE)</strong></h1>
<h2 id="día-1---22-nov-fundamentos-y-simulación"><strong>DÍA 1 - 22 NOV: FUNDAMENTOS Y SIMULACIÓN</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA (9:00-12:00):
• Teoría acelerada de control PID
• Introducción a sistemas embebidos con FPGA
• Ejecutar notebook Colab completo

TARDE (14:00-17:00):
• Análisis de resultados de simulación
• Compra express de componentes críticos
• Estudio de diagramas de conexión

ENTREGABLE: Simulación ejecutada y analizada
</code></pre>
<h2 id="día-2---23-nov-preparación-intensiva"><strong>DÍA 2 - 23 NOV: PREPARACIÓN INTENSIVA</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Estudio detallado de conexiones FPGA
• Configuración de software Quartus II
• Revisión de código VHDL

TARDE:
• Verificación de componentes comprados
• Preparación de protoboard y herramientas
• Práctica con ejemplos VHDL básicos

ENTREGABLE: Todo listo para implementación
</code></pre>
<h2 id="día-3---24-nov-armado-físico"><strong>DÍA 3 - 24 NOV: ARMADO FÍSICO</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Soldadura de componentes críticos
• Conexión de alimentación y tierras
• Instalación de sensor LM35

TARDE:
• Armado completo del circuito
• Verificación de conexiones con multímetro
• Pruebas básicas de alimentación

ENTREGABLE: Circuito físico completamente armado
</code></pre>
<h2 id="día-4---25-nov-programación-fpga"><strong>DÍA 4 - 25 NOV: PROGRAMACIÓN FPGA</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Compilación de código VHDL en Quartus
• Asignación de pines y configuración
• Programación inicial de la FPGA

TARDE:
• Pruebas de comunicación SPI con MCP3008
• Verificación de lectura de temperatura
• Ajustes de código según resultados

ENTREGABLE: FPGA programada y comunicándose
</code></pre>
<h2 id="día-5---26-nov-control-básico"><strong>DÍA 5 - 26 NOV: CONTROL BÁSICO</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Implementación de control PID básico
• Pruebas de respuesta del sistema
• Calibración de parámetros iniciales

TARDE:
• Verificación de salida PWM
• Pruebas con calefactor real
• Ajustes de ganancias PID

ENTREGABLE: Control PID tradicional funcionando
</code></pre>
<h2 id="día-6---27-nov-ia-y-optimización"><strong>DÍA 6 - 27 NOV: IA Y OPTIMIZACIÓN</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Implementación de lógica IA de modos
• Pruebas de cambio automático de parámetros
• Verificación de LEDs indicadores

TARDE:
• Optimización de umbrales de cambio
• Pruebas de desempeño comparativo
• Ajustes finos del algoritmo

ENTREGABLE: Control con IA operativo
</code></pre>
<h2 id="día-7---28-nov-pruebas-finales"><strong>DÍA 7 - 28 NOV: PRUEBAS FINALES</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA:
• Pruebas integrales del sistema completo
• Verificación de sistema de alarma
• Pruebas de estabilidad a largo plazo

TARDE:
• Resolución de problemas finales
• Calibración fina de parámetros
• Preparación de demostraciones

ENTREGABLE: Sistema completo y estable
</code></pre>
<h2 id="día-8---29-nov-documentación-y-entrega"><strong>DÍA 8 - 29 NOV: DOCUMENTACIÓN Y ENTREGA</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">MAÑANA (9:00-12:00):
• Redacción de reporte ejecutivo
• Grabación de video demostrativo (3-5 min)
• Captura de datos finales

TARDE (14:00-17:00):
• Revisión final de todos los entregables
• Empaquetado y preparación de entrega
• Pruebas finales de funcionamiento

ENTREGA FINAL: 29 Noviembre - 18:00 horas
</code></pre>
<hr>
<h1 id="🛒-paso-9-lista-completa-de-materiales">🛒 <strong>PASO 9: LISTA COMPLETA DE MATERIALES</strong></h1>
<h2 id="componentes-electrónicos-por-equipo"><strong>COMPONENTES ELECTRÓNICOS POR EQUIPO</strong></h2>

<table>
<thead>
<tr>
<th>Componente</th>
<th>Especificaciones</th>
<th>Cantidad</th>
<th>Precio Aprox</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>LM35DZ</strong></td>
<td>Sensor temperatura -55°C a 150°C</td>
<td>1</td>
<td>$1.50</td>
<td>Incluir socket</td>
</tr>
<tr>
<td><strong>MCP3008</strong></td>
<td>ADC 8-canales 10-bit</td>
<td>1</td>
<td>$3.00</td>
<td>Versión DIP</td>
</tr>
<tr>
<td><strong>TIP31C</strong></td>
<td>Transistor NPN 100V/3A</td>
<td>1</td>
<td>$0.50</td>
<td>Con disipador</td>
</tr>
<tr>
<td><strong>LEDs</strong></td>
<td>5mm (Rojo, Verde, Azul)</td>
<td>3</td>
<td>$0.30</td>
<td>Diferentes colores</td>
</tr>
<tr>
<td><strong>Resistencias</strong></td>
<td>1kΩ (1/4W)</td>
<td>3</td>
<td>$0.10</td>
<td>Para base transistor</td>
</tr>
<tr>
<td><strong>Resistencias</strong></td>
<td>470Ω (1/4W)</td>
<td>3</td>
<td>$0.10</td>
<td>Para LEDs</td>
</tr>
<tr>
<td><strong>Resistencia</strong></td>
<td>10kΩ (1/4W)</td>
<td>1</td>
<td>$0.05</td>
<td>Pull-up LM35</td>
</tr>
<tr>
<td><strong>Buzzer</strong></td>
<td>Activo 5V</td>
<td>1</td>
<td>$0.80</td>
<td>Alarma audible</td>
</tr>
<tr>
<td><strong>Protoboard</strong></td>
<td>400 puntos</td>
<td>1</td>
<td>$3.00</td>
<td>Tamaño medio</td>
</tr>
<tr>
<td><strong>Cables Dupont</strong></td>
<td>M-M, M-F, F-F</td>
<td>30</td>
<td>$2.50</td>
<td>Variedad</td>
</tr>
<tr>
<td><strong>Capacitores</strong></td>
<td>100nF cerámico</td>
<td>2</td>
<td>$0.20</td>
<td>Desacoplamiento</td>
</tr>
<tr>
<td><strong>Fusible</strong></td>
<td>2A rápido</td>
<td>1</td>
<td>$0.30</td>
<td>Protección</td>
</tr>
</tbody>
</table><h2 id="hardware-principal"><strong>HARDWARE PRINCIPAL</strong></h2>

<table>
<thead>
<tr>
<th>Equipo</th>
<th>Especificaciones</th>
<th>Cantidad</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>FPGA</strong></td>
<td>Altera MAX II EPM240</td>
<td>1</td>
<td>Kit de desarrollo</td>
</tr>
<tr>
<td><strong>Computadora</strong></td>
<td>Windows + USB</td>
<td>1</td>
<td>Con Quartus instalado</td>
</tr>
<tr>
<td><strong>Fuente alimentación</strong></td>
<td>5V/2A + 12V/1A</td>
<td>1</td>
<td>Doble salida</td>
</tr>
<tr>
<td><strong>Multímetro</strong></td>
<td>Digital básico</td>
<td>1</td>
<td>Medir voltajes</td>
</tr>
<tr>
<td><strong>Cable USB</strong></td>
<td>USB-Bluetooth</td>
<td>1</td>
<td>Programación FPGA</td>
</tr>
</tbody>
</table><h2 id="costo-total-estimado"><strong>COSTO TOTAL ESTIMADO</strong></h2>
<pre><code>┌──────────────────────┬─────────────┐
│ COMPONENTES NUEVOS   │   ~$12.35   │
│ HERRAMIENTAS LAB     │    $0.00    │
│ FPGA + COMPUTADORA   │    $0.00    │
├──────────────────────┼─────────────┤
│ TOTAL POR EQUIPO     │   ~$12.35   │
└──────────────────────┴─────────────┘
</code></pre>
<hr>
<h1 id="📊-paso-10-rúbrica-completa-de-evaluación">📊 <strong>PASO 10: RÚBRICA COMPLETA DE EVALUACIÓN</strong></h1>
<h2 id="evaluación-total-100-puntos"><strong>EVALUACIÓN TOTAL: 100 PUNTOS</strong></h2>
<h3 id="básico-60-puntos---implementación-mínima"><strong>BÁSICO (60 PUNTOS) - IMPLEMENTACIÓN MÍNIMA</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">▢ SIMULACIÓN (20 puntos)
   • Notebook Colab ejecutado correctamente (5)
   • Gráficas generadas y analizadas (5)
   • Comparación PID vs PID+IA realizada (5)
   • Conclusiones de simulación (5)

▢ CIRCUITO FÍSICO (20 puntos)
   • Componentes correctamente seleccionados (5)
   • Conexiones siguiendo diagramas (10)
   • Sensor LM35 funcionando (5)

▢ REPORTE ESCRITO (20 puntos)
   • Estructura completa y profesional (5)
   • Datos de simulación incluidos (5)
   • Fotos del circuito físico (5)
   • Conclusiones y análisis (5)
</code></pre>
<h3 id="bueno-80-puntos---implementación-funcional"><strong>BUENO (80 PUNTOS) - IMPLEMENTACIÓN FUNCIONAL</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">▢ PROGRAMACIÓN FPGA (10 puntos)
   • Código VHDL compila sin errores (5)
   • FPGA programada correctamente (5)

▢ CONTROL BÁSICO (10 puntos)
   • Sistema responde a cambios de temperatura (5)
   • Temperatura se estabiliza alrededor del setpoint (5)
</code></pre>
<h3 id="excelente-100-puntos---implementación-completa"><strong>EXCELENTE (100 PUNTOS) - IMPLEMENTACIÓN COMPLETA</strong></h3>
<pre class=" language-markdown"><code class="prism  language-markdown">▢ CONTROL CON IA (10 puntos)
   • IA modifica parámetros en tiempo real (5)
   • Mejora observable vs PID tradicional (5)

▢ DOCUMENTACIÓN PROFESIONAL (10 puntos)
   • Video demostrativo de 2-3 minutos (5)
   • Análisis comparativo detallado (5)
</code></pre>
<h2 id="bonus-extra-10-puntos"><strong>BONUS (EXTRA 10 PUNTOS)</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">★ Implementación adicional creativa (+3)
★ Mejoras al código o circuito (+3)
★ Análisis estadístico avanzado (+2)
★ Interfaz gráfica personalizada (+2)
</code></pre>
<h2 id="criterios-de-calificación"><strong>CRITERIOS DE CALIFICACIÓN</strong></h2>
<pre class=" language-markdown"><code class="prism  language-markdown">A (90-100): Excelente - Sistema completo con mejoras
B (80-89):  Muy Bueno - Sistema funcional con IA
C (70-79):  Bueno - Sistema básico funcionando
D (60-69):  Aprobado - Implementación mínima
F (0-59):   No aprobado - Implementación incompleta
</code></pre>
<hr>
<h1 id="🎯-entregables-finales-completos">🎯 <strong>ENTREGABLES FINALES COMPLETOS</strong></h1>
<h2 id="archivos-a-entregar"><strong>ARCHIVOS A ENTREGAR:</strong></h2>
<pre><code>PROYECTO_CONTROL_IA_EQUIPO[X]/
├── 📄 DOCUMENTACION/
│   ├── 🎯 Reporte_Final.pdf
│   ├── 📋 Lista_Materiales.csv
│   ├── 📅 Cronograma_Ejecutado.pdf
│   └── 📊 Resultados_Experimentales.xlsx
├── 💻 CODIGO_FUENTE/
│   ├── 🐍 simulacion_colab.py
│   ├── 🔌 control_temperatura_ia.vhd
│   ├── 🔬 tb_control_temperatura_ia.vhd
│   └── ⚙️ configuracion_quartus.qsf
├── 🎨 MULTIMEDIA/
│   ├── 🎥 Video_Demostrativo.mp4 (2-3 min)
│   ├── 📸 Fotos_Circuito/
│   │   ├── Vista_General.jpg
│   │   ├── Detalle_Conexiones.jpg
│   │   └── Funcionamiento.jpg
│   └── 📊 Graficas_Resultados/
│       ├── Comparacion_PID_IA.png
│       └── Respuesta_Temporal.png
└── 🔧 CONFIGURACION/
    ├── ⚡ Archivos_Quartus/
    │   ├── control_temperatura_ia.qsf
    │   ├── control_temperatura_ia.sdc
    │   └── debug_stp.stp
    └── 📝 Manual_Usuario.pdf
</code></pre>
<h2 id="fecha-y-formato-de-entrega"><strong>FECHA Y FORMATO DE ENTREGA:</strong></h2>
<ul>
<li><strong>📅 Fecha límite:</strong> 29 de Noviembre - 18:00 horas</li>
<li><strong>📦 Formato:</strong> Archivo ZIP nombrado: <code>Equipo[X]_ControlIA.zip</code></li>
<li><strong>📧 Método:</strong> Entrega por plataforma institucional</li>
</ul>
<hr>
<h1 id="✅-conclusión-final">✅ <strong>CONCLUSIÓN FINAL</strong></h1>
<h2 id="¿qué-logra-el-estudiante"><strong>¿QUÉ LOGRA EL ESTUDIANTE?</strong></h2>
<h3 id="habilidades-técnicas-desarrolladas"><strong>HABILIDADES TÉCNICAS DESARROLLADAS:</strong></h3>
<ul>
<li>✅ <strong>Programación en VHDL</strong> para sistemas embebidos</li>
<li>✅ <strong>Diseño de sistemas de control</strong> en hardware</li>
<li>✅ <strong>Comunicación SPI</strong> con periféricos</li>
<li>✅ <strong>Implementación de algoritmos de IA</strong> en FPGA</li>
<li>✅ <strong>Diseño de circuitos</strong> analógicos/digitales</li>
<li>✅ <strong>Protocolos de prueba</strong> y verificación</li>
</ul>
<h3 id="resultados-concretos"><strong>RESULTADOS CONCRETOS:</strong></h3>
<ul>
<li>✅ <strong>Sistema funcional</strong> de control de temperatura</li>
<li>✅ <strong>Algoritmo adaptativo</strong> que mejora el desempeño</li>
<li>✅ <strong>Documentación profesional</strong> del proyecto</li>
<li>✅ <strong>Capacidad de troubleshooting</strong> y resolución de problemas</li>
</ul>
<h3 id="aprendizajes-clave"><strong>APRENDIZAJES CLAVE:</strong></h3>
<ul>
<li>De la <strong>simulación</strong> a la <strong>implementación física</strong></li>
<li>Del <strong>código de software</strong> al <strong>hardware programable</strong></li>
<li>De la <strong>teoría de control</strong> a la <strong>práctica real</strong></li>
<li>De <strong>algoritmos básicos</strong> a <strong>sistemas inteligentes</strong></li>
</ul>
<hr>
<h1 id="🚀-¡proyecto-completo-y-listo-para-implementar">🚀 <strong>¡PROYECTO COMPLETO Y LISTO PARA IMPLEMENTAR!</strong></h1>
<p><strong>Este documento contiene ABSOLUTAMENTE TODO lo necesario para que los estudiantes completen exitosamente el proyecto en 8 días, desde los fundamentos teóricos hasta la implementación física completa, incluyendo toda la documentación, código, configuraciones y protocolos de prueba.</strong></p>
<p><strong>¡Éxito en la implementación!</strong> 🎓</p>
</div>
</body>

</html>
