---
title: Dayanıklı Azure işlevleri - sunucusuz uygulamalar
description: Dayanıklı Azure işlevleri, Azure işlevleri çalışma zamanı, durum bilgisi olan iş akışlarının kodda etkinleştirmek için genişletin.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 03197ad57813b8132fe592f4e555c6a35edbd9bd
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37405026"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="4395f-103">Dayanıklı Azure işlevleri</span><span class="sxs-lookup"><span data-stu-id="4395f-103">Durable Azure functions</span></span>

<span data-ttu-id="4395f-104">Azure işlevleri ile sunucusuz uygulamalar oluştururken, durum bilgisi olmayan bir şekilde çalıştırmak için işlemlerinizi genellikle tasarlanması.</span><span class="sxs-lookup"><span data-stu-id="4395f-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="4395f-105">Bu tasarım tercihinin nedeni, platform ölçekler kodu çalıştıran hangi sunucuların anlamak zor hale olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4395f-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="4395f-106">Ayrıca, kaç tane belirli bir anda etkin olan anlamak zor olur.</span><span class="sxs-lookup"><span data-stu-id="4395f-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="4395f-107">Ancak, bilinmesi bir işlemin geçerli durumunu gerektiren uygulamalar sınıfı vardır.</span><span class="sxs-lookup"><span data-stu-id="4395f-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="4395f-108">Bir çevrimiçi mağaza için bir sipariş göndermeden işleminde göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="4395f-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="4395f-109">Kullanıma alma işlemi işleminin durumunu bilmeniz gereken birden çok işlemlerini oluşan bir iş akışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="4395f-110">Bir müşterinin hesabını ve kredi kartı işleme sonuçlarını tüm krediler varsa ürün envanteri gibi bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="4395f-111">Bu işlemler kolayca kendi iç iş akışları veya üçüncü taraf sistemlerden hatta Hizmetleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="4395f-112">Çeşitli desenlerini bugün bu yardımcı uygulama durumu iç ve dış sistemler arasında koordinasyon ile mevcut.</span><span class="sxs-lookup"><span data-stu-id="4395f-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="4395f-113">Merkezi kuyruk sistemleri, dağıtılmış anahtar-değer depoları veya o durumu yönetmek için paylaşılan veritabanları kullanan çözümler arasında gelen yaygındır.</span><span class="sxs-lookup"><span data-stu-id="4395f-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="4395f-114">Ancak, bunlar artık sağlanan ve yönetilen için gereken tüm ek kaynaklara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4395f-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="4395f-115">Sunucusuz bir ortamda kodunuzu ile bu kaynakları el ile koordine etmek zahmetli hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="4395f-116">Azure işlevleri, durum bilgisi olan işlevler dayanıklı işlevler adlı oluşturmak için bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="4395f-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="4395f-117">Dayanıklı işlevler kod durum bilgisi olan iş akışı tanımını sağlayan Azure işlevleri çalışma zamanı bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4395f-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="4395f-118">Etkinlikler iş akışlarına bölmek tarafından dayanıklı işlevler uzantısını durumu yönetebilir, ilerleme denetim noktalarını oluşturma ve işlev çağrılarının dağıtım sunucular arasında işleme.</span><span class="sxs-lookup"><span data-stu-id="4395f-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="4395f-119">Arka planda bir Azure depolama hesabını kullan yürütme geçmişi kalıcı hale getirmek için etkinlik işlevlerini zamanlamak ve yanıtları almak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4395f-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="4395f-120">Sunucusuz kod hiçbir zaman bu depolama hesabında kalıcı bilgilerle etkileşim kuracağını ve genellikle geliştiriciler ile etkileşim kurmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4395f-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="4395f-121">Durum bilgisi olan iş akışı tetikler</span><span class="sxs-lookup"><span data-stu-id="4395f-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="4395f-122">Dayanıklı işlevler durum bilgisi olan iş akışlarında iç iki bileşene ayrılabilir; düzenleme ve etkinliği tetikler.</span><span class="sxs-lookup"><span data-stu-id="4395f-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="4395f-123">Tetikleyiciler ve bağlamalar başlatmak almak için giriş ve döndürülecek sonuçları bildirilmesini sağlamak uygulamanızın sunucusuz işlevlerini etkinleştirmek için Azure işlevleri tarafından kullanılan temel bileşenleridir.</span><span class="sxs-lookup"><span data-stu-id="4395f-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="4395f-124">Düzenleme istemcisi ile çalışma</span><span class="sxs-lookup"><span data-stu-id="4395f-124">Working with the Orchestration client</span></span>

<span data-ttu-id="4395f-125">Azure işlevleri'nde tetiklenen işlemlerinin başka stilleri karşılaştırıldığında düzenlemeleri benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="4395f-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="4395f-126">Dayanıklı işlevler ele saat veya gün tamamlamak için bile işlevlerin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4395f-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="4395f-127">Bu türden bir davranış, çalışan bir düzenleme durumunu denetlemek izinlere gerek ile sıd'lerde sonlandırmak veya dış olaylar bildirim göndermek gelir.</span><span class="sxs-lookup"><span data-stu-id="4395f-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="4395f-128">Böyle durumlarda, dayanıklı işlevler uzantısını sağlar `DurableOrchestrationClient` ile etkileşimde bulunmanızı sağlar sınıfını işlevleri düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="4395f-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="4395f-129">Kullanarak düzenleme istemcisi için size erişim `OrchestrationClientAttribute` bağlama.</span><span class="sxs-lookup"><span data-stu-id="4395f-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="4395f-130">Genellikle, bu öznitelik başka bir tetikleyici türü ile gibi dahil bir `HttpTrigger` veya `ServiceBusTrigger`.</span><span class="sxs-lookup"><span data-stu-id="4395f-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="4395f-131">Kaynak işlevi tetiklendikten sonra düzenleme istemcisi bir düzenleyici işlevi başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="4395f-132">Orchestrator işlevi</span><span class="sxs-lookup"><span data-stu-id="4395f-132">The orchestrator function</span></span>

