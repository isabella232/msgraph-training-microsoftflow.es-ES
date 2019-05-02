<!-- markdownlint-disable MD002 MD041 -->

En este ejercicio, creará una nueva aplicación de Azure Active Directory que se usará para proporcionar los permisos delegados para el conector personalizado.

Abra un explorador y vaya al [centro de administración de Azure Active Directory](https://aad.portal.azure.com). Elija el vínculo de **Azure Active Directory** en el menú de navegación de la izquierda y, después, elija la entrada **registros de aplicaciones** en la sección **administrar** de la hoja **Azure Active Directory** .

![Captura de pantalla de la hoja de Azure Active Directory en el centro de administración de Azure Active Directory](./images/app-reg-preview1.png)

Elija el elemento de menú **registro nuevo** en la parte superior de la hoja **registros de aplicaciones** .

![Captura de pantalla de la hoja registros de aplicaciones en el centro de administración de Azure Active Directory](./images/app-reg-preview2.png)

Escriba `MS Graph Batch App` en el campo **nombre** . En la sección **tipos de cuenta admitidos** , seleccione **cuentas en cualquier directorio de la organización**. Deje en blanco la sección **URI** de redireccionamiento y elija **registrar**.

![Captura de pantalla de la hoja de registro de aplicaciones en el centro de administración de Azure Active Directory](./images/app-reg-preview3.png)

En la hoja **aplicación para lotes de MS Graph** , copie el identificador de la **aplicación (cliente)**. Lo necesitará en el siguiente ejercicio.

![Captura de pantalla de la página de aplicación registrada](./images/app-reg-preview4.png)

Elija la entrada **permisos de API** en la sección **administrar** de la hoja **aplicación por lotes de MS Graph** . Elija **Agregar un permiso** en **permisos**de la API.

![Captura de pantalla de la hoja de permisos de la API](./images/app-perms-preview1.png)

En la hoja **solicitar permisos de API** , elija **Microsoft Graph**y, a continuación, elija **permisos**delegados. Busque y `group`, a continuación, seleccione el permiso delegados **leer y escribir en todos los grupos** . Elija **Agregar permisos** en la parte inferior de la hoja.

 ![Captura de pantalla de la hoja de permisos de la API de solicitud](./images/app-perms-preview2.png)

Elija la entrada **certificados y secretos** en la sección **administrar** de la hoja de la **aplicación batch de MS Graph** y, a continuación, elija **nuevo secreto de cliente**. Escriba `forever` en la **Descripción** y seleccione **nunca** en **Expires**. Seleccione **Agregar**.

![Captura de pantalla del módulo de certificados y secretos](./images/app-key-preview1.png)

Copie el valor clave de la nueva clave. Lo necesitará en el siguiente ejercicio.

![Captura de pantalla del nuevo secreto de cliente](./images/app-key-preview2.png)

> [!IMPORTANT]
> Este paso es crítico ya que no se podrá acceder a la clave una vez que cierre esta hoja. Guarde esta clave en un editor de texto para usarla en los ejercicios venideros.

Para habilitar la administración de servicios adicionales a los que se puede tener acceso a través de Microsoft Graph, incluidas las propiedades de Team, debe seleccionar ámbitos apropiados adicionales para habilitar la administración de servicios específicos. Por ejemplo, para ampliar nuestra solución para habilitar la creación de blocs de notas de OneNote o los planes de planeación, las tareas que necesitaría agregar los ámbitos de permisos necesarios para las API relevantes.