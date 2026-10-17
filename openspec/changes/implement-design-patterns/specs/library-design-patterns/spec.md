# Spec Delta

## Purpose

Define el comportamiento verificable de los cinco patrones de diseño requeridos por LibraryLab para crear préstamos, transformar datos, enviar notificaciones y consultar información consolidada de miembros.

## ADDED Requirements

### Requirement: Factory Method creates typed loans
El sistema SHALL crear un préstamo con los datos del comando recibido y con el tipo de recurso solicitado.

#### Scenario: Create a book loan
- **WHEN** se solicita crear un préstamo con `ResourceKind.Book`
- **THEN** el préstamo conserva el usuario, el recurso y el tipo `Book`

### Requirement: Builder creates loan receipts
El sistema SHALL construir un comprobante que conserve el identificador del préstamo, el recurso y la fecha de vencimiento recibidos.

#### Scenario: Build a receipt
- **WHEN** se construye un comprobante con datos válidos
- **THEN** el comprobante contiene exactamente esos datos

### Requirement: Adapter converts legacy catalog records
El sistema SHALL adaptar un registro legado del catálogo al contrato de importación actual y SHALL generar un identificador no vacío.

#### Scenario: Adapt a legacy record
- **WHEN** se adapta un registro con código, nombre y categoría
- **THEN** el resultado conserva esos valores y contiene un identificador válido

### Requirement: Decorator sends and audits loan notices
El sistema SHALL enviar cada aviso de préstamo mediante el remitente configurado y SHALL registrar el mismo aviso mediante el auditor configurado.

#### Scenario: Send and audit a notice
- **WHEN** se envía un aviso mediante el decorador
- **THEN** el remitente recibe el aviso y el auditor registra el aviso

### Requirement: Facade returns active member loan information
El sistema SHALL obtener el usuario solicitado, sus préstamos y los recursos asociados, y SHALL devolver un resumen con los comprobantes de sus préstamos activos.

#### Scenario: Build a member overview
- **WHEN** existe un usuario con un préstamo asociado a un recurso
- **THEN** el resumen contiene el identificador y nombre del usuario y el comprobante del préstamo con su recurso
