# Design

## Context

La capa `LibraryLab.Application` contiene contratos de ejercicios para cinco patrones y clases que todavía lanzan `NotImplementedException`. Las entidades de dominio, los comandos de aplicación y los repositorios existentes ya definen los datos necesarios. La solución utiliza .NET 8, C# 12 y Clean Architecture.

## Goals / Non-Goals

**Goals:**

- Implementar los cinco patrones en las clases existentes de `PatternExerciseContracts.cs`.
- Mantener los contratos públicos y las dependencias actuales.
- Usar los repositorios mediante sus abstracciones para que Facade sea independiente de infraestructura.
- Mantener compatibilidad con las pruebas existentes y permitir pruebas unitarias deterministas.

**Non-Goals:**

- Modificar pruebas, entidades de dominio, esquemas de base de datos o configuración de MySQL.
- Añadir dependencias externas, Docker o nuevos endpoints.
- Cambiar la estructura de Clean Architecture.

## Decisions

- **Factory Method:** `LoanFactoryExercise` creará la entidad `Loan` a partir de `CreateLoanCommand` y `ResourceKind`, centralizando la selección del tipo de recurso en el método de fábrica.
- **Builder:** `LoanReceiptBuilderExercise` construirá `LoanReceipt` a partir de sus tres valores requeridos, manteniendo una salida inmutable.
- **Adapter:** `LegacyCatalogAdapterExercise` traducirá explícitamente cada campo de `LegacyCatalogRecord` a `CatalogImport` y generará un `Guid` nuevo para el identificador.
- **Decorator:** `LoanNoticeDecoratorExercise` conservará las dependencias recibidas y ejecutará el envío y el registro del aviso con la misma cancelación. El decorador coordinará ambas responsabilidades sin cambiar los contratos.
- **Facade:** `MemberOverviewFacadeExercise` consultará el usuario y las listas de préstamos y recursos mediante repositorios. Filtrará los préstamos del usuario, asociará sus recursos y construirá comprobantes con las fechas de vencimiento.
- **Errores y datos ausentes:** se usarán las abstracciones y comportamientos existentes del dominio; no se añadirán consultas directas a MySQL ni referencias desde Application hacia Infrastructure.

## Risks / Trade-offs

- [Riesgo] Un préstamo puede referenciar un recurso inexistente → el Facade omitirá comprobantes sin recurso asociado en lugar de acceder directamente a infraestructura.
- [Riesgo] Cambiar el orden de las operaciones del Decorator puede afectar auditoría y envío → se mantendrá una secuencia determinista y se propagará la cancelación recibida.
- [Riesgo] La implementación podría introducir referencias fuera de Clean Architecture → solo se utilizarán contratos y entidades ya disponibles en Application y Domain.

## Migration Plan

No se requiere migración de datos ni cambios de infraestructura. Después de aplicar las implementaciones se compilará la solución y se ejecutarán las pruebas de patrones y la suite completa.
