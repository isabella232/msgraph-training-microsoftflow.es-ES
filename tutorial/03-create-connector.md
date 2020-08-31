<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="aa479-101">En este ejercicio, creará un nuevo conector personalizado que se puede usar en Microsoft Power Automate o en las aplicaciones lógicas de Azure.</span><span class="sxs-lookup"><span data-stu-id="aa479-101">In this exercise, you will create a new custom connector which can be used in Microsoft Power Automate or in Azure Logic Apps.</span></span> <span data-ttu-id="aa479-102">El archivo de definición de OpenAPI está precompilado con la ruta de acceso correcta para el punto de conexión de Microsoft Graph `$batch` y la configuración adicional para habilitar la importación simple.</span><span class="sxs-lookup"><span data-stu-id="aa479-102">The OpenAPI definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="aa479-103">Hay dos opciones para crear un conector personalizado para Microsoft Graph:</span><span class="sxs-lookup"><span data-stu-id="aa479-103">There are two options to create a custom connector for Microsoft Graph:</span></span>

- <span data-ttu-id="aa479-104">Crear a partir de blanco</span><span class="sxs-lookup"><span data-stu-id="aa479-104">Create from blank</span></span>
- <span data-ttu-id="aa479-105">Importar un archivo OpenAPI</span><span class="sxs-lookup"><span data-stu-id="aa479-105">Import an OpenAPI file</span></span>

## <a name="option-1-create-custom-connector-from-blank-template"></a><span data-ttu-id="aa479-106">Opción 1: crear un conector personalizado a partir de una plantilla en blanco</span><span class="sxs-lookup"><span data-stu-id="aa479-106">Option 1: Create custom connector from blank template</span></span>

<span data-ttu-id="aa479-107">Abra un explorador y navegue a [Microsoft Power Automate](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="aa479-107">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="aa479-108">Inicie sesión con su cuenta de administrador de inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="aa479-108">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="aa479-109">Elija **datos** en el menú de la parte izquierda y seleccione el elemento **conectores personalizados** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="aa479-109">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Captura de pantalla del menú desplegable de Microsoft Power automatizado](./images/custom-connectors.png)

<span data-ttu-id="aa479-111">En la página **conectores personalizados** , elija el vínculo **nuevo conector personalizado** en la parte superior derecha y, a continuación, seleccione el elemento **crear desde en blanco** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="aa479-111">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Create from blank** item in the drop-down menu.</span></span>

![Captura de pantalla del nuevo menú desplegable de conectores personalizados en Microsoft Power automatization](./images/new-connector.png)

<span data-ttu-id="aa479-113">Escriba `MS Graph Batch Connector` en el cuadro de texto **nombre del conector** .</span><span class="sxs-lookup"><span data-stu-id="aa479-113">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="aa479-114">Choose **Continue**.</span><span class="sxs-lookup"><span data-stu-id="aa479-114">Choose **Continue**.</span></span>

<span data-ttu-id="aa479-115">En la página configuración **General** del conector, rellene los campos como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="aa479-115">On the connector configuration **General** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="aa479-116">**Esquema**: https</span><span class="sxs-lookup"><span data-stu-id="aa479-116">**Scheme**: HTTPS</span></span>
- <span data-ttu-id="aa479-117">**Host**: `graph.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="aa479-117">**Host**: `graph.microsoft.com`</span></span>
- <span data-ttu-id="aa479-118">**Dirección URL base**: `/`</span><span class="sxs-lookup"><span data-stu-id="aa479-118">**Base URL**: `/`</span></span>

<span data-ttu-id="aa479-119">Elija el botón **seguridad** para continuar.</span><span class="sxs-lookup"><span data-stu-id="aa479-119">Choose **Security** button to continue.</span></span>

![Captura de pantalla de la pestaña General en la configuración del conector](./images/general-tab.png)

<span data-ttu-id="aa479-121">En la página **seguridad** , rellene los campos como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="aa479-121">On the **Security** page, fill in the fields as follows.</span></span>

- <span data-ttu-id="aa479-122">**Elija qué autenticación implementa la API**: `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="aa479-122">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="aa479-123">**Proveedor de identidad**: `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="aa479-123">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="aa479-124">**Identificador de cliente**: identificador de la aplicación que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="aa479-124">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="aa479-125">**Secreto de cliente**: la clave que creó en el ejercicio anterior</span><span class="sxs-lookup"><span data-stu-id="aa479-125">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="aa479-126">**Dirección URL de inicio de sesión**: `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="aa479-126">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="aa479-127">**Identificador de inquilino**: `common`</span><span class="sxs-lookup"><span data-stu-id="aa479-127">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="aa479-128">**Dirección URL del recurso**: `https://graph.microsoft.com` (sin finalización/)</span><span class="sxs-lookup"><span data-stu-id="aa479-128">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="aa479-129">**Ámbito**: dejar en blanco</span><span class="sxs-lookup"><span data-stu-id="aa479-129">**Scope**: Leave blank</span></span>

