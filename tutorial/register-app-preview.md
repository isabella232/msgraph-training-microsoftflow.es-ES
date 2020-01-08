<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="b98d5-101">En este ejercicio, creará una nueva aplicación de Azure Active Directory que se usará para proporcionar los permisos delegados para el conector personalizado.</span><span class="sxs-lookup"><span data-stu-id="b98d5-101">In this exercise, you will create a new Azure Active Directory Application which will be used to provide the delegated permissions for the custom connector.</span></span>

<span data-ttu-id="b98d5-102">Abra un explorador y vaya al [centro de administración de Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b98d5-102">Open a browser and navigate to [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="b98d5-103">Elija el vínculo de **Azure Active Directory** en el menú de navegación de la izquierda y, después, elija la entrada **registros de aplicaciones** en la sección **administrar** de la hoja **Azure Active Directory** .</span><span class="sxs-lookup"><span data-stu-id="b98d5-103">Choose the **Azure Active Directory** link in the left navigation menu, then choose the **App registrations** entry in the **Manage** section of the **Azure Active Directory** blade.</span></span>

![Captura de pantalla de la hoja de Azure Active Directory en el centro de administración de Azure Active Directory](./images/app-reg-preview1.png)

<span data-ttu-id="b98d5-105">Elija el elemento de menú **registro nuevo** en la parte superior de la hoja **registros de aplicaciones** .</span><span class="sxs-lookup"><span data-stu-id="b98d5-105">Choose the **New registration** menu item at the top of the **App Registrations** blade.</span></span>

![Captura de pantalla de la hoja registros de aplicaciones en el centro de administración de Azure Active Directory](./images/app-reg-preview2.png)

<span data-ttu-id="b98d5-107">Escriba `MS Graph Batch App` en el campo **nombre** .</span><span class="sxs-lookup"><span data-stu-id="b98d5-107">Enter `MS Graph Batch App` in the **Name** field.</span></span> <span data-ttu-id="b98d5-108">En la sección **tipos de cuenta admitidos** , seleccione **cuentas en cualquier directorio de la organización**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-108">In the **Supported account types** section, select **Accounts in any organizational directory**.</span></span> <span data-ttu-id="b98d5-109">Deje en blanco la sección **URI de redireccionamiento** y elija **registrar**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-109">Leave the **Redirect URI** section blank and choose **Register**.</span></span>

![Captura de pantalla de la hoja de registro de aplicaciones en el centro de administración de Azure Active Directory](./images/app-reg-preview3.png)

<span data-ttu-id="b98d5-111">En la hoja **aplicación para lotes de MS Graph** , copie el identificador de la **aplicación (cliente)**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-111">On the **MS Graph Batch App** blade, copy the **Application (client) ID**.</span></span> <span data-ttu-id="b98d5-112">Lo necesitará en el siguiente ejercicio.</span><span class="sxs-lookup"><span data-stu-id="b98d5-112">You'll need this in the next exercise.</span></span>

![Captura de pantalla de la página de aplicación registrada](./images/app-reg-preview4.png)

<span data-ttu-id="b98d5-114">Elija la entrada **permisos de API** en la sección **administrar** de la hoja **aplicación por lotes de MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="b98d5-114">Choose the **API permissions** entry in the **Manage** section of the **MS Graph Batch App** blade.</span></span> <span data-ttu-id="b98d5-115">Elija **Agregar un permiso** en **permisos**de la API.</span><span class="sxs-lookup"><span data-stu-id="b98d5-115">Choose **Add a permission** under **API permissions**.</span></span>

![Captura de pantalla de la hoja de permisos de la API](./images/app-perms-preview1.png)

<span data-ttu-id="b98d5-117">En la hoja **solicitar permisos de API** , elija **Microsoft Graph**y, a continuación, elija **permisos delegados**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-117">In the **Request API permissions** blade, choose the **Microsoft Graph**, then choose **Delegated permissions**.</span></span> <span data-ttu-id="b98d5-118">Busque y `group`, a continuación, seleccione el permiso delegados **leer y escribir en todos los grupos** .</span><span class="sxs-lookup"><span data-stu-id="b98d5-118">Search for `group`, then select the **Read and write all groups** delegated permission.</span></span> <span data-ttu-id="b98d5-119">Elija **Agregar permisos** en la parte inferior de la hoja.</span><span class="sxs-lookup"><span data-stu-id="b98d5-119">Choose **Add permissions** at the bottom of the blade.</span></span>

 ![Captura de pantalla de la hoja de permisos de la API de solicitud](./images/app-perms-preview2.png)

<span data-ttu-id="b98d5-121">Elija la entrada **certificados y secretos** en la sección **administrar** de la hoja de la **aplicación batch de MS Graph** y, a continuación, elija **nuevo secreto de cliente**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-121">Choose the **Certificates and secrets** entry in the **Manage** section of the **MS Graph Batch App** blade, then choose **New client secret**.</span></span> <span data-ttu-id="b98d5-122">Escriba `forever` en la **Descripción** y seleccione **nunca** en **Expires**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-122">Enter `forever` in the **Description** and select **Never** under **Expires**.</span></span> <span data-ttu-id="b98d5-123">Seleccione **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="b98d5-123">Choose **Add**.</span></span>

![Captura de pantalla del módulo de certificados y secretos](./images/app-key-preview1.png)

<span data-ttu-id="b98d5-125">Copie el valor clave de la nueva clave.</span><span class="sxs-lookup"><span data-stu-id="b98d5-125">Copy the key value for the new key.</span></span> <span data-ttu-id="b98d5-126">Lo necesitará en el siguiente ejercicio.</span><span class="sxs-lookup"><span data-stu-id="b98d5-126">You'll need this in the next exercise.</span></span>

![Captura de pantalla del nuevo secreto de cliente](./images/app-key-preview2.png)

> [!IMPORTANT]
> <span data-ttu-id="b98d5-128">Este paso es crítico ya que no se podrá acceder a la clave una vez que cierre esta hoja.</span><span class="sxs-lookup"><span data-stu-id="b98d5-128">This step is critical as the key will not be accessible once you close this blade.</span></span> <span data-ttu-id="b98d5-129">Guarde esta clave en un editor de texto para usarla en los ejercicios venideros.</span><span class="sxs-lookup"><span data-stu-id="b98d5-129">Save this key to a text editor for use in upcoming exercises.</span></span>

<span data-ttu-id="b98d5-130">Para habilitar la administración de servicios adicionales a los que se puede tener acceso a través de Microsoft Graph, incluidas las propiedades de Team, debe seleccionar ámbitos apropiados adicionales para habilitar la administración de servicios específicos.</span><span class="sxs-lookup"><span data-stu-id="b98d5-130">To enable management of additional services accessible via the Microsoft Graph, including Teams properties, you would need to select additional, appropriate scopes to enable managing specific services.</span></span> <span data-ttu-id="b98d5-131">Por ejemplo, para ampliar nuestra solución para habilitar la creación de blocs de notas de OneNote o los planes de planeación, las tareas que necesitaría agregar los ámbitos de permisos necesarios para las API relevantes.</span><span class="sxs-lookup"><span data-stu-id="b98d5-131">For example, to extend our solution to enable creating OneNote Notebooks or Planner plans, buckets and tasks you would need to add the required permission scopes for the relevant APIs.</span></span>
