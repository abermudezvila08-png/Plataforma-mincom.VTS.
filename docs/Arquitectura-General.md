# 🏛️ Arquitectura General del Sistema
> **VTS GovProc AI 3.0 — Plataforma Nacional de Compras Públicas**

---

## 1. Modelo de Capas Funcionales

El sistema está diseñado bajo una arquitectura limpia y modular de 6 capas independientes pero interconectadas:

1. **Capa 1: Experiencia Digital (UI/UX)**
   - Interfaz responsive desarrollada en Flutter (Web, Android, iOS, Desktop).
   - Motor Offline-First con IndexedDB / SQLite para continuidad operativa en zonas de baja conectividad.
   - Panel Ejecutivo Nacional con visualización de KPIs y mapa interactivo provincial.

2. **Capa 2: Gestión del Negocio (Core)**
   - Motor de Expediente Único Digital (EUD).
   - Módulo Presupuestario (Fondo, Programa, Organismo, CUP comprometido vs. ejecutado).
   - Gestión de Licitaciones, Comité Evaluador y Ejecución Contractual.

3. **Capa 3: Inteligencia y Cumplimiento Legal**
   - **LexCore Compliance Engine:** Evaluación continua de la Resolución 13/2026, Resolución 160 y Transformación 170.
   - **IA Operacional:** Algoritmos de scoring de riesgo para proveedores (0-100) y recomendaciones no vinculantes.

4. **Capa 4: Gestión Económica y Abasto**
   - Módulo de Mercado de Abasto Mayorista (Lotes, Membresías, Pedidos).
   - Facturación electrónica y conciliación de pagos con el sistema bancario nacional.

5. **Capa 5: Confianza y Criptografía**
   - Infraestructura de Firma Digital (PKI) para actas y decisiones de comité.
   - Cadena de Auditoría Hash ("Blockchain" interna) con verificación de integridad al 100%.

6. **Capa 6: Interoperabilidad Soberana (APIs)**
   - Conectores directos e interconectables con ONAT, MINCIN, Bancos (BPA/BANDEC/BM), Aduana y Registro Mercantil.

---

## 2. Diagrama de Flujo del Expediente Único

```text
[01. Solicitud de Compra]
         │
         ▼
[02. Certificación Presupuestaria]
         │
         ▼
[03. Apertura de Expediente Único]
         │
         ▼
[04. Convocatoria & Licitación]
         │
         ▼
[05. Recepción de Ofertas Anonimizadas]
         │
         ▼
[06. Análisis de Riesgo por IA]
         │
         ▼
[07. Evaluación y Votación del Comité]
         │
         ▼
[08. Adjudicación & Firma Digital PKI]
         │
         ▼
[09. Emisión de Contrato & Orden de Abasto]
         │
         ▼
[10. Facturación, Entrega & Pago Bancario]
         │
         ▼
[11. Verificación Hash & Cierre Auditoría]

