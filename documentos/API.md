# 🔌 Matriz de Interoperabilidad y Sovereign APIs
> **VTS GovProc AI 3.0 — Conectores Integrados del Estado**

---

## 1. Módulos de Integración Externos (Sovereign API Engine)

La plataforma está diseñada para comunicarse de forma bidireccional y segura con los sistemas clave del Gobierno Digital:

| Organismo / Sistema | Servicio API | Propósito de la Integración | Estado |
| :--- | :--- | :--- | :--- |
| **ONAT** | `/api/v1/onat/certificacion` | Verificación de solvencia tributaria en tiempo real | Preparado |
| **Bancos Nacionales** | `/api/v1/banca/conciliacion` | Conciliación de pagos en CUP y retención de garantías | Preparado |
| **MINCIN** | `/api/v1/mincin/mayoristas` | Validación de licencias del Mercado de Abasto (Res. 13/2026) | Conectado |
| **Aduana General** | `/api/v1/aduana/despacho` | Trazabilidad de importaciones vinculadas a contratos | Preparado |
| **Registro Mercantil** | `/api/v1/registro/entidad` | Validación de representación legal de actores económicos | Preparado |
| **Firma Digital PKI** | `/api/v1/pki/verificar` | Autenticación y firma criptográfica de decisiones | Conectado |

---

## 2. Endpoint de Ejemplo: Validación de Expediente en LexCore

```http
POST /api/v1/lexcore/validar-expediente
Content-Type: application/json

{
  "expediente_id": "EXP-2026-MINCOM-0012",
  "normativas": ["RES_13_2026", "RES_160", "TRANSF_170"]
}

