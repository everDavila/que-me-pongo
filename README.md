# Outfit

Outfit es un armario digital inteligente que ayuda a responder una pregunta cotidiana: **¿qué me pongo?**

No busca ser solo un catálogo de ropa. El usuario registra las prendas que realmente tiene y Outfit recomienda combinaciones apropiadas para su contexto, de forma explicable y consistente.

> Outfit sabe qué tienes y te ayuda a decidir qué ponerte.

## Problema

Decidir qué usar consume tiempo y energía, incluso cuando el armario está lleno. Las alternativas existentes suelen centrarse en digitalizar prendas o generar inspiración genérica; Outfit se centra en la **decisión**, usando el inventario real de cada persona.

La digitalización del armario es infraestructura. La recomendación es el producto.

## Cómo funciona

El usuario registra sus prendas y, cuando necesita decidir, proporciona un contexto breve —por ejemplo: “tengo una cena con amigos y mi profesor, hace calor y no quiero verme demasiado formal”—.

Outfit transforma ese contexto en criterios como ocasión, formalidad, clima y restricciones. Luego, su motor de recomendación evalúa combinaciones válidas de prendas disponibles, las ordena y ofrece una sugerencia con una explicación útil.

```text
inventario + contexto + reglas + preferencias
                    ↓
         candidatos de outfits válidos
                    ↓
            scoring y recomendación
```

El motor de outfits es propio: no depende de un LLM como fuente de decisión. Un LLM podría utilizarse más adelante para interpretar lenguaje natural ambiguo o explicar una sugerencia, pero no para elegir combinaciones de forma aleatoria.

## MVP

El MVP valida esta hipótesis:

> Si Outfit conoce suficientemente bien mi armario, puede reducir significativamente la fricción de decidir qué ponerme.

El ciclo a probar es:

1. Registrar prendas.
2. Contar con un armario estructurado.
3. Indicar el contexto.
4. Recibir una combinación.
5. Aceptarla, cambiarla o rechazarla.
6. Aprender de esa decisión.

Incluye inicialmente:

- Registro rápido de prendas mediante foto, con atributos sugeridos y confirmación del usuario.
- Prendas clasificadas por categoría, tipo, color, patrón, clima y formalidad cuando haya suficiente certeza.
- Tops, bottoms, calzado y accesorios como categorías de primera clase.
- Recomendaciones basadas en ocasión, formalidad, clima, preferencias, compatibilidad y restricciones.
- Reglas comprensibles, como sugerir correa marrón con zapatos marrones o penalizar prendas pesadas cuando hace calor.
- Señales de aprendizaje a partir de aceptaciones, reemplazos, rechazos y frecuencia de uso.

## Principios de producto y UX

- **Reducir decisiones:** evitar configuraciones largas y filtros innecesarios cada mañana.
- **Usar la ropa real:** recomendar exclusivamente desde el armario del usuario.
- **Explicar cuando aporte valor:** una recomendación debe poder justificarse.
- **Automatizar sin fingir certeza:** si una detección no es fiable, pedir confirmación o corrección.
- **Mobile-first y baja fricción:** registrar ropa no debe sentirse como administrar una base de datos.
- **Aprender progresivamente:** preferir señales de comportamiento antes que cuestionarios extensos.

## Casos de uso futuros

### Conversación contextual

Interpretar solicitudes naturales y convertirlas en criterios estructurados antes de que el motor haga la recomendación.

### Cápsulas para viajes

Proponer qué llevar considerando días, actividades, clima, equipaje, reutilización y versatilidad; optimiza un conjunto completo, no una lista de outfits independientes.

### Integración con Nimbus

Nimbus es un producto independiente que podría aportar clima y contexto con permiso del usuario. Outfit conservaría el inventario y el motor de vestimenta. La arquitectura debe permitir una API futura, sin sobrearquitecturar el MVP para esta integración.

## Estado del proyecto

Outfit está en fase de definición de producto y arquitectura. Aún no se han decidido el framework, backend, proveedor de datos, modelo de visión, LLM, Jev ni los pesos exactos del algoritmo.

Las decisiones estructurales se evaluarán antes de implementarse: alternativas, trade-offs y recomendación. Las decisiones pequeñas y reversibles pueden avanzar sin burocracia innecesaria.
