# Capítulo 3 - El enfoque tradicional de la automatización administrativa

El modelo tradicional [^3-1] para la automatización administrativa es potente y exitoso. Consiste en:

1. Un shell de programación (por ejemplo, sh, csh, ksh, bash) [^3-5]
2. Un conjunto de comandos administrativos (por ejemplo, ifconfig, ps, chmod, kill)
3. Un conjunto de utilitarios para manipulación de texto (por ejemplo, awk, grep, sed).
4. GUIs administrativas superpuestas a los comandos y los utilitarios

La filosofía de este modelo es que cada ejecutable debe hacer un pequeño conjunto de funciones, para que las funciones más complejas sean compuestas a través del uso de pipelining o una secuencia de ejecutables que se llaman unos a otros. Este modelo ha sido muy exitoso a pesar de tener algunos inconvenientes. Tras la inspección, lo que es ampliamente considerado como un bastión UNIX es de hecho una implementación defectuosa de este modelo [^3-2].

Cuando retrocede y examina lo que realmente sucede cuando alguien usa un comando pipelinado (si se me permite inventar esta palabra) como en "$ a | b | c", se concluye que el primer comando, es decir, "a" no logró lo que el administrador quería hacer. Si lo hubiera hecho, el administrador sólo tendría que haber escrito "a" y listo. Entonces, la pregunta es ¿por qué "a" no hizo lo que el administrador quería? La respuesta es que en este modelo tradicional, los ejecutables autónomos unen firmemente tres operaciones: 1) obtener objetos; 2) procesamiento de objetos; 3) salida de resultados como texto [^3-4]. Una de esas operaciones no hace lo que el administrador necesita, así que el resto de la tubería es un intento de corregir eso.

Debido a que el ejecutable genera texto, los elementos descendentes deben utilizar utilidades de manipulación de texto para intentar volver a los objetos originales y realizar trabajo faltante. Si bien el modelo básico es extremadamente poderoso, su defecto intrínseco es la estrecha vinculación de estas operaciones y el uso de texto no estructurado para la integración [^3-3]. Esto requiere utilitarios para la manipulación de texto torpes, con pérdidas e imprecisiones.

El modelo tradicional refleja el estado de la tecnología que estaba disponible en el momento en que surgió. .NET proporciona [^3-6] un nuevo conjunto de capacidades y abre la posibilidad de nuevos enfoques. Estos nuevos enfoques nos permiten sustituir el modelo tradicional por uno decisivamente superior. Ese modelo es lo que llamamos Monad

---
**Notas**

[^3-1]: Tradicional en el mundo Linux/Unix, pero no en Windows. Este es, de hecho, el cambio que Snover proponía: hacer que la administración administrativa funcione más como en Unix, ya que Unix es un modelo probado de éxito desde hace décadas. Probablemente ayudo que Snover proviniera de Digital Computer, una compañía con bastante familiaridad en variantes de Unix y sistemas operativos similares.

[^3-2]: Las personas que ven PowerShell como "linux-ification" de Windows deben tener en cuenta que Snover no estaba enamorado del modelo de línea de comandos Unix. Él sentía que era inconsistente y que le faltaba una mejor semántica. De muchas maneras, PowerShell fue el primer "segundo vencedor" en el modelo de línea de comandos de Unix, tomando sus puntos fuertes, pero reconsiderando lo que se había convertido en debilidades algo obvias.

[^3-3]: Hay un punto enorme aquí que a menudo se pierde. Cuando se escribe una herramienta que produce texto, las herramientas descendentes tienen que saber cómo procesar ese texto en el formato exacto que se produjo. Sus datos no están estructurados. Si cambia la salida de su herramienta, todo lo que se utiliza para trabajar con ella tendrá que cambiar. La orientación de objetos, es decir, presentar los datos en una estructura estandarizada que podría ser consumida por cualquier cosa que entienda "objetos", fue una de las mayores diferencias entre PowerShell y lo que había antes. Gran parte del tiempo de un administrador de Linux se gasta en el ciclo grep/sed/awk, ya que tienen que analizar el texto para que la próxima herramienta tenga datos con los que trabajar. PowerShell casi que elimina ese trabajo por completo.

[^3-4]: El resultado práctico de esto es que las herramientas - cmdlets, en el mundo de PowerShell - deben hacer una cosa, y sólo una cosa. Obtener objetos, procesar objetos o formatear objetos desde texto. Elija sólo una cosa y haga sólo eso. Si hace más de una cosa, comienza a crear una herramienta monolítica que es menos fácil de reutilizar. Este concepto de una sola cosa se ha convertido en el fundamento de las mejores prácticas en la comunidad de PowerShell, especialmente en torno a la creación de herramientas.

[^3-5]: Estos ejemplos enfatizan la influencia que el mainframe y UNIX tenían en las opciones de diseño de Snover.

[^3-6]: De manera realista, COM podría haber proporcionado las mismas capacidades ya que estaba orientada a objetos. Sin embargo, en el momento en que se escribió el manifiesto, COM fue “acabado” y Microsoft se había trasladado a .NET
