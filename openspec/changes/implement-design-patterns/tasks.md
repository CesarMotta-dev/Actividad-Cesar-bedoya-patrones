# Tasks

## 1. Patrones creacionales

- [x] 1.1 Implementar `LoanFactoryExercise` con Factory Method para crear préstamos conservando usuario, recurso, fecha y `ResourceKind`; verificar con `dotnet test tests/LibraryLab.Patterns.Tests/LibraryLab.Patterns.Tests.csproj --filter FullyQualifiedName~FactoryMethodExerciseTests`.
- [x] 1.2 Implementar `LoanReceiptBuilderExercise` para construir comprobantes inmutables con los datos recibidos; verificar con `dotnet test tests/LibraryLab.Patterns.Tests/LibraryLab.Patterns.Tests.csproj --filter FullyQualifiedName~BuilderExerciseTests`.

## 2. Patrones estructurales

- [x] 2.1 Implementar `LegacyCatalogAdapterExercise` para convertir registros legados y generar un identificador no vacío; verificar con `dotnet test tests/LibraryLab.Patterns.Tests/LibraryLab.Patterns.Tests.csproj --filter FullyQualifiedName~AdapterExerciseTests`.
- [x] 2.2 Implementar `LoanNoticeDecoratorExercise` para enviar y auditar el mismo aviso usando las dependencias configuradas; verificar con `dotnet test tests/LibraryLab.Patterns.Tests/LibraryLab.Patterns.Tests.csproj --filter FullyQualifiedName~DecoratorExerciseTests`.
- [x] 2.3 Implementar `MemberOverviewFacadeExercise` usando los repositorios existentes para construir el resumen del miembro y sus préstamos activos; verificar con `dotnet test tests/LibraryLab.Patterns.Tests/LibraryLab.Patterns.Tests.csproj --filter FullyQualifiedName~FacadeExerciseTests`.

## 3. Validación de integración

- [x] 3.1 Compilar la solución completa sin errores mediante `dotnet build LibraryLab.sln`.
- [x] 3.2 Ejecutar todas las pruebas automatizadas mediante `dotnet test LibraryLab.sln` y confirmar que no se modificaron las pruebas existentes.
- [x] 3.3 Validar la configuración de la API y la conexión MySQL mediante las pruebas de infraestructura y la configuración existente, sin añadir Docker ni cambiar la arquitectura.