<span data-ttu-id="aa479-130">Elija el botón **definición** para continuar.</span><span class="sxs-lookup"><span data-stu-id="aa479-130">Choose **Definition** button to continue.</span></span>

![Captura de pantalla de la pestaña seguridad en la configuración del conector](./images/security-tab.png)

<span data-ttu-id="aa479-132">En la página **definición** , seleccione **nueva acción** y rellene los campos de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="aa479-132">On the **Definition** page, select **New Action** and fill in the fields as follows.</span></span>

- <span data-ttu-id="aa479-133">**Resumen**: `Batch`</span><span class="sxs-lookup"><span data-stu-id="aa479-133">**Summary**: `Batch`</span></span>
- <span data-ttu-id="aa479-134">**Descripción**: `Execute Batch with Delegate Permission`</span><span class="sxs-lookup"><span data-stu-id="aa479-134">**Description**: `Execute Batch with Delegate Permission`</span></span>
- <span data-ttu-id="aa479-135">**Identificador de operación**: `Batch`</span><span class="sxs-lookup"><span data-stu-id="aa479-135">**Operation ID**: `Batch`</span></span>
- <span data-ttu-id="aa479-136">**Visibilidad**: `important`</span><span class="sxs-lookup"><span data-stu-id="aa479-136">**Visibility**: `important`</span></span>

![Captura de pantalla de la pestaña definición en la configuración del conector](./images/definition-tab.png)

<span data-ttu-id="aa479-138">Para crear una **solicitud** , seleccione **Importar desde ejemplo** y rellene los campos como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="aa479-138">Create **Request** by selecting **Import from Sample** and fill in the fields as follows.</span></span>

- <span data-ttu-id="aa479-139">**Verbo**: `POST`</span><span class="sxs-lookup"><span data-stu-id="aa479-139">**Verb**: `POST`</span></span>
- <span data-ttu-id="aa479-140">**URL**: `https://graph.microsoft.com/v1.0/$batch`</span><span class="sxs-lookup"><span data-stu-id="aa479-140">**URL**: `https://graph.microsoft.com/v1.0/$batch`</span></span>
- <span data-ttu-id="aa479-141">**Encabezados**: dejar en blanco</span><span class="sxs-lookup"><span data-stu-id="aa479-141">**Headers**: Leave blank</span></span>
- <span data-ttu-id="aa479-142">**Cuerpo**: `{}`</span><span class="sxs-lookup"><span data-stu-id="aa479-142">**Body**: `{}`</span></span>

<span data-ttu-id="aa479-143">Seleccione **Importar**.</span><span class="sxs-lookup"><span data-stu-id="aa479-143">Select **Import**.</span></span>

![Captura de pantalla del cuadro de diálogo Importar desde ejemplo en la configuración del conector](./images/import-sample.png)

<span data-ttu-id="aa479-145">Elija **crear conector** en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="aa479-145">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="aa479-146">Una vez creado el conector, copie la **dirección URL de redireccionamiento** generada desde la página **seguridad** .</span><span class="sxs-lookup"><span data-stu-id="aa479-146">After the connector has been created, copy the generated **Redirect URL** from **Security** page.</span></span>

![Captura de pantalla de la dirección URL de redireccionamiento generada](./images/redirect-url.png)

