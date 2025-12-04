# Estrategia Ultra-Confluencia LuxAlgo
## Objetivo: Winrate 80%+ con pocas senales de alta calidad

### Filosofia de la Estrategia
- **Escanear 800 simbolos** -> Obtener **1-2 senales diarias** de ultra-alta probabilidad
- **Multiples confirmaciones obligatorias** antes de disparar alerta
- **Operar con trailing stop** una vez confirmada la entrada

---

## PARTE 1: INDICADORES NECESARIOS

### Indicadores PREMIUM (Obligatorios)

| Indicador | Proposito | Prioridad |
|-----------|-----------|-----------|
| **Signals & Overlays (S&O)** | Senales de confirmacion, Smart Trail, Trend Strength | CRITICO |
| **Price Action Concepts (PAC)** | Order Blocks, FVGs, Estructura de mercado (BOS/CHoCH) | CRITICO |
| **Oscillator Matrix (OM)** | Divergencias, Reversiones, Momentum HyperWave | ALTO |

### Indicadores GRATUITOS (Complementarios)

| Indicador | Proposito |
|-----------|-----------|
| **Smart Money Concepts [LuxAlgo]** | Estructura SMC adicional |
| **Nadaraya-Watson Envelope [LuxAlgo]** | Bandas dinamicas de sobrecompra/venta |
| **Volume Profile** | Confirmar zonas de volumen |

---

## PARTE 2: CONFIGURACION DE CADA INDICADOR

### 2.1 Signals & Overlays (S&O) - CONFIGURACION

```
SIGNALS:
- Signal Mode: Confirmation + Contrarian
- Confirmation Sensitivity: 6-8 (mas selectivo)
- Show Strong Signals Only: ON (solo + signals)

OVERLAYS:
- Smart Trail: ON
- Smart Trail Sensitivity: 8-10 (menos ruido)
- Trend Tracer: ON
- Trend Catcher: ON
- Neo Cloud: ON

FILTERS:
- Trend Strength Filter: ON (minimo 50%)
- Smart Trail Filter: ON
- Reversal Zones: ON

DASHBOARD:
- Show Trend Strength: ON
```

### 2.2 Price Action Concepts (PAC) - CONFIGURACION

```
MARKET STRUCTURE:
- Internal Structure: ON
- Swing Structure: ON
- Show CHoCH: ON (Change of Character - reversiones)
- Show BOS: ON (Break of Structure)
- CHoCH+ Only: ON (mas confirmado)

ORDER BLOCKS:
- Show Order Blocks: ON
- Mitigation Method: Close (mas conservador)
- Show Volume %: ON
- Max Order Blocks: 3-5

FAIR VALUE GAPS:
- Show FVGs: ON
- Auto Threshold: ON (filtra FVGs insignificantes)
- Show Inverse FVGs: ON

LIQUIDITY:
- Trend Line Liquidity: ON
- Show Liquidity Grabs: ON

ZONES:
- Premium/Discount Zones: ON
- Equilibrium Zone: ON
```

### 2.3 Oscillator Matrix (OM) - CONFIGURACION

```
REVERSAL SIGNALS:
- Show Reversal Signals: ON
- Large Arrows Only: ON (solo las grandes triangulares)

HYPER WAVE:
- HyperWave: ON
- Divergence Detection: ON
- Divergence Sensitivity: High

THRESHOLDS:
- Overbought: 80
- Oversold: 20
```

---

## PARTE 3: LOGICA DE CONFLUENCIA (6+ FILTROS)

Para que salte una alerta, TODAS estas condiciones deben cumplirse:

### LONG (Compra)
```
1. Smart Trail = BULLISH (precio sobre el trail)
2. Trend Strength >= 60%
3. Confirmation Signal = Bullish+ (fuerte)
4. Order Block = Bullish OB cercano (soporte institucional)
5. FVG = Price en/cerca de Bullish FVG
6. Market Structure = CHoCH+ bullish O BOS bullish
7. HyperWave < 30 (oversold) O divergencia bullish
8. Precio en DISCOUNT zone (por debajo del equilibrio)
```

### SHORT (Venta)
```
1. Smart Trail = BEARISH (precio bajo el trail)
2. Trend Strength >= 60%
3. Confirmation Signal = Bearish+ (fuerte)
4. Order Block = Bearish OB cercano (resistencia institucional)
5. FVG = Price en/cerca de Bearish FVG
6. Market Structure = CHoCH+ bearish O BOS bearish
7. HyperWave > 70 (overbought) O divergencia bearish
8. Precio en PREMIUM zone (por encima del equilibrio)
```

