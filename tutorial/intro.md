<!-- markdownlint-disable MD002 MD041 -->

Hay más de 230 conectores no Box para Microsoft Flow. Muchos de estos conectores usan Microsoft Graph para comunicarse con extremos específicos de los productos de Microsoft, pero no hay ningún conector que se comunique directamente con Microsoft Graph para cubrir toda la API. Sin embargo, hay escenarios en los que es posible que debamos llamar a Microsoft Graph directamente desde el flujo mediante bloques de creación básicos del servicio.

Además de tratar los escenarios para llamar directamente a Microsoft Graph, una serie de puntos de conexión de la API de Microsoft Graph solo admiten [permisos delegados](https://docs.microsoft.com/graph/permissions-reference). El conector HTTP de Microsoft Flow permite integraciones muy flexibles, como la llamada a Microsoft Graph. Sin embargo, el conector HTTP carece de la capacidad de almacenar en caché las credenciales de un usuario para habilitar escenarios de permisos delegados específicos. En estos casos, se puede crear un conector personalizado para proporcionar un contenedor alrededor de la API de Microsoft Graph y habilitar el consumo de la API con permisos delegados.

Este laboratorio cubre los dos desafíos anteriores. En primer lugar, deberá crear un conector personalizado para habilitar integraciones con Microsoft Graph que requieran [permisos delegados](https://docs.microsoft.com/graph/permissions-reference). En segundo lugar, usará el [punto de conexión de $Batch request](https://docs.microsoft.com/graph/json-batching), para proporcionar acceso a toda la eficacia de Microsoft Graph mientras usa los permisos delegados que requieren que una aplicación tenga el usuario "que ha iniciado sesión".

> [!NOTE]
> Este es un tutorial sobre cómo crear un conector personalizado para su uso en Microsoft Flow y Azure LogicApps. En este tutorial se da por sentado que ha leído la [Introducción al conector personalizado](https://docs.microsoft.com/connectors/custom-connectors/) para comprender el proceso.

## <a name="prerequisites"></a>Requisitos previos

Para completar este ejercicio en esta publicación, necesitará lo siguiente:

- Acceso de administrador a un arrendamiento de Office 365. Si no tiene uno, visite el programa de [desarrolladores de Office 365](https://developer.microsoft.com/office/dev-program) para registrarse en un espacio empresarial gratuito para desarrolladores.
- Acceso a [Microsoft Flow](https://flow.microsoft.com/).

## <a name="feedback"></a>Comentarios

Envíe sus comentarios sobre este tutorial en el [repositorio de github](https://github.com/microsoftgraph/msgraph-training-microsoftflow).
