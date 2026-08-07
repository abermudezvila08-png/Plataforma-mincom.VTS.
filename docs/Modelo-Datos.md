# 🗄️ Esquema del Modelo de Datos Conceptual
> **VTS GovProc AI 3.0 — Arquitectura centrada en el Expediente Único**

---

## 1. Entidad Principal: `expediente`

El núcleo de la base de datos es la tabla `expediente`. Toda acción (licitación, contrato, factura, hash) se vincula a esta entidad.

```sql
CREATE TABLE expediente (
    id VARCHAR(50) PRIMARY KEY, -- Ej: EXP-2026-MINCOM-0012
    unidad_organizativa VARCHAR(100) NOT NULL,
    provincia_code VARCHAR(3) NOT NULL, -- Ej: LHA, VCL, PRI
    monto_presupuestado_cup DECIMAL(15,2) NOT NULL,
    estado VARCHAR(30) NOT NULL, -- SOLICITUD, LICITACION, EVALUACION, CONTRATADO, CERRADO
    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    hash_expediente VARCHAR(64) NOT NULL -- Sha-256 del estado inicial
);
  [presupuesto] ────1:N────> [expediente] ────1:N────> [licitacion]
                                  │                         │
                                  │                         ├──1:N──> [oferta]
                                  │                         └──1:1──> [evaluacion_ia]
                                  │
                                  ├──1:1──> [acta_comite]
                                  ├──1:N──> [contrato] ───1:N──> [factura] ───1:N──> [pago]
                                  └──1:N──> [bloque_auditoria_hash]
CREATE TABLE bloque_auditoria_hash (
    id_bloque SERIAL PRIMARY KEY,
    expediente_id VARCHAR(50) REFERENCES expediente(id),
    evento VARCHAR(100) NOT NULL, -- Ej: ADJUDICACION_FIRMADAS
    hash_anterior VARCHAR(64) NOT NULL,
    hash_bloque VARCHAR(64) NOT NULL,
    firma_digital_pk VARCHAR(255),
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
