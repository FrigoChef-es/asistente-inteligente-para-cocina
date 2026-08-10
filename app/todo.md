# FrigoChef - TODO

## Arquitectura & Base de Datos
- [x] Definir esquema de base de datos (usuarios, ingredientes, recetas, favoritas, caducidad, etc.)
- [x] Crear migraciones SQL con Drizzle
- [ ] Implementar helpers de base de datos en server/db.ts

## Landing Page Pública
- [x] Crear página de bienvenida con propuesta de valor: "La IA que decide qué cocinar por ti y evita que tires comida"
- [x] Diseñar hero section con CTA de registro
- [x] Mostrar beneficios clave (ahorro tiempo, ahorro dinero, comer mejor)
- [x] Incluir comparación plan gratuito vs Premium
- [x] Implementar navegación pública (sin requerir login)

## Pantalla Principal - Gestión de Ingredientes
- [x] Crear componente de lista de ingredientes con emojis
- [x] Implementar autocompletado de ingredientes (base de datos de ingredientes comunes)
- [x] Botón "Añadir ingrediente" con modal/drawer
- [x] Botón para eliminar ingredientes de la lista
- [x] Botón "Generar recetas" que llama a IA
- [x] Botón "Sorpréndeme" que elige automáticamente la mejor receta
- [ ] Persistencia de ingredientes en sesión/localStorage

## Generación de Recetas con IA
- [x] Integrar LLM para generar recetas basadas en ingredientes
- [x] Estructura de respuesta: título, tiempo, dificultad, calorías, ingredientes (tiene/falta)
- [x] Mostrar receta con opción "Ver receta completa"
- [x] Botón "Guardar" (requiere autenticación)
- [x] Botón "Otra receta" para generar nueva
- [x] Implementar función "Sorpréndeme" que elige mejor receta según criterios IA

## Escaneo de Nevera por Foto
- [x] Crear componente de carga de imagen
- [x] Integrar visión por IA para detectar ingredientes en foto
- [x] Mostrar ingredientes detectados con opción de editar
- [x] Generar recetas automáticamente basadas en foto
- [x] Feature exclusiva de plan Premium

## Sistema de Recetas Favoritas
- [x] Crear tabla de recetas favoritas en BD
- [x] Implementar guardar receta favorita (requiere login)
- [x] Crear página de recetas guardadas
- [x] Mostrar contador de favoritas guardadas
- [x] Límite de 10 favoritas en plan gratuito
- [x] Recetas ilimitadas en plan Premium
- [x] Opción de eliminar de favoritas
- [x] Crear habilidad reutilizable webdev-favorites-system

## Menú Semanal Automático
- [x] Crear formulario para: personas, presupuesto, preferencias dietéticas, restricciones
- [x] Integrar IA para generar menú semanal (desayuno, comida, cena)
- [x] Generar lista de compra optimizada
- [x] Mostrar presupuesto total vs presupuesto indicado
- [x] Feature exclusiva de plan Premium

## Control de Caducidad
- [x] Crear tabla de productos con fecha de caducidad
- [x] Implementar agregar producto con fecha de vencimiento
- [x] Sistema de alertas para productos próximos a caducar
- [ ] Generar recetas automáticas para ingredientes por caducar
- [x] Feature exclusiva de plan Premium

## Sistema Freemium
- [ ] Crear tabla de suscripciones en BD
- [ ] Implementar contador de recetas generadas por día (límite 5 gratuitas)
- [ ] Implementar límite de 10 recetas favoritas en plan gratuito
- [ ] Crear página de planes/pricing
- [ ] Integrar Stripe para pagos (Premium 4,99 €/mes)
- [ ] Mostrar estado de suscripción en UI
- [ ] Bloquear features Premium para usuarios gratuitos
- [ ] Implementar lógica de reset diario de contador de recetas

## Autenticación & Perfil de Usuario
- [ ] Verificar que OAuth Manus está configurado
- [ ] Crear página de perfil de usuario
- [ ] Mostrar plan actual (Gratuito/Premium)
- [ ] Mostrar recetas generadas hoy vs límite
- [ ] Mostrar recetas favoritas guardadas vs límite
- [ ] Opción de cambiar plan/cancelar suscripción

## UI/UX & Diseño
- [ ] Definir paleta de colores (tema claro/oscuro)
- [ ] Crear componentes reutilizables
- [ ] Implementar navegación consistente
- [ ] Responsive design (mobile-first)
- [ ] Animaciones suaves y feedback visual
- [ ] Estados de carga y error
- [ ] Empty states informativos

## Testing & QA
- [ ] Tests unitarios para procedimientos tRPC
- [ ] Tests de integración para flujos principales
- [ ] Verificar límites del plan gratuito
- [ ] Verificar features Premium bloqueadas
- [ ] Testing en mobile
- [ ] Testing de generación de recetas con IA

## Optimizaciones Finales
- [ ] Optimizar llamadas a IA (caché, batching)
- [ ] Mejorar performance de carga
- [ ] Validación de datos en cliente y servidor
- [ ] Manejo de errores robusto
- [ ] Logging y monitoreo
- [ ] Documentación de API

## Deployment
- [ ] Crear checkpoint final
- [ ] Verificar todas las variables de entorno
- [ ] Testing en producción
- [ ] Publicar aplicación

## Tareas Pendientes - Integración de Base de Datos
- [ ] Conectar autocompletado de ingredientes a tabla `commonIngredients` vía tRPC
- [ ] Crear helper `getCommonIngredients()` en server/db.ts
- [ ] Crear procedimiento tRPC `ingredients.getCommon` para obtener ingredientes
- [ ] Poblar tabla `commonIngredients` con lista inicial de ingredientes comunes


## FASE 1: Optimización de Sorpréndeme ✅ COMPLETADA
- [x] Crear tabla `cachedSurprises` en BD
- [x] Implementar helpers de caché (getCachedSurprise, saveCachedSurprise)
- [x] Optimizar prompts (reducir tokens: 127→45 y 98→35)
- [x] Agregar timeout (3 segundos) a generación de recetas
- [x] Implementar fallback recipes para cuando IA falla
- [x] Crear tests para validar caché y fallback
- [x] Agregar procedimiento tRPC para estadísticas de caché

## FASE 2: Personalización ✅ COMPLETADA
- [x] Crear tabla `userPreferences` en BD
- [x] Crear procedimientos tRPC para get/update preferencias
- [x] Implementar `getUserTasteProfile()` basado en historial
- [x] Crear `generatePersonalizedPrompt()` con contexto del usuario
- [x] Implementar `scoreRecipeForUser()` para ranking personalizado
- [x] Crear `generatePersonalizedSurpriseRecipe()` con preferencias
- [x] Tests completos para scoring y ranking (9 tests)
