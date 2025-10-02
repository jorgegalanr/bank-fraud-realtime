# 💳 Detección de Fraude en Tiempo (casi) Real

**Objetivo negocio:** reducir **falsos negativos** dado un **coste de fraude** > coste de revisión.  
**Idea:** entrenar *offline*, simular **streaming** y medir latencia + *throughput*.

---

## 🔧 Metodología
- **Imbalance learning** (class weights / focal loss) + *time-based split*.
- **Features secuenciales** por tarjeta, comercio y dispositivo (ventanas móviles).
- **Umbral por coste** y **curva de beneficio**.
- **Online**: *mock* de streaming (productor/consumidor) y **scoring** con caché de *features*.

---

## 🧪 Métricas
AUC/PR-AUC, **Recall@cost**, latencia P95, *throughput* (tx/s).

---

## ▶️ Cómo ejecutar
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

make train     # entrenamiento offline
make stream    # lanza productor y consumidor (simulación)
make serve     # API para reglas + ML
make eval      # eval coste/beneficio y curva de umbral
