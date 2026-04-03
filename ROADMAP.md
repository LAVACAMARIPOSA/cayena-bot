# 🏗️ CayenaBot — AI PropTech Builder
## Roadmap & Estado del Proyecto

> **85 commits** | Single-file HTML app | Deployed on Render.com
> **Repositorio:** github.com/lavacamariposa/cayena-bot

---

## 🎯 Qué es CayenaBot

CayenaBot es una herramienta AI para empresas de real estate que genera automáticamente:
- Renders fotorrealistas de proyectos inmobiliarios
- Tours virtuales 360° interactivos
- Análisis de planos arquitectónicos con AI
- Brochures PDF profesionales
- Contenido de marketing inmobiliario

**Modelo de negocio:** Uso interno para generar contenido de lujo para clientes ($800-$2,500 por proyecto).

---

## ✅ Estado Actual (Abril 2026) — Lo que YA funciona

### 🔐 Sistema Multi-Usuario
- [x] Login con 4 usuarios (ISA, JAG, PAM, ALV) con avatares y colores
- [x] Solo seleccionar avatar + escribir clave (no username)
- [x] Tracking de actividad por usuario (quién editó qué)
- [x] Badges de color en mensajes de chat y proyectos
- [x] Cerrar sesión / cambiar usuario

### 📂 Gestión de Proyectos (estilo ChatGPT)
- [x] Pantalla de proyectos guardados después del login
- [x] Crear nuevo proyecto / cargar existente / eliminar
- [x] Auto-guardado cada 30 segundos con checkpoints
- [x] Exportar proyecto como JSON
- [x] Importar proyecto JSON (llena builder automáticamente)
- [x] Cada proyecto independiente en localStorage

### 💬 Chat AI — Centro de Control
- [x] Chat nunca se bloquea (message queue + processing)
- [x] Botón "⏹ Detener" para cancelar respuesta
- [x] Cola de mensajes (escribe mientras AI piensa)
- [x] Multi-proveedor: OpenRouter (gratis), Groq, OpenAI, Claude
- [x] 6+ modelos gratuitos con fallback automático
- [x] Triple seguridad: NUNCA gasta créditos de OpenRouter
- [x] Blacklist de modelos muertos (Kimi, etc)
- [x] System prompt que le dice al bot todas sus capacidades
- [x] Comandos de chat: "reintentar renders", "abre tour", "detén swarm"

### 🌐 Búsqueda Web en Tiempo Real
- [x] DuckDuckGo como proveedor principal (gratis, ilimitado)
- [x] SerpAPI Google como fallback
- [x] Auto-detección de cuándo buscar (precios, ubicaciones, normativas)
- [x] Resultados inyectados en contexto del AI
- [x] Indicador "🔍 Buscando en internet..."

### 🇩🇴 Datos Inmobiliarios de República Dominicana
- [x] Precios de construcción por zona (Santo Domingo, Punta Cana, Cabarete, Cap Cana, Santiago, Las Terrenas)
- [x] Precios de venta por m² por zona
- [x] Materiales con precios en RD$ (cemento, varilla, blocks)
- [x] ROI Airbnb por zona (6-15%)
- [x] Normativa: R-001, Ley 675, DGII 3%, retiros, sísmica
- [x] Marcas locales (León Jimenes, Windoor, Corona, etc)

### 🎨 Generación de Imágenes (Race Mode)
- [x] RACE mode: todos los proveedores al mismo tiempo, primero gana
- [x] Proveedores: OpenRouter Gemini, AI Horde, Pollinations, Together.ai, Local SD
- [x] 5 renders paralelos en el swarm
- [x] Retry automático (3 intentos por render)
- [x] Agentes idle rescatan renders fallidos (Fase 3)
- [x] Botón "🔄 Reintentar" en cada render fallido
- [x] Conversión automática de R2 URLs a base64 (para Pannellum)
- [x] Resolución 1024×512 (ratio 2:1 para panoramas)

### ⚡ Ruflo Swarm Engine — 100 Agentes AI
- [x] Wizard de Estilo con 6 pasos antes de generar:
  1. 📍 Ubicación (auto-detección con AI)
  2. 🏗️ Estilo arquitectónico (6 opciones con fotos Unsplash)
  3. 🛋️ Estilo de interiores (6 opciones con fotos)
  4. 🎨 Paleta de colores (6 opciones con strips)
  5. 📸 Cantidad de renders (4 opciones: clave, mínimo, completo, custom)
  6. 🔊 Sonido ambiente (olas, brisa, jazz, piano, pájaros)
