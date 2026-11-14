# Conclusiones

## Conclusiones y recomendaciones

### Conclusiones

**AV2:**

<ul>
  <li>
    <strong>Verificación del producto.</strong> Los tres productos de código cuentan con suites automatizadas que se
    ejecutan en cada Pull Request: 229 pruebas en Qualitrack-Platform, 870 en Qualitrack-WebApplication y 174 en
    Qualitrack-MobileApplication, todas aprobadas (sección 6.1). El análisis estático (sección 6.2) no encontró
    vulnerabilidades de seguridad reales en el código: las observaciones del backend son de estilo (697 de PMD, la
    mayoría por sentencias sin llaves), la web tiene 6 errores de lint corregibles y las 11 dependencias vulnerables
    reportadas por npm audit son de desarrollo y no llegan al bundle publicado. La aplicación móvil no presenta
    observaciones.
  </li>
  <li>
    <strong>Revisión de código.</strong> La verificación mostró que casi todos los Pull Requests se integraron sin una
    aprobación formal registrada en GitHub. Es el principal hallazgo de proceso del avance y dio lugar a las reglas de
    revisión de la sección 6.2.2.
  </li>
  <li>
    <strong>Pipeline DevOps.</strong> La integración continua (sección 7.1) y el despliegue continuo a Azure Container
    Apps, Firebase Hosting y GitHub Pages (secciones 7.2 y 7.3) ya funcionan; el último release de cada producto
    (backend v1.2.0, web v2.5.0 y Landing Page v1.1.0) llegó a producción a través de ese pipeline. En cambio, el
    monitoreo continuo (sección 7.4) está diseñado pero todavía no implementado: el código no incluye health checks,
    Application Insights, Crashlytics ni analítica.
  </li>
  <li>
    <strong>Problem Statement.</strong> El Problem Statement de la sección 1.2.2.1 plantea reducir el tiempo
    entre la aparición de una desviación ambiental, su identificación y la acción tomada. El producto actual ya registra
    cuándo se crea, se reconoce y se resuelve cada alerta, y avisa al usuario mediante la campana de notificaciones y un
    correo por cada alerta crítica, lo que permite medir ese tiempo (MTTA y MTTR).
  </li>
  <li>
    <strong>Experimentación.</strong> El Capítulo VIII convirtió las preguntas abiertas del negocio en experimentos
    medibles. Las dos preguntas de mayor puntaje del Question Backlog atacan directamente el Problem Statement: un banner
    de alertas críticas en la web (EXP-01, medido con el MTTA) y las notificaciones push en la aplicación móvil (EXP-02,
    medido con el porcentaje de alertas reconocidas en 15 minutos). Esta última responde al assumption de que los
    responsables de calidad no permanecen todo el tiempo en las instalaciones. Cada experimento tiene hipótesis nula y
    alternativa, tamaño de muestra calculado (α = 0.05, potencia 80 %) y un tracking plan, y quedó traducido en 13 ítems
    del To-Be Product Backlog (38 story points).
  </li>
  <li>
    <strong>Responsabilidad ética.</strong> Los experimentos se diseñaron para que ninguna condición de control quite
    información de alertas a los usuarios (ambas conservan la campana y el correo) y para que el tracking plan no
    registre datos personales ni credenciales.
  </li>
</ul>

### Recomendaciones

**AV2:**

<ul>
  <li>
    Implementar primero la instrumentación del To-Be Product Backlog (analítica, asignación a variantes y health check
    del backend), porque sin ella no es posible medir ningún experimento ni operar el monitoreo continuo.
  </li>
  <li>
    Ejecutar EXP-01 antes que EXP-02, como se definió en el Capítulo VIII, para no exponer a los mismos usuarios a dos
    experimentos sobre la atención de alertas al mismo tiempo.
  </li>
  <li>
    Activar en los repositorios de producto la protección de ramas con al menos una aprobación y el pipeline en verde,
    corregir los 6 errores de lint de la web y actualizar las dependencias de desarrollo señaladas por npm audit.
  </li>
  <li>
    Incorporar al pipeline de integración continua de la web los scripts de navegador de Playwright, que hoy se ejecutan
    solo de forma local, y automatizar la distribución del APK de la aplicación móvil.
  </li>
  <li>
    Para el roadmap de los productos: implementar las notificaciones push en la aplicación móvil (hoy pendientes) y
    usar los resultados de EXP-01 a EXP-03 para decidir qué variantes se adoptan de forma definitiva en la web, la
    aplicación móvil y la Landing Page.
  </li>
</ul>

## Video App Validation

[POR COMPLETAR: resumen del video de validación de la aplicación, URL de la versión publicada, duración y captura
representativa.]

## Video About-the-Team

[POR COMPLETAR: resumen del video About-the-Team, pauta de secuencias con el tiempo de inicio de cada sección
(hh:mm:ss), cuadro representativo, URL de la versión publicada en Microsoft Stream y URL de la versión publicada en
YouTube.]

<div style="page-break-after: always;"></div>
