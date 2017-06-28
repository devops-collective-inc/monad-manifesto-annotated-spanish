# Capítulo 1 - ¿Qué es Monad?
___
Monad [^1-1] [^1-2] es la próxima generación de plataformas para la automatización administrativa. Monad resuelve los problemas de gestión tradicionales aprovechando la [Plataforma .NET](http://bit.ly/1PAsRao). Desde el primer prototipo (limitado), se pueden resaltar beneficios significativos para desarrolladores, testers, usuarios avanzados y administradores. Monad aprovecha [^ 1-6] el [.NET Common Runtime](http://bit.ly/1Q0TrV3) Runtime para proporcionar un potente, consistente, intuitivo, extensible y útil conjunto de herramientas que reducen los costos de administración y hacen que la vida de los no programadores sea mucho más sencilla. 

Monad consta de:

1. [Monad Automation Model (MAM)](): Un modelo de automatización basado en [clases .NET](http://bit.ly/1R9oPTO), métodos y atributos para producir [Cmdlets](https://msdn.microsoft.com/en-us/library/ms714395(v=vs.85).aspx).[^1-3]
2. [Monad Shell (MSH)](): Un entorno de ejecución de scripts basado en .NET para exponer los Cmdlets como herramientas de línea de comandos de [API](https://msdn.microsoft.com/en-us/library/ms123401.aspx) y un shell de línea de comandos programable e interactivo.
3. [Monad Management Models (MMM)](): El conjunto con las clases de base de código administrado (o interfaces) para implementar escenarios de administración específicos y herramientas administrativas in-the-box para ejecutar esos escenarios.  
4. [Monad Remote Scripting (MRS)](): Conjunto de componentes basados en  [Web Services](https://msdn.microsoft.com/en-us/library/ms950421.aspx) que permiten ejecutar secuencias de comandos remotamente en muchas máquinas [^1-4].
5. [Monad Management Console (MMC)](): Un modelo basado en .NET y un conjunto de servicios para la creación de GUIs de administración sobre [MSH](https://technet.microsoft.com/en-us/magazine/2005.11.scripting.aspx) exponiendo todas las interacciones de GUI como secuencias de comandos visibles por el usuario [^1-5].

Este [white paper](https://en.wikipedia.org/wiki/White_paper) presenta el enfoque tradicional de la automatización administrativa, sus fortalezas y deficiencias. A continuación, se presenta una visión general de los principales componentes de Monad. Un conjunto de [propuestas de valor](https://en.wikipedia.org/wiki/Value_proposition) se articula entonces para las audiencias objetivo de Monad.

___

**Notas:**

[^1-1]: (ORIGINAL) Este no es un documento técnico de Windows PowerShell ni es una descripción precisa de cómo funciona [V1.0](http://blogs.msdn.com/b/powershell/archive/2006/11/14/windows-powershell-1-0-released.aspx). Esta es una versión del original Manifiesto de Monad que articuló la visión a largo plazo y comenzó el esfuerzo de desarrollo que se convirtió en [PowerShell](http://bit.ly/1Q0TyzZ). Muchos de los elementos descritos en este documento han sido liberados y otros han proporcionado una buena hoja de ruta para el futuro. El documento se ha actualizado para su publicación. La información confidencial ha sido eliminada y los ejemplos se actualizan para reflejar la sintaxis actual.

[^1-2]: (ORIGINAL) [Monad](https://en.wikipedia.org/wiki/Monadology) es el término de [Leibniz’s](https://en.wikipedia.org/wiki/Gottfried_Wilhelm_Leibniz) utilizado para describir una unidad fundamental a la que luego se agregan componentes para implementar un propósito. En esta filosofía, todo es una composición de Monads. Esto captura lo que queremos lograr con una gestión [compuesta](https://en.wikipedia.org/wiki/Composability). Más información sobre Monad se puede encontrar en: [http://www.wise.virginia.edu/philosophy/phil206/Leibniz.html](http://www.wise.virginia.edu/philosophy/phil206/Leibniz.html)

[^1-3]: La versión 1 de PowerShell se liberó en 2006 y proporcionó la implementación de cmdlets. Los cmdlets de hoy se escriben en [lenguajes .NET](https://en.wikipedia.org/wiki/List_of_CLI_languages) y consisten en una sola clase por cada cmdlet. PowerShell proporciona una clase base que hace mucho del trabajo pesado. Los desarrolladores definen las propiedades de la clase que se convierten en parámetros y reemplazan métodos específicos para participar en el ciclo de vida de la canalización en el pipeline. Los cmdlets, junto con el entorno general, fueron el primero de los cuatro puntos de visión principales que se proponen en el Manifiesto.

[^1-4]: Remoting fue introducido en PowerShell [versión 2](http://blogs.msdn.com/b/powershell/archive/2009/07/23/windows-powershell-2-0-rtm.aspx), que se liberó con Windows Vista y Windows Server 2008. [Remoting](https://technet.microsoft.com/en-us/magazine/ff700227.aspx) es el segundo de los cuatro puntos de visión principales propuestos en el Manifiesto.

[^1-5]: Aunque nunca se expuso como una [MMC](https://msdn.microsoft.com/en-us/library/bb742441.aspx) per se, el motor de PowerShell se implementó como una clase .NET. Cualquier aplicación .NET puede instanciar el motor, ejecutar comandos y traducir la salida a una pantalla GUI. [Exchange Server 2007](https://technet.microsoft.com/en-us/magazine/2006.12.managementshell.aspx) fue el primer producto que lo hizo y sigue siendo uno de los mejores ejemplos del "enfoque completo de PowerShell" para la administración.

[^1-6]: Debe tenerse en cuenta que PowerShell casi no existe debido a su dependencia de .NET. En el período 2004-2006, un número sorprendente de proyectos de código gestionado de alto perfil fallaron, lo que contribuyó a los retrasos de Windows Vista. Depender de algún lenguaje de scripting de administración escrito en .NET no era políticamente correcto en ese momento. De hecho, era tan arriesgado que hizo que el equipo de Exchange Server construyera toda su _API intermedia_ bajo Cmdlets de PowerShell, con la teoría de que podrían desechar dichos cmdlets y reemplazarlos por otra cosa, si fuera necesario



