# Library App

## Descripción

Library App es una aplicación de consola para la gestión de una biblioteca, desarrollada en .NET 8.0. Permite buscar usuarios (patrons), gestionar préstamos de libros y renovar membresías. Utiliza una arquitectura en capas con inyección de dependencias, almacenamiento de datos en archivos JSON y pruebas unitarias con xUnit y NSubstitute.

## Estructura del Proyecto

- `AccelerateDevGitHubCopilot.sln`: Archivo de solución de Visual Studio.
- `README.md`: Este archivo de documentación.
- `src/`
  - `Library.ApplicationCore/`
    - `Library.ApplicationCore.csproj`: Proyecto de núcleo de aplicación.
    - `Entities/`: Entidades del dominio (e.g., Patron, Loan).
    - `Enums/`: Enumeraciones (e.g., CommonActions).
    - `Interfaces/`: Interfaces de servicios y repositorios.
    - `Services/`: Servicios de negocio (e.g., PatronService, LoanService).
  - `Library.Console/`
    - `appSettings.json`: Configuración de rutas JSON.
    - `CommonActions.cs`: Enumeración de acciones comunes.
    - `ConsoleApp.cs`: Clase principal de la aplicación de consola.
    - `ConsoleState.cs`: Estados de la consola.
    - `Library.Console.csproj`: Proyecto de consola.
    - `Program.cs`: Punto de entrada con configuración de DI.
    - `Json/`: Archivos JSON de datos (e.g., Authors.json, Books.json).
  - `Library.Infrastructure/`
    - `Library.Infrastructure.csproj`: Proyecto de infraestructura.
    - `Data/`: Clases de acceso a datos (e.g., JsonData, JsonPatronRepository).
- `tests/`
  - `UnitTests/`
    - `LoanFactory.cs`: Fábrica para pruebas.
    - ... (otros archivos de pruebas).

## Clases e Interfaces Clave

- [`ConsoleApp`](src/Library.Console/ConsoleApp.cs): Gestiona el flujo de la interfaz de consola, manejando estados como búsqueda de usuarios y detalles de préstamos.
- [`JsonPatronRepository`](src/Library.Infrastructure/Data/JsonPatronRepository.cs): Implementa [`IPatronRepository`](src/Library.ApplicationCore/Interfaces/IPatronRepository.cs) para operaciones CRUD en usuarios usando JSON.
- [`JsonLoanRepository`](src/Library.Infrastructure/Data/JsonLoanRepository.cs): Implementa [`ILoanRepository`](src/Library.ApplicationCore/Interfaces/ILoanRepository.cs) para operaciones en préstamos.
- [`JsonData`](src/Library.Infrastructure/Data/JsonData.cs): Centraliza la carga y guardado de datos JSON, incluyendo métodos para poblar entidades relacionadas.
- [`PatronService`](src/Library.ApplicationCore/Services/PatronService.cs): Servicio de negocio para lógica de usuarios.
- [`LoanService`](src/Library.ApplicationCore/Services/LoanService.cs): Servicio de negocio para lógica de préstamos.

## Uso

1. Clona el repositorio y abre `AccelerateDevGitHubCopilot.sln` en Visual Studio.
2. Restaura paquetes NuGet: `dotnet restore`.
3. Construye la solución: `dotnet build`.
4. Ejecuta la aplicación de consola: `dotnet run --project src/Library.Console/Library.Console.csproj`.
5. Sigue las instrucciones en la consola para buscar usuarios, ver detalles y gestionar préstamos.

Los datos se almacenan en archivos JSON en `src/Library.Console/Json/`. Configura rutas en `appSettings.json`.

## Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo LICENSE para más detalles.