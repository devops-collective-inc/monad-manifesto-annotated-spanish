# Capítulo 4 - Nuevos enfoques
___
Monad adopta nuevos enfoques a los problemas de 1) construcción de comandos, 2) composición de soluciones 3) modelos de gestión y 4) GUI de gestión. La arquitectura de Monad proviene de las siguientes observaciones:

1. La mayoría de las soluciones son desarrolladas “in house” y compuestas por comandos existentes por los administradores.
2. La mayoría de las soluciones se centran en la automatización de la gestión o la provisión de correcciones ad hoc.
3. La mayoría de los administradores no son programadores “natos”. O bien no tienen el deseo, la habilidad o (más a menudo), el tiempo para hacer una programación sofisticada.
4. La mayoría de los desarrolladores de aplicaciones no harán que su código sea manejable a menos que haya un beneficio inmediato y sustancial para el usuario [^4-5]

## 4.1 - Un nuevo enfoque para construir comandos
El enfoque tradicional de la construcción de comandos es ineficiente. Gran parte del esfuerzo se dedica a reescribir las mismas funciones una y otra vez por diferentes personas de diferentes maneras. Todos para:

  * Analizar, validar y codificar la entrada de usuario.
  * Documentar su uso.
  * Dejar registro de actividades.
  * Formatear datos, resultados de salida e informes de errores.
  * Operar en nodos remotos o conjuntos de nodos remotos.
   
Sin embargo, a pesar de toda esta coincidencia, la mayoría de las plataformas [^4-1] [^4-2] proporcionan poco o ningún apoyo para hacer estas actividades de manera coherente. El resultado es que los comandos de hoy en día son ineficientes para desarrollar e inconsistentes en su forma de usar [^4-6].

Monad adopta un enfoque diferente que proporciona a los desarrolladores el máximo aprovechamiento y la máxima consistencia para los usuarios finales, mediante la definición de un modelo de automatización para aplicaciones que afecta a las funciones comunes para que puedan implementarse una vez en un entorno de ejecución común [^4-3]. Los desarrolladores ya no producen ejecutables autónomos. En su lugar, escriben piezas de código muy enfocadas como  clases .NET (Cmdlets) que luego se exponen como API, comandos e interfaces gráficas. Las funciones comunes se implementan y prueban una vez y proporcionan un conjunto único de semántica, así como un conjunto coherente y uniforme de mensajes de error. [^4-7]

## 4.2 - Un nuevo enfoque para componer soluciones
El enfoque tradicional para componer soluciones es difícil y frágil. Utiliza “pipelines” para realizar análisis basado en oraciones de flujos de texto [^4-4]. Estos mecanismos son incómodos, inconsistentes e imprecisos. Los administradores pasan la mayor parte de su tiempo buscando mecanismos para resolver problemas, en lugar de resolver dichos problemas. Monad tiene un enfoque diferente que proporciona un motor de ejecución de secuencias de comandos preciso y potente para crear tuberías (pipelines) de objetos .NET. En lugar de canalizar texto no estructurado, canalizamos objetos .NET [^4-8]. Esto permite que los componentes de la canalización (pipelines) operen a bajo nivel directamente sobre los objetos y sus propiedades utilizando las API [.NET Reflection](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/cpguide/html/cpconreflectionoverview.asp). (Las API de Reflection permiten encontrar el tipo de un objeto, las propiedades y métodos que tiene, obtener los valores de propiedades e invocar sus métodos).

El entorno de tiempo de ejecución de Monad proporciona un medio para acceder a los cmdlets y ejecutar secuencias de comandos en máquinas remotas a través de Web Services. [^4-9]

## 4.3 - Un nuevo enfoque de los modelos de gestión

El enfoque tradicional de los modelos de gestión produce una experiencia de administración inconsistente. Hoy en día hay miles de comandos optimizados localmente. Cada desarrollador de comandos define su propio modelo de gestión con un conjunto de nombres y conceptos. Mientras se produce la copia de comandos populares, no hay incentivo sistémico para hacerlo. Se han hecho esfuerzos para proporcionar directrices que impulsen la optimización global, pero el peso del legado ha dificultado que tales esfuerzos ganen mucha fuerza.

Una situación similar existe con las tecnologías de instrumentación actuales que languidecen debido a la falta de soporte de herramientas. Los esfuerzos de evangelización por instrumentación son difíciles a medida que los grupos [de productos] rechazan la estrategia "construye y vendrá". Los desarrolladores de herramientas se resisten a la vasta superficie de los objetos y responden proporcionando una funcionalidad genérica (como supervisión o navegación) a través de una amplia gama de objetos o proporcionando funciones complejas para un pequeño conjunto de problemas.

Monad adopta un enfoque diferente: minimiza el coste de la automatización y proporciona un beneficio inmediato para el usuario final proporcionando **clases de extensión de automatización** basadas en escenarios y herramientas in-the-box que explotan esas clases. Monad puede soportar casi cualquier esquema de automatización, pero alienta firmemente el uso de esquemas estándar proporcionando un conjunto de clases base para escenarios administrativos específicos. Estas clases base incluyen: Navegación, Diagnóstico, Configuración, Ciclo de Vida y Operaciones [^4-10]. Dichas clases proporcionan una sintaxis común, conmutadores, mensajes de error internacionalizados y soluciones a problemas de escenarios comunes (por ejemplo, una implementación común de una pila de directorios para todos los comandos de navegación). Monad también proporciona un conjunto de controles de interfaz de usuario y herramientas que se suministran con el sistema operativo que controla dichas extensiones para realizar una tarea de gestión específica