- [x] "Style DNA" inyectado en TODOS los prompts = coherencia visual
- [x] Cálculo inteligente de renders basado en cantidad de unidades
- [x] 3 fases: agentes rápidos → renders paralelos → idle agents rescatan fallidos
- [x] Dashboard en tiempo real con progreso por agente
- [x] Click en agentes para ver su render
- [x] Botón flotante "Swarm" para reabrir dashboard
- [x] Auto-sugerencia de swarm cuando la tarea lo necesita

### 🧭 Tour Virtual
- [x] Pannellum.js para modo 360° (panoramas equirectangulares)
- [x] Vista plana con Ken Burns cinematográfico (zoom+pan automático)
- [x] Transiciones "walking" con dolly zoom + blur + fade
- [x] Hotspots animados estilo Matterport (🚶 con pulso dorado)
- [x] Pan/zoom con drag + scroll (clamped, sin bordes negros)
- [x] Thumbnails en barra inferior con auto-scroll
- [x] Autoplay (avance automático cada 8s)
- [x] Botón 🚶 "Walk Forward" centrado
- [x] Indicador "Siguiente → [nombre]" 
- [x] Teclado: ← → para navegar
- [x] Sonido ambiente durante el tour

### 📷 Captura Guiada de Fotos
- [x] 10 pasos guiados con instrucciones profesionales
- [x] Tips de fotografía para cada espacio
- [x] Cámara del dispositivo (capture="environment")
- [x] Preview de cada foto antes de aceptar
- [x] Grid de fotos capturadas con progreso
- [x] Crear tour automáticamente al terminar
- [x] Visible en tour empty state como botón principal

### 📐 Planos AI — Análisis Arquitectónico
- [x] Wizard técnico: tipo de proyecto, etapa, niveles, estructura, zona sísmica
- [x] 10 prioridades de análisis seleccionables
- [x] Auto-detección de datos del plano con AI visión
- [x] Análisis profesional: unidades, medidas, estructura, normativa
- [x] Chat de modificaciones con contexto técnico
- [x] Modificación visual del plano con Gemini (imagen → imagen editada)
- [x] Render 3D basado en el plano real (no genérico)
- [x] Botones rápidos: analizar medidas, sugerir mejoras, calcular m²

### 📍 Detección de Ubicación
- [x] SerpAPI Google Maps (vía CORS proxy)
- [x] AI fallback para describir ubicación
- [x] Campo de contexto de ubicación en builder y wizard
- [x] Geo-context engine: materiales, vegetación, iluminación por región
- [x] 4 regiones: Caribe, Mediterráneo, Tropical Asia, Urbano Moderno

### 🖼️ Galería + Descargas
- [x] Grid de renders con lightbox
- [x] 👍/👎 feedback en cada render
- [x] Botón ⬇ en cada imagen + lightbox
- [x] "Descargar todas" como HTML gallery
- [x] Renders se agregan automáticamente al tour

