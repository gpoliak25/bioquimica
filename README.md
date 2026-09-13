# Laboratorio conectado · EISPLUS

Propuesta de solución para dos necesidades planteadas desde la práctica bioquímica:
un **catálogo maestro de análisis** integrado a la receta electrónica, y una **bolsa de
reactivos en red** montada sobre ARCION.

El repositorio contiene la presentación de la propuesta y un prototipo funcional de ambos
módulos. Los dos son archivos HTML autocontenidos: se abren en cualquier navegador, sin
dependencias ni build.

## Contenido

| Archivo | Qué es |
|---|---|
| `laboratorio-conectado.html` | Presentación de la propuesta. 12 diapositivas: punto de partida, los dos módulos, arquitectura de integración, valor por actor y hoja de ruta. Se navega con las flechas, la barra espaciadora o el clic. |
| `demo-laboratorio-conectado.html` | Prototipo funcional de los dos módulos, para mostrar en vivo lo que la presentación describe. |

## El prototipo

**Módulo 1 · Catálogo maestro en la receta electrónica.** 92 registros tipificados, cada uno
con analito, momento de la toma, método, tipo de muestra, unidad, valor de referencia y
mapeo a NBU y LOINC. La búsqueda resuelve sinónimos —"azúcar" encuentra glucemia,
"transaminasas" encuentra TGO y TGP— y hay nueve perfiles que cargan varios registros
exactos de un clic. Al emitir la orden se compara la indicación en texto libre de hoy
contra la orden codificada y agrupada por tubo.

**Módulo 2 · Bolsa de reactivos.** Excedentes publicados por laboratorios de la red con
lote, vencimiento semaforizado, determinaciones disponibles, precio por uso y reglas de
aptitud. Reservar descuenta stock, calcula el pago previo y el ahorro frente a reponer el
kit, y genera el asiento de liquidación. También se puede publicar un excedente propio.

**Trazabilidad.** El código del análisis y el lote del reactivo recorren cada uno su
circuito y se cruzan en el momento del procesamiento. La vista se alimenta de lo que se
haga en los otros dos módulos.

El botón *Guion de demostración*, en la barra lateral, trae los cinco pasos sugeridos para
presentarlo; *Reiniciar demo* deja el prototipo limpio entre reuniones.

## Cómo verlo

Basta con abrir cualquiera de los dos archivos con doble clic. Para servirlos por HTTP —
útil si se quiere abrir desde otro dispositivo de la red — alcanza con un servidor
estático apuntado a la raíz del repositorio, por ejemplo:

```
npx --yes serve .
```

## Sobre los datos

Todos los datos del prototipo son de ejemplo y están marcados como tales en la interfaz.
El catálogo es un subconjunto representativo del volumen propuesto de ~10.000 registros.
Los vencimientos de los reactivos se calculan como desplazamiento desde la fecha actual,
de modo que la demo no se desactualiza. Los importes en pesos son plausibles pero deben
ajustarse con valores reales de la red antes de usarlos frente a un interlocutor técnico.
