# GraphQL Schema Specification - Analytics & Reports

## 1. Descripción
Este esquema define las consultas necesarias para generar reportes dinámicos de actividad de usuarios y rendimiento del sistema.

## 2. Definición del Esquema (SDL)

```graphql
"""
Representa un reporte generado por el sistema.
"""
type Report {
  id: ID!
  title: String!
  category: ReportCategory!
  dataPoints: [DataPoint!]!
  generatedAt: String!
}

enum ReportCategory {
  USER_ACTIVITY
  SYSTEM_PERFORMANCE
  REVENUE
}

type DataPoint {
  label: String!
  value: Float!
}

type Query {
  # Obtener un reporte por su ID
  getReport(id: ID!): Report
  
  # Listar todos los reportes de una categoría específica
  listReports(category: ReportCategory): [Report!]!
}

type Mutation {
  # Generar un nuevo reporte bajo demanda
  generateReport(title: String!, category: ReportCategory!): Report
}
```

## Ejemplo de Query

```graphql
query {
  getReport(id: "rep-99") {
    title
    dataPoints {
      label
      value
    }
  }
}
```