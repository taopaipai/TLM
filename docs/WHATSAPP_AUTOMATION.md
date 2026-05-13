# Configuración de WhatsApp Empresa y Automatización - TLM

Este documento detalla la lógica de automatización para el canal de WhatsApp de TLM Telecomunicaciones, diseñada para filtrar prospectos y agendar reuniones técnicas de forma automática.

## 1. Canal y Tecnología
- **Plataforma:** WhatsApp Business API.
- **Integración:** Connectado vía Webhooks a **Make (Integromat)** y de ahí al CRM en **Notion**.
- **Bot de Triaje:** Diseñado para identificar si el lead es **Empresarial** o **Residencial/Parcela**.

## 2. Flujos de Conversación (Árbol de Decisión)

### A. Mensaje de Bienvenida (Trigger: Cualquier mensaje entrante)
> "¡Hola! 👋 Gracias por contactar a TLM Telecomunicaciones. Soy el asistente virtual de Esteban Negrete. Para ayudarte mejor, por favor selecciona una opción:"
- [Botón 1] Proyecto Empresarial / Industrial 🏢
- [Botón 2] Proyecto Parcela / Residencial 🏡
- [Botón 3] Soporte Técnico (Clientes actuales) 🔧

### B. Flujo Empresarial (B2B)
1. **Pregunta:** "¿En qué zona se encuentra tu empresa/planta? (Norte, Centro, Sur)"
2. **Pregunta:** "¿Qué solución necesitas? (Fibra Óptica, CCTV, Telemetría/Wise, Respaldo Energía)"
3. **Pregunta:** "¿Es una instalación nueva o una falla crítica?"
4. **Acción:** 
   - Si es **Falla Crítica**: Alertar a Esteban inmediatamente vía Telegram/Notificación Push.
   - Si es **Instalación Nueva**: "Excelente. Para una evaluación técnica senior, por favor elige un horario para una llamada con Esteban: [Link a Calendly]".
5. **Cierre:** Registrar en Notion con etiqueta `Fuente: WhatsApp` y `Tipo: Empresa`.

### C. Flujo Parcela / Rural (B2C)
1. **Pregunta:** "¿En qué zona se encuentra tu parcela? (Ej: Pucón, Villarrica, Puerto Varas)"
2. **Pregunta:** "¿Tienes factibilidad eléctrica o necesitas soluciones 100% solares?"
3. **Acción:** "Entendemos lo importante que es la seguridad en zonas rurales. Te enviaremos nuestro catálogo de soluciones solares y Starlink optimizado. ¿Te gustaría agendar una breve llamada de factibilidad?"
4. **Cierre:** Registrar en Notion con etiqueta `Fuente: WhatsApp` y `Tipo: Parcela`.

## 3. Automatización de Agendamiento
Se utilizará **Calendly** integrado con el calendario de Google de Esteban. 
- Los horarios disponibles serán de Lunes a Viernes de 09:00 a 11:00 (bloque de ventas).
- Al confirmar el agendamiento, Calendly actualiza el registro en Notion a `Estado: Reunión Agendada`.

## 4. Respuesta a Consultas Fuera de Horario
> "Actualmente nuestro equipo técnico está fuera de línea (o en terreno 🏔️). Hemos registrado tu consulta y Esteban te contactará a primera hora del próximo día hábil. ¡Gracias por tu paciencia!"

---
*Configurado por el equipo de Ingeniería Move iT para TLM SPA*
