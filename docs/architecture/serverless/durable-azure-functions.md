---
title: Dayanıklı Azure işlevleri-sunucusuz uygulamalar
description: Sürekli Azure işlevleri, koddaki durum bilgisi olan iş akışlarını etkinleştirmek için Azure Işlevleri çalışma zamanını genişletir.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522853"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="1728f-103">Dayanıklı Azure işlevleri</span><span class="sxs-lookup"><span data-stu-id="1728f-103">Durable Azure functions</span></span>

<span data-ttu-id="1728f-104">Azure Işlevleri ile sunucusuz uygulamalar oluştururken, işlemleriniz genellikle durum bilgisiz bir şekilde çalışacak şekilde tasarlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="1728f-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="1728f-105">Bu tasarım seçeneğinin nedeni, platformun ölçeklendirilirken, kodun hangi sunuculara çalıştığını anlamak zor hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1728f-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="1728f-106">Ayrıca, belirli bir noktada kaç örnek etkin olduğunu anlamak zor olur.</span><span class="sxs-lookup"><span data-stu-id="1728f-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="1728f-107">Ancak, bir işlemin geçerli durumunun bilinmesini gerektiren uygulama sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="1728f-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="1728f-108">Çevrimiçi mağazaya sipariş gönderme sürecini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1728f-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="1728f-109">Kullanıma alma işlemi, işlemin durumunu bilmemiz gereken birden çok işlemden oluşan bir iş akışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="1728f-110">Bu tür bilgiler, müşterinin hesabında krediler varsa ve aynı zamanda kredi kartını işleme sonuçları varsa ürün envanterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="1728f-111">Bu işlemler kendi iç iş akışlarına veya hatta üçüncü taraf sistemlerden gelen hizmetlere kolayca sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="1728f-112">Günümüzde, iç ve dış sistemler arasında uygulama durumunun koordinasyonuna yardımcı olacak çeşitli desenler vardır.</span><span class="sxs-lookup"><span data-stu-id="1728f-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="1728f-113">Bu durumu yönetmek için merkezi sıraya alma sistemleri, dağıtılmış anahtar-değer depoları veya paylaşılan veritabanları kullanan çözümler arasında gelmesi yaygındır.</span><span class="sxs-lookup"><span data-stu-id="1728f-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="1728f-114">Ancak, bunlar artık sağlanması ve yönetilmesi gereken tüm ek kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="1728f-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="1728f-115">Sunucusuz bir ortamda, kodunuz bu kaynaklarla el ile koordine edilmeye çalışırken çok daha fazla hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="1728f-116">Azure Işlevleri Dayanıklı İşlevler olarak adlandırılan durum bilgisi olan işlevleri oluşturmaya yönelik bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="1728f-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="1728f-117">Dayanıklı İşlevler, koddaki durum bilgisi olan iş akışlarının tanımını sağlayan Azure Işlevleri çalışma zamanının uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="1728f-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="1728f-118">İş akışlarını etkinliklere bölmek için Dayanıklı İşlevler uzantısı durumu yönetebilir, ilerleme kontrol noktaları oluşturabilir ve sunucular arasında işlev çağrılarının dağıtımını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="1728f-119">Arka planda, yürütme geçmişini kalıcı hale getirmek, etkinlik işlevlerini zamanlamak ve yanıtları almak için bir Azure depolama hesabı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1728f-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="1728f-120">Sunucusuz kodunuz, bu depolama hesabındaki kalıcı bilgilerle asla etkileşmemelidir ve genellikle geliştiricilerin etkileşimde bulunmak için ihtiyaç duyduğu bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="1728f-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="1728f-121">Durum bilgisi olan bir iş akışını tetikleme</span><span class="sxs-lookup"><span data-stu-id="1728f-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="1728f-122">Dayanıklı İşlevler durum bilgisi olan iş akışları, iki iç bileşene ayrılabilir; düzenleme ve etkinlik Tetikleyicileri.</span><span class="sxs-lookup"><span data-stu-id="1728f-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="1728f-123">Tetikleyiciler ve bağlamalar, Azure Işlevleri tarafından, başlangıç, giriş alma ve sonuç döndürme sırasında sunucusuz işlevlerinizin bildirilmesini sağlamak için kullanılan temel bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="1728f-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="1728f-124">Orchestration istemcisiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="1728f-124">Working with the Orchestration client</span></span>