<span data-ttu-id="4395f-133">Azure işlevleri işaretleri OrchestrationTriggerAttribute işleviyle bu işlev bir düzenleyici işlevi ek açıklama ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="4395f-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="4395f-134">Durum bilgisi olan iş akışınızı kurabilmeniz çeşitli etkinliklerinin yönetmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4395f-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="4395f-135">Orchestrator işlevleri yapamazsınız OrchestrationTriggerAttribute dışında bağlamalarının kullanın.</span><span class="sxs-lookup"><span data-stu-id="4395f-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="4395f-136">Bu öznitelik yalnızca DurableOrchestrationContext parametre türü ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="4395f-137">İşlev imzası girişlerinde seri durumdan çıkarma desteklenmiyor olduğundan, diğer giriş kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="4395f-138">Düzenleme istemcisi, GetInput sağlanan girişler almak için\<T\> yöntemi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4395f-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="4395f-139">Ayrıca, orchestration işlevlerin dönüş türleri olmalıdır void, görev veya JSON seri hale getirilebilir bir değer.</span><span class="sxs-lookup"><span data-stu-id="4395f-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="4395f-140">*Hata işleme kodunu konuyu uzatmamak amacıyla bırakıldı '*</span><span class="sxs-lookup"><span data-stu-id="4395f-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="4395f-141">Birden çok örneğini düzenleme aynı anda kullanmaya başlama ve çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="4395f-142">Çağırma `StartNewAsync` metodunda `DurableOrchestrationClient` düzenleme yeni bir örneğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="4395f-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="4395f-143">Yöntem döndürür bir `Task<string>` düzenleme başlatıldığında tamamlar.</span><span class="sxs-lookup"><span data-stu-id="4395f-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="4395f-144">Türünde bir özel durum `TimeoutException` düzenleme 30 saniye içinde başlamadığı olursa durum.</span><span class="sxs-lookup"><span data-stu-id="4395f-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="4395f-145">Tamamlanan `Task<string>` gelen `StartNewAsync` düzenleme örneğinin benzersiz Kimliğini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="4395f-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="4395f-146">Bu örnek kimliği, belirli düzenleme işlemleri çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="4395f-147">Düzenleme durumu sorgulanan veya olay bildirimleri gönderdiniz.</span><span class="sxs-lookup"><span data-stu-id="4395f-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="4395f-148">Etkinlik işlevleri</span><span class="sxs-lookup"><span data-stu-id="4395f-148">The activity functions</span></span>

<span data-ttu-id="4395f-149">Etkinlik işlevleri iş akışı oluşturmak için bir düzenleme işlevi içinde birlikte oluşan ayrık işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="4395f-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="4395f-150">İşte burada gerçek çoğunu gerçekleşmesi.</span><span class="sxs-lookup"><span data-stu-id="4395f-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="4395f-151">Bunlar, iş mantığı göstermek, çalışan işlemleri ve daha büyük bir çözümü için Bulmacanın parçaları uzun.</span><span class="sxs-lookup"><span data-stu-id="4395f-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="4395f-152">`ActivityTriggerAttribute` Türünde bir işlev parametre öğesine açıklama eklemek için kullanılan `DurableActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="4395f-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="4395f-153">Ek açıklama kullanarak, çalışma zamanı işlevi bir etkinlik işlevi kullanılması amaçlanmıştır bildirir.</span><span class="sxs-lookup"><span data-stu-id="4395f-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="4395f-154">Etkinlik işlevlere giriş değerlerini kullanarak alınır `GetInput<T>` yöntemi `DurableActivityContext` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4395f-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="4395f-155">Benzer şekilde düzenleme işlevleri, etkinlik işlevlerin dönüş türleri olmalıdır void, görev veya JSON seri hale getirilebilir bir değer.</span><span class="sxs-lookup"><span data-stu-id="4395f-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="4395f-156">Etkinlik işlevler içinde oluşturulan işlenmemiş özel durumlar çağırma orchestrator işlevine gönderileceği alıp olarak sunulan bir `TaskFailedException`.</span><span class="sxs-lookup"><span data-stu-id="4395f-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="4395f-157">Bu noktada, hata yakalandı ve orchestrator'da günlüğe kaydedilir ve etkinlik yeniden denenebilir.</span><span class="sxs-lookup"><span data-stu-id="4395f-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="4395f-158">Önerilen kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4395f-158">Recommended resources</span></span>

* [<span data-ttu-id="4395f-159">Dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="4395f-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="4395f-160">Dayanıklı işlevler için bağlamaları</span><span class="sxs-lookup"><span data-stu-id="4395f-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [<span data-ttu-id="4395f-161">Dayanıklı işlevler örneklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="4395f-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
<span data-ttu-id="4395f-162">[Önceki](event-grid.md)
[İleri](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="4395f-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>