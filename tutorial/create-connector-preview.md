<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="10472-101">En este ejercicio, creará un nuevo conector personalizado que se puede usar en flujo o en aplicaciones lógicas de Azure.</span><span class="sxs-lookup"><span data-stu-id="10472-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="10472-102">El archivo de definición de la API abierta se crea previamente con la ruta de acceso `$batch` correcta para el punto de conexión de Microsoft Graph y la configuración adicional para habilitar la importación simple.</span><span class="sxs-lookup"><span data-stu-id="10472-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="10472-103">Con un editor de texto, cree un nuevo archivo vacío `MSGraph-Delegate-Batch.swagger.json` denominado y agregue el siguiente código.</span><span class="sxs-lookup"><span data-stu-id="10472-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="10472-104">Abra un explorador y vaya a [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="10472-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="10472-105">Inicie sesión con su cuenta de administrador de inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="10472-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="10472-106">Elija el icono de engranaje en la esquina superior derecha y seleccione el elemento **conectores personalizados** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="10472-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Captura de pantalla del menú desplegable de Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="10472-108">En la página **conectores personalizados** , elija el vínculo **crear conector personalizado** en la parte superior derecha y, a continuación, seleccione el elemento **importar un archivo de la API abierta** en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="10472-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Captura de pantalla del menú desplegable crear conector personalizado en Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="10472-110">Escriba `MS Graph Batch Connector` en el cuadro de texto **nombre del conector personalizado** .</span><span class="sxs-lookup"><span data-stu-id="10472-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="10472-111">Elija el icono de carpeta para cargar el archivo de la API abierta.</span><span class="sxs-lookup"><span data-stu-id="10472-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="10472-112">Busque el `MSGraph-Delegate-Batch.swagger.json` archivo que ha creado.</span><span class="sxs-lookup"><span data-stu-id="10472-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="10472-113">Elija **continuar** para cargar el archivo de la API abierta.</span><span class="sxs-lookup"><span data-stu-id="10472-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Captura de pantalla del cuadro de diálogo crear conector personalizado](./images/flow-conn3.png)

<span data-ttu-id="10472-115">En la página Configuración del conector, elija el vínculo **seguridad** en el menú de navegación.</span><span class="sxs-lookup"><span data-stu-id="10472-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="10472-116">ReLlene los campos como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="10472-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="10472-117">**Elija qué autenticación implementa la API**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="10472-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="10472-118">**Proveedor de identidad**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="10472-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="10472-119">**Identificador de cliente**: identificador de la aplicación que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="10472-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="10472-120">**Secreto de cliente**: la clave que creó en el ejercicio anterior</span><span class="sxs-lookup"><span data-stu-id="10472-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="10472-121">**Dirección URL de inicio de sesión**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="10472-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="10472-122">**Identificador de inquilino**:`common`</span><span class="sxs-lookup"><span data-stu-id="10472-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="10472-123">**Dirección URL**del `https://graph.microsoft.com` recurso: (sin finalización/)</span><span class="sxs-lookup"><span data-stu-id="10472-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="10472-124">**Ámbito**: dejar en blanco</span><span class="sxs-lookup"><span data-stu-id="10472-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="10472-125">Elija **crear conector** en la parte superior derecha</span><span class="sxs-lookup"><span data-stu-id="10472-125">Choose **Create Connector** on the top-right</span></span>

![Captura de pantalla de la pestaña seguridad en la configuración del conector](./images/flow-conn4.png)

<span data-ttu-id="10472-127">Una vez creado el conector, copie la **dirección URL**de redireccionamiento generada.</span><span class="sxs-lookup"><span data-stu-id="10472-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Captura de pantalla de la dirección URL de redireccionamiento generada](./images/flow-conn5.png)

<span data-ttu-id="10472-129">Vuelva a la aplicación registrada en el [portal de Azure](https://aad.portal.azure.com) que creó en el ejercicio anterior.</span><span class="sxs-lookup"><span data-stu-id="10472-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="10472-130">Seleccione **información general** en la hoja **aplicación para lotes de MS Graph** y, a continuación, seleccione **Agregar un URI**de redireccionamiento.</span><span class="sxs-lookup"><span data-stu-id="10472-130">Select **Overview** on the **MS Graph Batch App** blade, then select **Add a Redirect URI**.</span></span> <span data-ttu-id="10472-131">Agregue la **URL** de redireccionamiento que ha copiado en el campo **URI** de redireccionamiento y elija **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="10472-131">Add the **Redirect URL** you copied in the **Redirect URI** field and choose **Save**.</span></span>

![Captura de pantalla de la hoja direcciones URL de respuesta en Azure portal](./images/flow-conn-preview6.png)