---

## PARTE 4: ALERT SCRIPTING - SCRIPT COMPLETO

### SCRIPT PARA SENALES LONG (Ultra-Confluencia)

Pegar este codigo en el campo **"Alert Scripting"** del indicador S&O:

```
// ============================================
// LUXALGO ULTRA-CONFLUENCIA - LONG SIGNALS
// Winrate Target: 80%+
// ============================================

// PASO 1: Smart Trail Bullish (OBLIGATORIO)
{bullish_smart_trail}

// PASO 2: Trend Strength >= 60 (OBLIGATORIO)
and {trend_strength} >= 60

// PASO 3: Senal de Confirmacion Fuerte (OBLIGATORIO)
and {bullish_confirmation+}

// PASO 4: Dentro de Reversal Zone inferior O cerca de soporte
and ({lower_reversal_zone} or {bullish_tracer})

// PASO 5: Neo Cloud Bullish
and {bullish_cloud}

// PASO 6: Trend Catcher confirma
and {bullish_catcher}

// ACTION: Crear alerta cuando todo se cumple
@alert() = {bullish_smart_trail} and {trend_strength} >= 60 and {bullish_confirmation+} and {bullish_catcher} and {bullish_cloud}
```

### SCRIPT PARA SENALES SHORT (Ultra-Confluencia)

```
// ============================================
// LUXALGO ULTRA-CONFLUENCIA - SHORT SIGNALS
// Winrate Target: 80%+
// ============================================

// PASO 1: Smart Trail Bearish (OBLIGATORIO)
{bearish_smart_trail}

// PASO 2: Trend Strength >= 60 (OBLIGATORIO)
and {trend_strength} >= 60

// PASO 3: Senal de Confirmacion Fuerte (OBLIGATORIO)
and {bearish_confirmation+}

// PASO 4: Dentro de Reversal Zone superior O cerca de resistencia
and ({upper_reversal_zone} or {bearish_tracer})

// PASO 5: Neo Cloud Bearish
and {bearish_cloud}

// PASO 6: Trend Catcher confirma
and {bearish_catcher}

// ACTION: Crear alerta cuando todo se cumple
@alert() = {bearish_smart_trail} and {trend_strength} >= 60 and {bearish_confirmation+} and {bearish_catcher} and {bearish_cloud}
```

### SCRIPT COMBINADO (LONG + SHORT en uno)

```
// ============================================
// LUXALGO ULTRA-CONFLUENCIA - ALL SIGNALS
// Escaneo de 800 simbolos -> 1-2 alertas/dia
// ============================================

// LONG ULTRA-CONFIRMADO
@alert(message="LONG ULTRA: {{ticker}} - TF: {{interval}}") =
    {bullish_smart_trail}
    and {trend_strength} >= 60
    and {bullish_confirmation+}
    and {bullish_catcher}
    and {bullish_cloud}
    and {lower_reversal_zone}

// SHORT ULTRA-CONFIRMADO
@alert(message="SHORT ULTRA: {{ticker}} - TF: {{interval}}") =
    {bearish_smart_trail}
    and {trend_strength} >= 60
    and {bearish_confirmation+}
    and {bearish_catcher}
    and {bearish_cloud}
    and {upper_reversal_zone}

// INVALIDACION: Reset si Smart Trail cambia
@invalidate() = {bullish_smart_trail} and {bearish_smart_trail[1]}
@invalidate() = {bearish_smart_trail} and {bullish_smart_trail[1]}
```

---

## PARTE 5: CONFIGURACION DEL CUSTOM ALERT CREATOR (Alternativa GUI)

Si prefieres usar la interfaz grafica en lugar de Alert Scripting:

### Modo: MATCH (todas las condiciones simultaneas)

| Step | Condicion | Configuracion |
|------|-----------|---------------|
| 1 | Smart Trail | Bullish/Bearish |
| 1 | Trend Strength | >= 60 |
| 1 | Confirmation | Strong (+) Only |
| 1 | Trend Catcher | Same Direction |
| 1 | Neo Cloud | Same Direction |
| 1 | Reversal Zone | Active |

### Filtros Adicionales:
- **Invalidate On Step 1**: ON
- **Invalidate On Any Repeated Step**: ON

---

## PARTE 6: INTEGRACION CON PRICE ACTION CONCEPTS

Para anadir confluencia con PAC, usa el **Custom Alert Creator de PAC**:

### Configuracion PAC Alert Creator

