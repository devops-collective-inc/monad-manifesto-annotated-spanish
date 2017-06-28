# The Monad Manifesto - Annotated

by Jeffrey Snover
as annotated by the PowerShell Community

---

Este proyecto está destinado a preservar [The Monad Manifesto](http://www.jsnover.com/blog/2011/10/01/monad-manifesto/), un documento escrito por el inventor de Microsoft Windows PowerShell [Jeffrey Snover](https://social.technet.microsoft.com/profile/Jeffrey%20Snover%20Windows%20Server) en Microsoft en 2002. La idea de este proyecto fue del autor de Pluralsight [Tim Warner](http://www.pluralsight.com/author/tim-warner), con las anotaciones iniciales que hicieroen Tim y el Microsoft MVP [Don Jones](https://twitter.com/concentrateddon).

El Manifiesto original era un documento prospectivo, anterior a la publicación pública de PowerShell por alrededor de 4 años. En los años transcurridos desde el lanzamiento de PowerShell [2006](http://blogs.msdn.com/b/powershell/archive/2006/11/14/windows-powershell-1-0-released.aspx), el producto ha evolucionado sustancialmente, pero siempre alrededor de los conceptos  descritos en el Manifiesto.

Consideramos que no sólo es importante conservar el documento con fines históricos, sino también anotar y ampliar los diversos conceptos que introduce. Intentaremos vincular las referencias de las tecnologías reales que el Manifiesto predijo y proporcionar explicaciones contextuales en torno a algunas de las directivas del Manifiesto.

Encontrará [^1] notas de pie de página en el texto. Éstas son una característica de [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) que no son compatibles con nuestra plataforma de publicación, pero están destinadas a vincular a las notas de pie de página correspondientes en la parte inferior de la página. En algunos casos, estas son las notas originales de Jeffrey marcadas como "ORIGINAL" para separarlas de las notas a pie de página que nosotros hemos añadido.

---

Esta guía se publica bajo la licencia Creative Commons Attribution-NoDerivs 3.0 Unported. Los autores le animan a redistribuir este archivo lo más ampliamente posible, pero le solicitan que no modifique el documento original.

**¿Ha sido útil este libro?** El (los) autor (es) le pide (n) que haga una donación deducible de impuestos (en los EE.UU., consulte sus leyes si vive en otro lugar) de cualquier cantidad a [The DevOps Collective](https://devopscollective.org/donate) para apoyar su trabajo.

** Revise las actualizaciones! ** Nuestros ebooks se actualizan a menudo con contenido nuevo y corregido. Los hacemos disponibles de tres maneras:

* Nuestra rama principal [GitHub organization](https://github.com/devops-collective-inc), con un repositorio para cada libro. Visite https://github.com/devops-collective-inc/

* Nuestra [GitBook page](https://www.gitbook.com/@devopscollective), donde puede navegar por los libros en línea, o descargarlos en formato PDF, EPUB o MOBI. Utilizando el lector en línea, puede saltar a capítulos específicos. Visite https://www.gitbook.com/@devopscollective

* En [LeanPub](https://leanpub.com/u/devopscollective), donde se pueden descargar como PDF, EPUB, o MOBI (login requerido), y "comprar" los libros haciendo una donación a DevOps. También puede elegir recibir notificaciones de actualizaciones. Visite https://leanpub.com/u/devopscollective

GitBook y LeanPub generan la salida del formato PDF ligeramente diferente, por lo que puede elegir el que prefiera. LeanPub también le puede notificar cada vez que liberamos alguna actualización. Nuestro repositorio de GitHub es el principal; los repositorios en otros sitios suelen ser sólo espejos utilizados para el proceso de publicación. GitBook normalmente contendrá nuestra última versión, incluyendo algunos bits no terminados; LeanPub siempre contiene la más reciente "publicación liberada" de cualquier libro.
