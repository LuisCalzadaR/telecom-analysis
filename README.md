# Resumen Ejecutivo — Análisis de Clientes ConnectaTel
**Preparado por:** Luis Eder Calzada Ramírez | Analista de Datos  
**Período analizado:** 2022 – 2024  
**Base de clientes:** 4,000 usuarios | 40,000 eventos de uso

---

## ⚠️ Calidad de los Datos

Antes del análisis se identificaron y corrigieron los siguientes problemas:

| Problema | Columna | Registros afectados | Acción tomada |
|---|---|---|---|
| Sentinel imposible | `age = -999` | 55 (1.4%) | Reemplazado con mediana (48 años) |
| Valor inválido | `city = "?"` | 96 (2.4%) | Reemplazado con nulo |
| Fecha futura | `reg_date = 2026` | 40 (1.0%) | Marcado como nulo |
| Nulos esperados | `churn_date` | 3,534 (88.4%) | Ignorado — usuarios activos |

> Los datos son confiables para el análisis tras la limpieza aplicada.

---

## 👥 Segmentación por Edad

| Segmento | Rango | Comportamiento | Oportunidad |
|---|---|---|---|
| **Joven** | < 30 años | Uso moderado, menor presencia | Captación con planes digitales |
| **Adulto** | 30 – 59 años | Segmento dominante y más activo | Retención y upselling |
| **Adulto Mayor** | 60+ años | Uso conservador y estable | Fidelización y soporte |

El segmento **Adulto** concentra la mayor parte del consumo de llamadas y mensajes,
siendo el núcleo del negocio actual de ConnectaTel.

---

## 📊 Segmentación por Nivel de Uso

| Segmento | Criterio | Perfil predominante | Riesgo |
|---|---|---|---|
| **Alto uso** | ≥ 10 llamadas y ≥ 10 mensajes | Usuario Premium activo | Bajo |
| **Uso medio** | 5–9 llamadas y 5–9 mensajes | Mixto (Básico y Premium) | Medio |
| **Bajo uso** | < 5 llamadas y < 5 mensajes | Usuario Básico inactivo | Alto (churn) |

> El segmento de **Alto uso** es el más numeroso, lo que indica que la base de clientes
> tiene una demanda real que puede estar superando los límites del plan Básico.

---

## 📈 Patrones de Uso Extremo (Outliers)

| Variable | Límite IQR | Valor máximo real | Decisión |
|---|---|---|---|
| `cant_mensajes` | 28.5 | 60 | **Conservar** — uso intensivo real |
| `cant_llamadas` | 22.5 | 45 | **Conservar** — uso intensivo real |
| `cant_minutos_llamada` | 135.9 min | 120 min | **Sin outliers** |

Los usuarios con consumo extremo en llamadas y mensajes podrían representar
**clientes corporativos o power users** que actualmente no tienen un plan adecuado
a su nivel de consumo.

---

## 💡 Recomendaciones Comerciales

### 1. Crear un Plan Intermedio
Existe un segmento significativo de **Uso medio** que supera el plan Básico pero
no justifica el costo del Premium. Un plan con ~250 minutos, ~300 mensajes y
15 GB a ~$18 USD/mes captaría este segmento y reduciría el churn.

### 2. Campaña de Upselling para Usuarios Básico de Alto Uso
Los usuarios en plan Básico con comportamiento de Alto uso están pagando excesos
continuamente. Una campaña de migración al plan Premium o Intermedio
representaría mayor ingreso recurrente y mayor satisfacción del cliente.

### 3. Programa de Retención para Adultos Mayores
El segmento de 60+ años con Bajo uso tiene el mayor riesgo de churn silencioso.
Se recomienda un programa de fidelización con beneficios simples:
descuentos por permanencia, atención prioritaria o minutos extra.

### 4. Plan Corporativo para Power Users
Los outliers en llamadas (+22 llamadas) y mensajes (+28 mensajes) sugieren
uso empresarial. Crear un plan corporativo con tarifas por volumen captaría
este segmento de alto valor.

### 5. Estrategia de Captación para Jóvenes
El segmento menor de 30 años es el más pequeño pero el de mayor potencial
de crecimiento. Planes digitales con datos prioritarios y mensajería ilimitada
serían más atractivos para este perfil.

---

## 🔑 Conclusión

ConnectaTel cuenta con una base de clientes sólida y activa, pero su oferta
actual de dos planes (Básico y Premium) no cubre adecuadamente la diversidad
de perfiles de consumo identificados. La creación de un **plan intermedio**,
combinada con estrategias diferenciadas por segmento, tiene el potencial de
aumentar el ingreso promedio por usuario (ARPU) y reducir el churn de manera
significativa.
