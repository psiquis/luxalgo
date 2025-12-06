# Champion Traders V2 - Referencia Rápida

## ⚡ Configuración Rápida (Copy-Paste)

### 🟢 Perfil Conservador
```
═══ TRAILING STOP ═══
Activar Trailing Stop: ✓
Tipo de Trailing: ATR
Trailing ATR Multiplicador: 3.0
Activar trail en R múltiplo: 2.0
Mover a B/E cuando trail activo: ✓

═══ GESTIÓN DE RIESGO ═══
Stop Loss %: 6%
Ratio Riesgo/Beneficio: 3.5

═══ VCP PATTERN ═══
Umbral de contracción ATR: 0.5

═══ RELATIVE STRENGTH ═══
RS Rating Mínimo: 75
```

### 🟡 Perfil Balanceado (Recomendado)
```
═══ TRAILING STOP ═══
Activar Trailing Stop: ✓
Tipo de Trailing: ATR
Trailing ATR Multiplicador: 2.5
Activar trail en R múltiplo: 1.5
Mover a B/E cuando trail activo: ✓

═══ GESTIÓN DE RIESGO ═══
Stop Loss %: 7%
Ratio Riesgo/Beneficio: 3.0

═══ VCP PATTERN ═══
Umbral de contracción ATR: 0.6

═══ RELATIVE STRENGTH ═══
RS Rating Mínimo: 70
```

### 🔴 Perfil Agresivo
```
═══ TRAILING STOP ═══
Activar Trailing Stop: ✓
Tipo de Trailing: Percentage
Trailing % desde máximo: 2.5%
Activar trail en R múltiplo: 1.0
Mover a B/E cuando trail activo: ✗

═══ GESTIÓN DE RIESGO ═══
Stop Loss %: 8%
Ratio Riesgo/Beneficio: 2.5

═══ VCP PATTERN ═══
Umbral de contracción ATR: 0.7

═══ RELATIVE STRENGTH ═══
RS Rating Mínimo: 65
```

---

## 🎯 Checklist Pre-Entrada

Antes de tomar una señal, verifica:

- [ ] **Trend Template:** Verde (✓ ACTIVO)
- [ ] **RS Rating:** ≥ 70 (verde)
- [ ] **VCP Pattern:** ✓ Detectado
- [ ] **Vol Ratio:** ≥ 1.5x (verde)
- [ ] **Acumulación:** ✓ SÍ
- [ ] **Dist. 52W High:** < 25%
- [ ] **Dist. 52W Low:** > 30%
- [ ] **Volumen promedio:** Verificar en tabla
- [ ] **Contexto de mercado:** SPY/QQQ en tendencia alcista
- [ ] **Noticias:** No hay earnings próximos ni noticias negativas

---

## 📊 Interpretación de la Tabla

### Columna "STATUS"

| Indicador | ✓ Óptimo | ⚠️ Aceptable | ✗ Evitar |
|-----------|----------|--------------|----------|
| **Trend Template** | ✓ ACTIVO | - | ✗ Inactivo |
| **RS Rating** | 80-100 | 70-79 | < 70 |
| **VCP Pattern** | ✓ Detectado | - | ✗ No |
| **Vol Ratio** | > 1.5x | 1.2-1.5x | < 1.2x |
| **Acumulación** | ✓ SÍ | - | ✗ NO |
| **Dist 52W High** | 0-15% | 15-25% | > 25% |
| **Dist 52W Low** | > 50% | 30-50% | < 30% |
| **POSICIÓN** | > 1.5R | 0-1.5R | < 0R |

---

## 🛡️ Gestión de Posición en Vivo

### Al Abrir Posición
1. Verifica entrada en gráfico (triángulo verde ▲)
2. Nota precio de entrada (línea azul)
3. Confirma stop loss (línea roja)
4. Identifica take profit (línea verde)
5. Observa ATR Ratio en tabla

### Durante la Posición
**Monitorea en la tabla:**
- **POSICIÓN:** Múltiplo R actual
- **P&L:** Ganancia/pérdida en %

**Fases del trailing:**
```
0R → 1.5R: Stop fijo en nivel inicial
1.5R →: Trailing ACTIVO
        - Stop sube con el precio
        - Línea roja sube gradualmente
2.0R →: Stop en breakeven (si configurado)
```

### Señales de Salida
- **Stop tocado:** Salida automática por línea roja
- **Take Profit:** Salida automática en objetivo verde
- **MA50 Break:** Precio cierra bajo MA50 azul
- **Trailing:** Precio retrocede y toca trailing stop

---

## 🔧 Solución Rápida de Problemas

### Sin señales hace tiempo
```
Acciones:
1. Bajar RS Rating a 65
2. Subir VCP Umbral a 0.7
3. Desactivar "Requerir ruptura volumen"
4. Verificar que MA200 sube en el activo
```

### Muchas señales falsas
```
Acciones:
1. Subir RS Rating a 75-80
2. Bajar VCP Umbral a 0.5
3. Activar "Requerir ruptura volumen"
4. Subir Vol Multiplicador a 2.0
```