<span data-ttu-id="1728f-125">Düzenlemeler, Azure Işlevlerinde tetiklenen işlemlerin diğer stilleriyle karşılaştırıldığında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="1728f-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="1728f-126">Dayanıklı İşlevler, saat veya hatta tamamlanması gereken işlevlerin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1728f-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="1728f-127">Bu tür davranışlar, çalışan bir düzenleme durumunun denetlenmesi, preemptively sonlanması veya dış olayların bildirimlerini gönderebilme gereksinimiyle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="1728f-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="1728f-128">Bu tür durumlarda Dayanıklı İşlevler uzantısı, genişletilmiş işlevlerle etkileşime girebilmeniz için `DurableOrchestrationClient` sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1728f-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="1728f-129">`OrchestrationClientAttribute` bağlamasını kullanarak Orchestration istemcisine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1728f-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="1728f-130">Genellikle, bu özniteliği bir `HttpTrigger` veya `ServiceBusTrigger`gibi başka bir tetikleyici türüyle dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="1728f-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="1728f-131">Kaynak işlev tetiklendikten sonra, düzenleme istemcisi bir Orchestrator işlevi başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="1728f-132">Orchestrator işlevi</span><span class="sxs-lookup"><span data-stu-id="1728f-132">The orchestrator function</span></span>

<span data-ttu-id="1728f-133">Azure Işlevleri 'nde, bir Orchestrator işlevi olarak işlev gören OrchestrationTriggerAttribute ile bir işleve açıklama ekleme.</span><span class="sxs-lookup"><span data-stu-id="1728f-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="1728f-134">Durum bilgisi olan iş akışınızı oluşturan çeşitli etkinlikleri yönetmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1728f-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="1728f-135">Orchestrator işlevleri, OrchestrationTriggerAttribute dışındaki bağlamaları kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="1728f-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="1728f-136">Bu öznitelik, yalnızca DurableOrchestrationContext parametre türüyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="1728f-137">İşlev imzasında girişlerin serisini kaldırma desteklenmediğinden başka giriş kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1728f-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="1728f-138">Orchestration istemcisi tarafından sağlanmış girdileri almak için Getınput\<T\> yöntemi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1728f-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="1728f-139">Ayrıca, düzenleme işlevlerinin dönüş türleri void, Task veya JSON serileştirilebilir değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1728f-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="1728f-140">*Hata işleme kodu breçekimi için ayrılmıştır*</span><span class="sxs-lookup"><span data-stu-id="1728f-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="1728f-141">Bir Orchestration 'un birden fazla örneği aynı anda başlatılabilir ve çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="1728f-142">`DurableOrchestrationClient` `StartNewAsync` yönteminin çağrılması, Orchestration 'un yeni bir örneğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="1728f-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="1728f-143">Yöntemi, düzenleme başladığında tamamlayan bir `Task<string>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1728f-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="1728f-144">Düzenleme işlemi 30 saniye içinde başlatılmamışsa `TimeoutException` türünde bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="1728f-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="1728f-145">`StartNewAsync` tamamlanan `Task<string>`, Orchestration örneğinin benzersiz KIMLIĞINI içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1728f-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="1728f-146">Bu örnek KIMLIĞI, belirli bir düzenleme üzerindeki işlemleri çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="1728f-147">Düzenleme durumu veya gönderilen olay bildirimleri için sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="1728f-148">Etkinlik işlevleri</span><span class="sxs-lookup"><span data-stu-id="1728f-148">The activity functions</span></span>

<span data-ttu-id="1728f-149">Etkinlik işlevleri, iş akışını oluşturmak için bir Orchestration işlevi içinde birlikte oluşturulan ayrık işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="1728f-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="1728f-150">İşte en çok gerçek iş gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1728f-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="1728f-151">İş mantığını, uzun süre çalışan süreçlerini ve bulmaca parçalarını daha büyük bir çözüme göre temsil ederler.</span><span class="sxs-lookup"><span data-stu-id="1728f-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="1728f-152">`ActivityTriggerAttribute`, `DurableActivityContext`türünde bir işlev parametresine açıklama eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1728f-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="1728f-153">Ek açıklamanın kullanılması, işlevin etkinlik işlevi olarak kullanılması amaçlanan çalışma zamanına bildirir.</span><span class="sxs-lookup"><span data-stu-id="1728f-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="1728f-154">Etkinlik işlevlerine giriş değerleri, `DurableActivityContext` parametresinin `GetInput<T>` yöntemi kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="1728f-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="1728f-155">Düzenleme işlevlerine benzer şekilde, etkinlik işlevlerinin dönüş türleri void, Task veya JSON serileştirilebilir bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1728f-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="1728f-156">Etkinlik işlevleri içinde oluşturulan işlenmemiş özel durumlar, çağıran Orchestrator işlevine gönderilir ve bir `TaskFailedException`olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="1728f-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="1728f-157">Bu noktada, hata yakalanıp Orchestrator oturumu açabilir ve etkinlik yeniden denenebilir.</span><span class="sxs-lookup"><span data-stu-id="1728f-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="1728f-158">Önerilen Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1728f-158">Recommended resources</span></span>

- [<span data-ttu-id="1728f-159">Dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="1728f-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="1728f-160">Dayanıklı İşlevler bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1728f-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="1728f-161">Dayanıklı İşlevler örnekleri yönetme</span><span class="sxs-lookup"><span data-stu-id="1728f-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="1728f-162">[Önceki](event-grid.md)
>[İleri](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="1728f-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
