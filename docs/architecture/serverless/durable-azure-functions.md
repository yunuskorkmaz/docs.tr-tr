---
title: Dayanıklı Azure fonksiyonları - Sunucusuz uygulamalar
description: Dayanıklı Azure işlevleri, koddaki devlet eserini etkinleştirmek için Azure İşlevlerini çalışma süresini genişletir.
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522853"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="b3414-103">Dayanıklı Azure işlevleri</span><span class="sxs-lookup"><span data-stu-id="b3414-103">Durable Azure functions</span></span>

<span data-ttu-id="b3414-104">Azure İşlevleri ile sunucusuz uygulamalar oluştururken, işlemleriniz genellikle stateless bir şekilde çalışacak şekilde tasarlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="b3414-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="b3414-105">Bu tasarım seçiminin nedeni, platform ölçeklendikçe kodun hangi sunucularda çalıştığını bilmenin zorlaşmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b3414-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="b3414-106">Ayrıca, herhangi bir noktada kaç örneğin etkin olduğunu bilmek de zorlaşır.</span><span class="sxs-lookup"><span data-stu-id="b3414-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="b3414-107">Ancak, bir işlemin geçerli durumunun bilinmesini gerektiren uygulama sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="b3414-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="b3414-108">Çevrimiçi bir mağazaya sipariş gönderme işlemini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="b3414-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="b3414-109">Ödeme işlemi, işlemin durumunu bilmesi gereken birden çok işlemden oluşan bir iş akışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="b3414-110">Bu tür bilgiler, müşterinin hesabında herhangi bir kredi varsa ürün envanterini ve kredi kartının işlenmesinin sonuçlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="b3414-111">Bu işlemler kolayca kendi iç iş akışları ve hatta üçüncü taraf sistemlerden hizmetleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="b3414-112">Günümüzde iç ve dış sistemler arasında uygulama durumunun koordinasyonuna yardımcı olan çeşitli desenler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b3414-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="b3414-113">Merkezi sıraya sistemleri, dağıtılan anahtar değer depoları veya bu durumu yönetmek için paylaşılan veritabanlarına dayanan çözümlerle karşılaşmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b3414-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="b3414-114">Ancak, bunların tümü artık sağlanması ve yönetilmesi gereken ek kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="b3414-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="b3414-115">Sunucusuz bir ortamda, kodunuz bu kaynaklarla el ile koordine etmeye çalışırken hantal hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="b3414-116">Azure İşlevler, Dayanıklı Işlevler adı verilen durum lu işlevler oluşturmak için bir alternatif sunar.</span><span class="sxs-lookup"><span data-stu-id="b3414-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="b3414-117">Dayanıklı Işlevler, koddaki devlet li iş akışlarının tanımını sağlayan Azure İşlevleri çalışma zamanının bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b3414-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="b3414-118">İş akışlarını etkinliklere ayırarak, Dayanıklı Işlevler uzantısı durumu yönetebilir, ilerleme denetim leri oluşturabilir ve işlev çağrılarının sunucular arasında dağıtımını işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="b3414-119">Arka planda, yürütme geçmişini sürdürmek, etkinlik işlevlerini zamanlamak ve yanıtları almak için bir Azure Depolama hesabı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3414-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="b3414-120">Sunucusuz kodunuz hiçbir zaman bu depolama hesabındaki kalıcı bilgilerle etkileşime girmemelidir ve genellikle geliştiricilerin etkileşimde olması gereken bir şey değildir.</span><span class="sxs-lookup"><span data-stu-id="b3414-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="b3414-121">Durum lu bir iş akışını tetikleme</span><span class="sxs-lookup"><span data-stu-id="b3414-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="b3414-122">Dayanıklı Işlevler'deki durumsal iş akışları iki içsel bileşene ayrılabilir; orkestrasyon ve aktivite tetikler.</span><span class="sxs-lookup"><span data-stu-id="b3414-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="b3414-123">Tetikleyiciler ve bağlamalar, sunucusuz işlevlerinizin başlatıldığında, girdi alacağında ve sonuçları döndüreceğinizde bildirilmesini sağlamak için Azure İşlevleri tarafından kullanılan temel bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="b3414-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="b3414-124">Orkestrasyon istemcisi ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b3414-124">Working with the Orchestration client</span></span>

<span data-ttu-id="b3414-125">Azure İşlevlerinde tetiklenen diğer işlem stilleriyle karşılaştırıldığında, orkestrasyonlar benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="b3414-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="b3414-126">Dayanıklı Fonksiyonlar, tamamlanması saatler, hatta günler süren işlevlerin yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3414-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="b3414-127">Bu tür davranışlar, çalışan bir orkestrasyonun durumunu denetleme, önceden sonlandırma veya dış olaylarla ilgili bildirimler gönderebilme gereksinimiyle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="b3414-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="b3414-128">Bu gibi durumlarda, Dayanıklı İşlevler uzantısı, düzenlenmiş işlevlerle etkileşimkurmanızı sağlayan `DurableOrchestrationClient` sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3414-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="b3414-129">Bağlamayı kullanarak orkestrasyon istemcisine `OrchestrationClientAttribute` erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3414-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="b3414-130">Genellikle, bu özniteliği başka bir tetikleyici türüyle `HttpTrigger` eklersiniz, örneğin. `ServiceBusTrigger`</span><span class="sxs-lookup"><span data-stu-id="b3414-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="b3414-131">Kaynak işlevi tetiklendikten sonra, orkestrasyon istemcisi bir orchestrator işlevini başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

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

