<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="dd90d-101">El flujo que ha creado en el ejercicio anterior usa `$batch` la API para realizar dos solicitudes individuales a Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="dd90d-101">The Flow you created in the previous exercise uses the `$batch` API to make two individual requests to the Microsoft Graph.</span></span> <span data-ttu-id="dd90d-102">La llamada `$batch` al punto de conexión de esta forma proporciona alguna ventaja y flexibilidad, pero la `$batch` verdadera potencia del punto de conexión viene cuando ejecuta varias solicitudes a Microsoft `$batch` Graph en una sola llamada.</span><span class="sxs-lookup"><span data-stu-id="dd90d-102">Calling the `$batch` endpoint this way provides some benefit and flexibility, but the true power of the `$batch` endpoint comes when executing multiple requests to Microsoft Graph in a single `$batch` call.</span></span> <span data-ttu-id="dd90d-103">En este ejercicio, ampliará el ejemplo de creación de un grupo unificado y asociando un equipo para incluir la creación de varios canales predeterminados para `$batch` el equipo en una sola solicitud.</span><span class="sxs-lookup"><span data-stu-id="dd90d-103">In this exercise, you will extend the example of creating a Unified Group and associating a Team to include creating multiple default Channels for the Team in a single `$batch` request.</span></span>

<span data-ttu-id="dd90d-104">Abra [Microsoft Flow](https://flow.microsoft.com) en el explorador e inicie sesión con su cuenta de administrador de inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="dd90d-104">Open [Microsoft Flow](https://flow.microsoft.com) in your browser and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="dd90d-105">Seleccione el flujo que creó en el paso anterior y elija **Editar**.</span><span class="sxs-lookup"><span data-stu-id="dd90d-105">Select the Flow you created in the previous step and choose **Edit**.</span></span>

<span data-ttu-id="dd90d-106">Elija **nuevo paso** y escriba `Batch` en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="dd90d-106">Choose **New step** and type `Batch` in the search box.</span></span> <span data-ttu-id="dd90d-107">Agregue la acción **conector por lotes de MS Graph** .</span><span class="sxs-lookup"><span data-stu-id="dd90d-107">Add the **MS Graph Batch Connector** action.</span></span> <span data-ttu-id="dd90d-108">Elija los puntos suspensivos y cambie el nombre de `Batch POST-channels`esta acción a.</span><span class="sxs-lookup"><span data-stu-id="dd90d-108">Choose the ellipsis and rename this action to `Batch POST-channels`.</span></span>

<span data-ttu-id="dd90d-109">Agregue el código siguiente en el cuadro de texto **Body** de la acción.</span><span class="sxs-lookup"><span data-stu-id="dd90d-109">Add the following code into the **body** text box of the action.</span></span>

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

<span data-ttu-id="dd90d-110">Observe que las tres solicitudes anteriores usan la propiedad [DEPENDSON](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) para especificar un orden secuencial, y cada una de ellas ejecutará una solicitud post para crear un nuevo canal en el nuevo equipo.</span><span class="sxs-lookup"><span data-stu-id="dd90d-110">Notice the three requests above are using the [dependsOn](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) property to specify a sequence order, and each will execute a POST request to create a new channel in the new Team.</span></span>

<span data-ttu-id="dd90d-111">Seleccione cada instancia del `REPLACE` marcador de posición y, a continuación, seleccione **expresión** en el panel de contenido dinámico.</span><span class="sxs-lookup"><span data-stu-id="dd90d-111">Select each instance of the `REPLACE` placeholder, then select **Expression** in the dynamic content pane.</span></span> <span data-ttu-id="dd90d-112">Agregue la fórmula siguiente a la **expresión**.</span><span class="sxs-lookup"><span data-stu-id="dd90d-112">Add the following formula into the **Expression**.</span></span>

```js
body('Batch_PUT-team').responses[0].body.id
```

![Captura de pantalla de la expresión en el panel de contenido dinámico](./images/flow-channel1.png)

<span data-ttu-id="dd90d-114">Elija **Guardar**y, a continuación, elija **prueba** para ejecutar el flujo.</span><span class="sxs-lookup"><span data-stu-id="dd90d-114">Choose **Save**, then choose **Test** to execute the Flow.</span></span> <span data-ttu-id="dd90d-115">Seleccione el botón de opción **voy a realizar la** acción desencadenadora y, a continuación, elija **Guardar prueba de &**.</span><span class="sxs-lookup"><span data-stu-id="dd90d-115">Select the **I'll perform the trigger** action radio button, then choose **Save & Test**.</span></span> <span data-ttu-id="dd90d-116">Escriba un nombre de grupo único en el campo **nombre** sin espacios y elija **Ejecutar flujo** para ejecutar el flujo.</span><span class="sxs-lookup"><span data-stu-id="dd90d-116">Enter a unique group name in the **Name** field without spaces, and choose **Run flow** to execute the Flow.</span></span>

![Captura de pantalla del cuadro de diálogo flujo de ejecución](./images/flow-channel3.png)

<span data-ttu-id="dd90d-118">Una vez que se inicie el flujo, seleccione el vínculo **ver actividad de ejecución de flujo** y, a continuación, elija el flujo de ejecución para ver el registro de actividades.</span><span class="sxs-lookup"><span data-stu-id="dd90d-118">Once the Flow starts, choose the **See flow run activity** link, then choose the running Flow to see the activity log.</span></span>

<span data-ttu-id="dd90d-119">Una vez finalizado el flujo, el resultado final de `Batch POST-channels` la acción tiene una respuesta de Estado HTTP de 201 para cada canal creado.</span><span class="sxs-lookup"><span data-stu-id="dd90d-119">When the Flow completes, the final output for the `Batch POST-channels` action has a 201 HTTP Status response for each Channel created.</span></span>

![Captura de pantalla del registro de la actividad de flujo correcta](./images/flow-channel2.png)

<span data-ttu-id="dd90d-121">Vaya a [Microsoft Teams](https://teams.microsoft.com) e inicie sesión con su cuenta de administrador de inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="dd90d-121">Browse to [Microsoft Teams](https://teams.microsoft.com) and sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="dd90d-122">Compruebe que el equipo que acaba de crear aparece e incluye los tres canales creados por `$batch` la solicitud.</span><span class="sxs-lookup"><span data-stu-id="dd90d-122">Verify that the team you just created appears and includes the three channels created by the `$batch` request.</span></span>

![Captura de pantalla de la aplicación Teams con el nuevo equipo y los canales que se muestran](./images/team-channels.png)

<span data-ttu-id="dd90d-124">Aunque la acción `Batch POST-channels` anterior se implementó en este tutorial como una acción independiente, las llamadas para crear los canales podrían haberse agregado como llamadas adicionales en la `Batch PUT-team` acción.</span><span class="sxs-lookup"><span data-stu-id="dd90d-124">While the above `Batch POST-channels` action was implemented in this tutorial as a separate action, the calls to create the channels could have been added as additional calls in the `Batch PUT-team` action.</span></span> <span data-ttu-id="dd90d-125">Esto habría creado el equipo y todos los canales en una sola llamada por lotes.</span><span class="sxs-lookup"><span data-stu-id="dd90d-125">This would have created the Team and all Channels in a single batch call.</span></span> <span data-ttu-id="dd90d-126">Pruebe el propio.</span><span class="sxs-lookup"><span data-stu-id="dd90d-126">Give that a try on your own.</span></span>

<span data-ttu-id="dd90d-127">Por último, recuerde que las llamadas de [procesamiento por lotes JSON](https://docs.microsoft.com/graph/json-batching) devolverán un código de estado http para cada solicitud.</span><span class="sxs-lookup"><span data-stu-id="dd90d-127">Finally, remember that [JSON Batching](https://docs.microsoft.com/graph/json-batching) calls will return an HTTP status code for each request.</span></span> <span data-ttu-id="dd90d-128">En un proceso de producción, es posible que desee combinar el posprocesamiento de los resultados [`Apply to each`](https://docs.microsoft.com/flow/apply-to-each) con una acción y validar cada respuesta individual que tenga un código de estado de 201 o compensar otros códigos de estado recibidos.</span><span class="sxs-lookup"><span data-stu-id="dd90d-128">In a production process, you may want to combine post processing of the results with an [`Apply to each`](https://docs.microsoft.com/flow/apply-to-each) action and validate each individual response has a 201 status code or compensate for any other status codes received.</span></span>