### Trailing muy ajustado (salidas prematuras)
```
Acciones:
1. Subir ATR Multiplicador a 3.0-3.5
2. O subir % Trailing a 4-5%
3. Activar trailing más tarde (2.0R)
4. Desactivar "Mover a B/E"
```

### Trailing muy suelto (devuelve ganancias)
```
Acciones:
1. Bajar ATR Multiplicador a 2.0
2. O bajar % Trailing a 2-2.5%
3. Activar trailing antes (1.0R)
4. Activar "Mover a B/E"
```

---

## 📈 Timeframes & Activos

### Timeframes Recomendados

| Timeframe | Estilo | Señales/mes | Hold Time | Ventajas |
|-----------|--------|-------------|-----------|----------|
| **1D** | Swing | 2-5 | 2-6 semanas | Menos ruido, alta calidad |
| **4H** | Swing | 4-10 | 3-10 días | Balance señales/calidad |
| **1H** | Intraday | 8-20 | 1-3 días | Más oportunidades |

### Activos Óptimos

**✅ MEJORES:**
- Acciones growth tech (AAPL, MSFT, NVDA, GOOGL)
- Líderes de sector en tendencia
- Alta capitalización + volumen
- Acciones con RS > 80

**⚠️ USAR CON CUIDADO:**
- Small caps volátiles
- Acciones < $10
- Volumen bajo < 500k/día
- Sectores en declive

**❌ EVITAR:**
- Penny stocks (< $5)
- Volumen < 100k/día
- Acciones en downtrend
- ETFs inversos/apalancados

---

## 💰 Cálculo de Tamaño de Posición

### Método 1: % de Riesgo Fijo
```
Capital total: $100,000
Riesgo por trade: 1.5% = $1,500
Precio entrada: $150
Stop loss: 7% → $150 × 0.93 = $139.50
Riesgo por acción: $150 - $139.50 = $10.50

Acciones = Riesgo Total / Riesgo por Acción
Acciones = $1,500 / $10.50 = 142 acciones

Inversión = 142 × $150 = $21,300 (21.3% del capital)
```

### Método 2: % de Capital Fijo
```
Capital total: $100,000
% asignado: 10%
Inversión: $10,000
Precio entrada: $150

Acciones = $10,000 / $150 = 66 acciones
Stop loss: 7% → $139.50
Riesgo por acción: $10.50
Riesgo total: 66 × $10.50 = $693 (0.69% del capital)
```

**Recomendación:** Usar Método 1 para riesgo controlado

---

## 📋 Template de Diario de Trading

```
Fecha: ___________
Activo: ___________
Timeframe: ___________

ENTRADA:
- Precio: $_______
- Razón: _________________________
- Trend Template: ☐ ✓
- RS Rating: _____
- VCP: ☐ ✓
- Vol Ratio: ____x
- Setup: _________________________

GESTIÓN:
- Stop inicial: $_______
- Target: $_______
- Tamaño posición: _____ acciones
- Riesgo total: $_______
- Trailing activado en: _____ R

SALIDA:
- Precio: $_______
- Razón: _________________________
- R obtenido: _____
- Días en operación: _____
- P&L: $_______

NOTAS:
_________________________________
_________________________________
_________________________________

LECCIONES:
_________________________________
_________________________________
_________________________________
```

---

## 🎯 Metas Realistas

### Por Mes (Balanceado)
- Operaciones: 3-8
- Win Rate: 40-50%
- Average R: 1.5-2.5R
- Return: 3-8%

### Por Trimestre
- Operaciones: 10-25
- Win Rate: 45-55%
- Average R: 1.8-2.8R
- Return: 10-25%

### Por Año
- Operaciones: 40-100
- Win Rate: 45-55%
- Average R: 2.0-3.0R
- Return: 30-80%

**Nota:** Estos son rangos esperados. Resultados varían según mercado y disciplina.

---

## ⚠️ Reglas de Oro

1. **NUNCA** operar sin stop loss
2. **NUNCA** mover stop loss a favor de posición perdedora
3. **NUNCA** arriesgar > 2% en un trade
4. **SIEMPRE** respetar el trailing stop
5. **SIEMPRE** usar el checklist pre-entrada
6. **SIEMPRE** llevar diario de operaciones
7. **NO** operar durante earnings
8. **NO** operar noticias importantes (Fed, CPI, etc)
9. **ESPERAR** señales de calidad
10. **REVISAR** configuración cada mes

---

## 🔄 Rutina Diaria/Semanal

### Diaria (5-10 min)
- [ ] Revisar posiciones abiertas
- [ ] Verificar trailing stops
- [ ] Escanear señales nuevas
- [ ] Actualizar diario si hay trades

### Semanal (30-60 min)
- [ ] Revisar performance de la semana
- [ ] Analizar trades ganadores/perdedores
- [ ] Ajustar watchlist de activos
- [ ] Verificar contexto de mercado (SPY, QQQ)
- [ ] Planificar semana siguiente

### Mensual (2-3 horas)
- [ ] Análisis completo de métricas
- [ ] Revisar y ajustar parámetros si necesario
- [ ] Backtest con nuevos datos
- [ ] Actualizar plan de trading
- [ ] Revisar objetivos

---

**Última actualización:** Diciembre 2024
**Versión:** 2.0