### 📄 Exportaciones
- [x] JSON (proyecto completo con imágenes)
- [x] PDF Brochure profesional (A4 landscape, estilo Sotheby's)
- [x] HTML Gallery (todas las imágenes con download)
- [x] Builder genera plataforma web standalone

### 🔧 Configuración
- [x] API Keys: OpenRouter, OpenAI, Claude, Groq, SD Local
- [x] Test completo del sistema (40+ tests automáticos)
- [x] Diagnóstico de renders
- [x] Tutorial de bienvenida (6 pasos)
- [x] Cerrar sesión

---

## 🚧 Problemas Conocidos

### Críticos
- **Seguridad:** API keys en client-side (visible en DevTools). Necesita backend.
- **Monolito:** Todo en un solo archivo HTML (~8000+ líneas). Difícil de mantener.
- **Persistencia:** localStorage puede borrarse. No hay backup en la nube.
- **Calidad de renders:** AI Horde (gratis) genera calidad SD/SDXL. No es Midjourney.

### Tour Virtual
- **No es Matterport real:** Las imágenes AI no son panoramas 360° perfectos.
- **Panoramas generados por AI:** Calidad variable, algunos salen distorsionados.
- **Sin escaneo 3D:** Para tours tipo Matterport real se necesita cámara 360°.

### Performance
- **Renders lentos:** 30-90 segundos por imagen con servicios gratis.
- **localStorage limitado:** ~5-10MB, los proyectos con muchas imágenes base64 pueden llenar el espacio.
- **XSS potencial:** innerHTML sin sanitizar en varios lugares.

---

## 🗺️ Roadmap — Próximos Pasos

### Fase 1: Estabilización (Prioridad CRÍTICA)
- [ ] **Backend simple** (Node.js/Express o Python FastAPI)
  - Proxy para API calls (ocultar keys)
  - Persistencia real (Supabase o Firebase)
  - Rate limiting
  - Autenticación real con JWT
- [ ] **Sanitizar HTML** (DOMPurify para evitar XSS)
- [ ] **Modularizar código** (separar en archivos JS + CSS)
- [ ] **Error handling robusto** en todas las funciones

### Fase 2: Mejoras de Calidad
- [ ] **Mejor generación de imágenes**
  - Integrar Flux Pro (fal.ai) con API pagada para calidad premium
  - Opción "preview gratis → versión HD pagada"
  - img2img: usar render como referencia para mantener coherencia
- [ ] **Tour virtual mejorado**
  - Gaussian splatting para modelos 3D
  - Video transiciones entre habitaciones (Pollinations video)
  - Sonidos por habitación (agua en piscina, pájaros afuera)
- [ ] **Editor de planos interactivo**
  - Canvas drawing para modificar planos
  - Arrastrar/soltar muebles
  - Cálculo automático de m² al dibujar

### Fase 3: Producto Profesional
- [ ] **Multi-usuario real** con base de datos
  - Roles (admin, editor, viewer)
  - Log de actividad detallado
  - Permisos por proyecto
- [ ] **Dominio propio** (cayenabuilder.com)
- [ ] **WhatsApp/Telegram bot**
  - Cliente envía fotos → bot genera tour
  - Integración con API de WhatsApp Business
- [ ] **Exportaciones avanzadas**
  - Video walkthrough (MP4) generado automáticamente
  - Embed code para tour (iframe para websites)
  - Integración con portales inmobiliarios (Zillow, Idealista)

### Fase 4: Escala
- [ ] **SaaS público**
  - Planes: Free (5 renders/mes), Pro ($29/mes), Enterprise
  - Dashboard de analytics
  - Equipo colaborativo
- [ ] **API pública** para integración con otras plataformas
- [ ] **Marketplace de estilos** (paquetes de estilo descargables)
- [ ] **AI training personalizado** (fine-tune con renders aprobados)

---

## 🛠️ Stack Técnico Actual

| Componente | Tecnología |
|-----------|-----------|
| Frontend | Single HTML file, Vanilla JS, CSS |
| Tour 360° | Pannellum.js 2.5.6 |
| 3D Fallback | Three.js r128 |
| AI Chat | OpenRouter (free), Groq, OpenAI, Claude |
| AI Images | AI Horde, OpenRouter Gemini, Pollinations, Together.ai |
| AI Vision | Qwen VL 72B (free via OpenRouter) |
| Web Search | DuckDuckGo (free, unlimited) + SerpAPI (fallback) |
| Location | SerpAPI Google Maps |
| Audio | Freesound.org CDN |
| Hosting | Render.com (static site) |
| Storage | localStorage (browser) |

---

## 📊 Métricas del Código

| Métrica | Valor |
|---------|-------|
| Total commits | 85 |
| Archivo principal | index.html (~8000+ líneas) |
| Funciones JS | 100+ |
| Proveedores de imagen | 5 (race mode) |
| Modelos AI chat | 6+ free + 3 paid |
| Tests automáticos | 40+ |
| Usuarios | 4 |
| Regiones geo | 4 |

---

## 👥 Equipo

| Usuario | Rol | Color |
|---------|-----|-------|
| ISA (💩) | — | Rosa |
| JAG (🤬) | — | Dorado |
| PAM (🥰) | — | Azul |
| ALV (👨‍💻) | — | Verde |

---

*Generado el 3 de abril de 2026 por CayenaBot AI*