### <a name="the-orchestrator-function"></a><span data-ttu-id="b3414-132">Orkestratör işlevi</span><span class="sxs-lookup"><span data-stu-id="b3414-132">The orchestrator function</span></span>

<span data-ttu-id="b3414-133">Azure İşlevlerinde OrchestrationTriggerAttribute ile bir işlevin açıklama ekedilmesi, bir orkestratör işlevi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="b3414-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="b3414-134">Özel iş akışınızı oluşturan çeşitli etkinlikleri yönetmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b3414-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="b3414-135">Orchestrator işlevleri OrchestrationTriggerAttribute dışındaki bağlamaları kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="b3414-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="b3414-136">Bu öznitelik yalnızca Dayanıklı Düzenleme Bağlamı'nın parametre türüyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="b3414-137">İşlev imzasındaki girdilerin deserialization desteklenmediğinden başka giriş ler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b3414-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="b3414-138">Düzenleme istemcisi tarafından sağlanan girişleri almak için\<\> GetInput T yöntemi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3414-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="b3414-139">Ayrıca, düzenleme işlevlerinin dönüş türleri geçersiz, Görev veya JSON serileştirilebilir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3414-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="b3414-140">*Hata işleme kodu kısalık için dışarıda bırakıldı*</span><span class="sxs-lookup"><span data-stu-id="b3414-140">*Error handling code has been left out for brevity*</span></span>

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

<span data-ttu-id="b3414-141">Bir orkestrasyonun birden çok örneği aynı anda başlatılabilir ve çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="b3414-142">Başlatma `StartNewAsync` yöntemini `DurableOrchestrationClient` çağırmak, orkestrasyonun yeni bir örneğini başlatıyor.</span><span class="sxs-lookup"><span data-stu-id="b3414-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="b3414-143">Yöntem, orkestrasyon başlatıldığında tamamlayan bir `Task<string>` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3414-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="b3414-144">Orkestrasyon `TimeoutException` 30 saniye içinde başlamadıysa, tür bir istisna atılır.</span><span class="sxs-lookup"><span data-stu-id="b3414-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="b3414-145">Tamamlanan `Task<string>` `StartNewAsync` orkestrasyon örneğinin benzersiz kimliğini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b3414-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="b3414-146">Bu örnek kimliği, belirli bir düzenleme deki işlemleri çağırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="b3414-147">Orkestrasyon durum için sorgulanabilir veya olay bildirimleri gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="b3414-148">Etkinlik fonksiyonları</span><span class="sxs-lookup"><span data-stu-id="b3414-148">The activity functions</span></span>

<span data-ttu-id="b3414-149">Etkinlik işlevleri, iş akışını oluşturmak için bir orkestrasyon işlevi içinde bir araya gelen ayrık işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="b3414-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="b3414-150">Burada gerçek işin çoğu yer alacak.</span><span class="sxs-lookup"><span data-stu-id="b3414-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="b3414-151">Onlar iş mantığı, uzun çalışan süreçler ve daha büyük bir çözüm için bulmaca parçaları temsil.</span><span class="sxs-lookup"><span data-stu-id="b3414-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="b3414-152">Bu `ActivityTriggerAttribute` tür `DurableActivityContext`bir işlev parametresi açıklama yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3414-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="b3414-153">Ek açıklamanın kullanılması, çalışma saatini işlevin bir etkinlik işlevi olarak kullanılmasının amaçlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b3414-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="b3414-154">Etkinlik işlevlerine giriş değerleri `GetInput<T>` `DurableActivityContext` parametre yöntemi kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="b3414-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="b3414-155">Düzenleme işlevlerine benzer şekilde, etkinlik işlevlerinin dönüş türleri geçersiz, Görev veya JSON serileştirilebilir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3414-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="b3414-156">Etkinlik işlevleri içinde atılan işlenmemiş özel durumlar, çağrı orkestratör işlevine gönderilir `TaskFailedException`ve bir .</span><span class="sxs-lookup"><span data-stu-id="b3414-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="b3414-157">Bu noktada, hata yakalanabilir ve orkestratörde günlüğe kaydedilebilir ve etkinlik yeniden denenebilir.</span><span class="sxs-lookup"><span data-stu-id="b3414-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="b3414-158">Önerilen kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b3414-158">Recommended resources</span></span>

- [<span data-ttu-id="b3414-159">Dayanıklı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b3414-159">Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="b3414-160">Dayanıklı Fonksiyonlar için Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b3414-160">Bindings for Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="b3414-161">Dayanıklı İşlevler'deki örnekleri yönetme</span><span class="sxs-lookup"><span data-stu-id="b3414-161">Manage instances in Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="b3414-162">[Önceki](event-grid.md)
>[Sonraki](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="b3414-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