## 4.4 - Un Nuevo Enfoque a las Herramientas GUI de Gestión

El enfoque tradicional de las GUI de administración proporciona un mínimo de apalancamiento para desarrolladores. Las herramientas de GUI de administración de Windows de hoy en día se desarrollan de la misma manera que una aplicación completa. Tienen código de interfaz gráfica de usuario, aplicación de lógica de dominio/restricción y acceso de API a objetos administrados locales y remotos. Los servicios de GUI de gestión se limitan en gran medida a un contenedor de interfaz de usuario que facilita la multiplexación de varias herramientas y un cierto nivel de integración. Este enfoque requiere un esfuerzo significativo y un conjunto de pruebas exhaustivo. Dado que gran parte de la lógica del dominio y la imposición de restricciones está incrustada en la GUI, es común que las líneas de comandos expongan un subconjunto de las funciones de una GUI. El enfoque tradicional funciona en contra de la automatización.

Monad adopta un enfoque diferente que proporciona un rico conjunto de servicios orientados a la gestión para desarrollar herramientas de GUI de gestión. Estos servicios permiten que las GUI de administración se superpongan al motor de secuencias de comandos y Cmdlets. Esto proporciona auditoría, grabación/reproducción de macros y herramientas integradas de GUI/línea de comandos. Esto disminuye el nivel de habilidad requerido para desarrollar una GUI de administración, al simplificar el acceso y el control de los objetos de administración transparentes de manera remota. También permite a los usuarios ver los scripts ejecutados por las interacciones GUI que les ayuda a aprender la capa de automatización y crear sus propios scripts automatizados. La estratificación reduce la matriz de pruebas aprovechando las pruebas realizadas en la línea de comandos y las secuencias de comandos y solo es necesario probar las rutas GUI para invocar esas funciones. La GUI de administración también puede exponer su funcionamiento interno a través de Cmdlets que proporciona a los desarrolladores, probadores y soporte un fácil acceso al estado interno y el control de la GUI para la depuración/diagnóstico/prueba automatizada.

___

**Notas**:
 [^4-1]: ORIGINAL: UNIX tiene [getopt ()](http://www.gnu.org/software/libc/manual/html_node/Using-Getopt.html) para el análisis simple de opciones de comandos.

[^4-2]: ORIGINAL: [VMS DCL](http://h71000.www7.hp.com/doc/732final/9996/9996pro.html) y AS400's CL son las excepciones a esto. Proporcionan un analizador de comandos común para que los comandos que se usan tengan un alto grado de consistencia sintáctica.

[^4-3]: ORIGINAL: Existe una maravillosa sinergia entre el deseo del programador de minimizar la cantidad de código que escribe para la administración y los clientes que desean tener una experiencia de administración consistente.

[^4-4]: El análisis basado en la oración es cuando analiza el texto y luego ora para que lo entienda correctamente. p.ej. Cortar las primeras 3 (¿o eran 4?) Líneas, recortar la columna 30-40 (suponiendo que esos espacios no son Tabs), convertir a un entero (hmm. - ¿Alguien utiliza 64 bits? ... bueno espero que sea de 32 bits).

[^4-5]: Lo que significa que la mayoría de los desarrolladores no implementarán interfaces que los administradores puedan usar para administrar la aplicación. En el mejor de los casos, un desarrollador "perezoso" podría simplemente poner toda su información de configuración en un archivo de texto y llamarla "manejable". Irónicamente, eso es esencialmente como Unix se construyó desde cero, y _es manejable_, porque no es tan fácil como modificar un archivo de texto, especialmente si está estructurado (como en JSON o XML).

[^4-6]: Es por eso que los desarrolladores odian hacerlos y los administradores odian usarlos.

[^4-7]: Este es el modelo adoptado por PowerShell. Los cmdlets son instancias de una clase, que heredan de una única base. Esa clase proporciona una tonelada de funcionalidad común, de modo que el código real en un cmdlet está alrededor del 99% centrado en lo que sea que el cmdlet esté haciendo. El desarrollador del cmdlet no se centra en analizar los argumentos de la línea de comandos, validar los elementos obligatorios, etc.

[^4-8]: Un "objeto" en este sentido es poco más que un conjunto de datos estructurados, a diferencia de una tabla de base de datos o una hoja de cálculo. Cada objeto representa algún componente de gestión, y sus propiedades representan bits de información sobre ese objeto. Los comandos no tienen que analizar estos objetos para encontrar datos, ya que .NET entiende la estructura del objeto y puede simplemente recuperar los bits de información haciendo referencia a los nombres de propiedades.

[^4-9]: Una de las primeras referencias directas a lo que se convirtió en PowerShell Remoting, que de hecho es un servicio web basado en WS-MAN (Web Services for Management).

[^4-10]: PowerShell nunca tuvo clases bases específicas para estos escenarios, pero este fue el origen de la lista estandarizada de verbos de PowerShell  que se utilizaron en los nombres de cmdlet. Este concepto también impulsó la creación de las abstracciones PSProvider y PSDrive, en el que cualquier almacén de datos podría ser expuesto como una "unidad de disco", lo que permite un conjunto estandarizado de comandos para manipular cualquier almacén de datos expuestos.