<span data-ttu-id="aa479-148">Vuelva a la aplicación registrada en el [portal de Azure](https://aad.portal.azure.com) que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="aa479-148">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="aa479-149">Seleccione **autenticación** en el menú de la parte izquierda.</span><span class="sxs-lookup"><span data-stu-id="aa479-149">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="aa479-150">Seleccione **Agregar una plataforma**y, a continuación, seleccione **Web**.</span><span class="sxs-lookup"><span data-stu-id="aa479-150">Select **Add a platform**, then select **Web**.</span></span> <span data-ttu-id="aa479-151">Escriba la dirección URL de redireccionamiento copiada del paso anterior en los **URI de redireccionamiento**y, después, seleccione **configurar**.</span><span class="sxs-lookup"><span data-stu-id="aa479-151">Enter the redirect URL copied from the previous step in the **Redirect URIs**, then select **Configure**.</span></span>

![Captura de pantalla de la hoja direcciones URL de respuesta en Azure portal](./images/update-app-reg.png)

## <a name="option-2-create-custom-connector-by-importing-openapi-file"></a><span data-ttu-id="aa479-153">Opción 2: crear un conector personalizado mediante la importación del archivo OpenAPI</span><span class="sxs-lookup"><span data-stu-id="aa479-153">Option 2: Create custom connector by importing OpenAPI file</span></span>

<span data-ttu-id="aa479-154">Con un editor de texto, cree un nuevo archivo vacío denominado `MSGraph-Delegate-Batch.swagger.json` y agregue el siguiente código.</span><span class="sxs-lookup"><span data-stu-id="aa479-154">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="aa479-155">Abra un explorador y navegue a [Microsoft Power Automate](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="aa479-155">Open a browser and navigate to [Microsoft Power Automate](https://flow.microsoft.com).</span></span> <span data-ttu-id="aa479-156">Inicie sesión con su cuenta de administrador de inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="aa479-156">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="aa479-157">Elija **datos** en el menú de la parte izquierda y seleccione el elemento **conectores personalizados** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="aa479-157">Choose **Data** on the left-hand side menu, and select the **Custom Connectors** item in the drop-down menu.</span></span>

<span data-ttu-id="aa479-158">En la página **conectores personalizados** , elija el vínculo **nuevo conector personalizado** en la parte superior derecha y, a continuación, seleccione el elemento **importar un archivo de OpenAPI** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="aa479-158">On the **Custom Connectors** page choose the **New custom connector** link in the top right, then select the **Import an OpenAPI file** item in the drop-down menu.</span></span>

<span data-ttu-id="aa479-159">Escriba `MS Graph Batch Connector` en el cuadro de texto **nombre del conector** .</span><span class="sxs-lookup"><span data-stu-id="aa479-159">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="aa479-160">Elija el icono de carpeta para cargar el archivo OpenAPI.</span><span class="sxs-lookup"><span data-stu-id="aa479-160">Choose the folder icon to upload the OpenAPI file.</span></span> <span data-ttu-id="aa479-161">Busque el `MSGraph-Delegate-Batch.swagger.json` archivo que ha creado.</span><span class="sxs-lookup"><span data-stu-id="aa479-161">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="aa479-162">Elija **continuar** para cargar el archivo OpenAPI.</span><span class="sxs-lookup"><span data-stu-id="aa479-162">Choose **Continue** to upload the OpenAPI file.</span></span>

<span data-ttu-id="aa479-163">En la página Configuración del conector, elija el vínculo **seguridad** en el menú de navegación.</span><span class="sxs-lookup"><span data-stu-id="aa479-163">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="aa479-164">Rellene los campos como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="aa479-164">Fill in the fields as follows.</span></span>

- <span data-ttu-id="aa479-165">**Elija qué autenticación implementa la API**: `OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="aa479-165">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="aa479-166">**Proveedor de identidad**: `Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="aa479-166">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="aa479-167">**Identificador de cliente**: identificador de la aplicación que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="aa479-167">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="aa479-168">**Secreto de cliente**: la clave que creó en el ejercicio anterior</span><span class="sxs-lookup"><span data-stu-id="aa479-168">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="aa479-169">**Dirección URL de inicio de sesión**: `https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="aa479-169">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="aa479-170">**Identificador de inquilino**: `common`</span><span class="sxs-lookup"><span data-stu-id="aa479-170">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="aa479-171">**Dirección URL del recurso**: `https://graph.microsoft.com` (sin finalización/)</span><span class="sxs-lookup"><span data-stu-id="aa479-171">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="aa479-172">**Ámbito**: dejar en blanco</span><span class="sxs-lookup"><span data-stu-id="aa479-172">**Scope**: Leave blank</span></span>

<span data-ttu-id="aa479-173">Elija **crear conector** en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="aa479-173">Choose **Create Connector** on the top-right.</span></span> <span data-ttu-id="aa479-174">Una vez creado el conector, copie la **dirección URL de redireccionamiento**generada.</span><span class="sxs-lookup"><span data-stu-id="aa479-174">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Captura de pantalla de la dirección URL de redireccionamiento generada](./images/redirect-url.png)

<span data-ttu-id="aa479-176">Vuelva a la aplicación registrada en el [portal de Azure](https://aad.portal.azure.com) que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="aa479-176">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="aa479-177">Seleccione **autenticación** en el menú de la parte izquierda.</span><span class="sxs-lookup"><span data-stu-id="aa479-177">Select **Authentication** on the left-hand side menu.</span></span> <span data-ttu-id="aa479-178">Seleccione **Agregar una plataforma**y, a continuación, seleccione **Web**.</span><span class="sxs-lookup"><span data-stu-id="aa479-178">Select **Add a platform**, then select **Web**.</span></span> <span data-ttu-id="aa479-179">Escriba la dirección URL de redireccionamiento copiada del paso anterior en los **URI de redireccionamiento**y, después, seleccione **configurar**.</span><span class="sxs-lookup"><span data-stu-id="aa479-179">Enter the redirect URL copied from the previous step in the **Redirect URIs**, then select **Configure**.</span></span>

![Captura de pantalla de la hoja direcciones URL de respuesta en Azure portal](./images/update-app-reg.png)