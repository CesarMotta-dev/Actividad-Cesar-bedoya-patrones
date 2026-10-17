# Proposal

## Why

La API LibraryLab contiene cinco ejercicios de patrones de diseño pendientes que actualmente lanzan `NotImplementedException`. Se requiere completarlos para que la gestión de préstamos, catálogo, notificaciones y consultas de miembros funcione respetando Clean Architecture.

## What Changes

Se implementarán los patrones Factory Method, Builder, Adapter, Decorator y Facade en la capa de aplicación. Las implementaciones conservarán los contratos existentes, serán compatibles con .NET 8 y no modificarán las pruebas automatizadas.

## Capabilities

### New Capabilities

- `library-design-patterns`: Implementación de los cinco patrones de diseño requeridos para las operaciones de biblioteca.

### Modified Capabilities

## Impact

Se verá afectado el proyecto `LibraryLab.Application` y las pruebas del proyecto `LibraryLab.Patterns.Tests`. No se modificarán las entidades de dominio, los contratos de persistencia, la configuración de MySQL ni las pruebas existentes.
