# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Visión general

**listmart** es una app iOS en SwiftUI (`listmart.xcodeproj`) para hacer la lista de la compra. Actualmente es la plantilla inicial de Xcode: `listmartApp` es el punto de entrada `@main` (`WindowGroup { ContentView() }`) y `ContentView` sigue siendo el "Hello, world!".

## Alcance del MVP

- **Pantallas**: Login y Dashboard.
- El usuario puede agregar productos con **nombre**, **descripción** (opcional) y **valor**.
- Cada producto tiene un **checkbox** que indica si ya se compró. Al marcarlo, su valor se suma a un **total acumulado**, que muestra cuánto lleva gastado la lista de la compra.

## Arquitectura: MVVM

- **Model**: structs puros (p. ej. `Product` con nombre, descripción opcional, valor e `isPurchased`).
- **ViewModel**: clases `ObservableObject` (o `@Observable`) con la lógica: autenticación del Login y, en el Dashboard, añadir productos, marcar comprados y calcular el total de los comprados.
- **View**: vistas SwiftUI (`LoginView`, `DashboardView`) que solo muestran estado y delegan las acciones al ViewModel, sin lógica de negocio.
- Carpetas dentro de `listmart/`: `Models/`, `ViewModels/`, `Views/`.

## Comandos

No hay paquetes Swift ni tests todavía. Se compila y ejecuta desde Xcode (SDK iOS), o por CLI:

```bash
xcodebuild -project listmart.xcodeproj -scheme listmart -sdk iphonesimulator build
```

## Spec Kit

Skills `speckit-*` en `.claude/skills/`, plantillas y scripts en `.specify/`. Flujo: specify → clarify → plan → tasks → implement. La constitución (`.specify/memory/constitution.md`) todavía es la plantilla sin rellenar; usa `speckit-constitution` antes de empezar features.