| Step | Condicion |
|------|-----------|
| 1 | CHoCH+ Bullish/Bearish (estructura confirmada) |
| 2 | Price near Order Block |
| 3 | FVG present |

### Combinar alertas de ambos indicadores:
1. Crea alerta en S&O con el script anterior
2. Crea alerta en PAC con CHoCH+ y Order Blocks
3. Usa un servicio externo (TradingView webhook + bot) para cruzar ambas alertas

---

## PARTE 7: TIMEFRAMES RECOMENDADOS

| Tipo de Trading | Timeframe Principal | Confirmacion |
|-----------------|---------------------|--------------|
| Swing Trading | 4H | 1D |
| Day Trading | 1H | 4H |
| Scalping (no recomendado para 80% WR) | 15m | 1H |

**RECOMENDACION**: Para 800 simbolos con pocas senales, usa **4H o 1D**.

---

## PARTE 8: FLUJO DE OPERACION

```
1. ALERTA SALTA (ultra-confluencia confirmada)
           |
           v
2. VERIFICAR MANUALMENTE:
   - Order Block de PAC visible?
   - FVG sin mitigar?
   - Estructura CHoCH+ reciente?
           |
           v
3. SI TODO OK -> ENTRADA
   - Entry: Precio actual o retroceso a OB
   - Stop Loss: Detras del Order Block
   - Take Profit: Siguiente zona de liquidez
           |
           v
4. GESTION CON TRAILING STOP
   - Usar Smart Trail como trailing dinamico
   - Mover SL a breakeven en +1R
   - Trail con Smart Trail hasta salida
```

---

## PARTE 9: CHECKLIST PRE-ENTRADA

Antes de operar cualquier alerta, verifica:

- [ ] Smart Trail en direccion correcta
- [ ] Trend Strength >= 60%
- [ ] Senal Confirmation+ visible
- [ ] Order Block institucional presente (PAC)
- [ ] FVG sin mitigar en la zona (PAC)
- [ ] CHoCH+ o BOS reciente (PAC)
- [ ] No hay resistencia/soporte mayor inmediato
- [ ] Volumen acompana el movimiento
- [ ] No hay noticias de alto impacto proximas

---

## PARTE 10: METRICAS ESPERADAS

| Metrica | Objetivo |
|---------|----------|
| Winrate | 75-85% |
| Senales/dia (800 simbolos) | 1-3 |
| Risk:Reward minimo | 1:2 |
| Drawdown maximo | 5-10% |

---

## NOTAS IMPORTANTES

1. **Backtesting**: Usa LUCID de LuxAlgo para backtestear esta estrategia
2. **Paper Trading**: Prueba 2-4 semanas antes de operar en real
3. **Ajuste de sensibilidad**: Si obtienes 0 senales, baja Trend Strength a 50
4. **Muchas senales**: Si obtienes mas de 5/dia, sube Trend Strength a 70

---

## PLACEHOLDERS DISPONIBLES EN ALERT SCRIPTING (Referencia)

### Signals & Overlays
```
{bullish_confirmation}     - Confirmacion bullish
{bearish_confirmation}     - Confirmacion bearish
{bullish_confirmation+}    - Confirmacion bullish FUERTE
{bearish_confirmation+}    - Confirmacion bearish FUERTE
{bullish_contrarian}       - Contrariano bullish
{bearish_contrarian}       - Contrariano bearish
{bullish_smart_trail}      - Smart Trail bullish
{bearish_smart_trail}      - Smart Trail bearish
{bullish_tracer}           - Trend Tracer bullish
{bearish_tracer}           - Trend Tracer bearish
{bullish_catcher}          - Trend Catcher bullish
{bearish_catcher}          - Trend Catcher bearish
{bullish_cloud}            - Neo Cloud bullish
{bearish_cloud}            - Neo Cloud bearish
{upper_reversal_zone}      - En zona de reversion superior
{lower_reversal_zone}      - En zona de reversion inferior
{trend_strength}           - Valor numerico 0-100
```

### Operadores
```
and                        - Y logico
or                         - O logico
not                        - Negacion
>=, <=, >, <, ==           - Comparadores
[1], [2], etc              - Valores anteriores (barras atras)
```

### Actions
```
@alert(message="...")      - Disparar alerta con mensaje
@filter(steps="1,2")       - Aplicar filtro a pasos especificos
@invalidate()              - Condicion de invalidacion
@line(...)                 - Dibujar linea
@label(...)                - Dibujar etiqueta
```
