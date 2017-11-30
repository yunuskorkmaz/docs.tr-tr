---
title: "Giriş olayları"
description: ".NET Core ve dil tasarım hedeflerimiz bu genel bakışta olayları için olay hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: f81c2d9fc2ec69c295485fe06029b5de65335db0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-events"></a><span data-ttu-id="95061-104">Giriş olayları</span><span class="sxs-lookup"><span data-stu-id="95061-104">Introduction to Events</span></span>

[<span data-ttu-id="95061-105">Önceki</span><span class="sxs-lookup"><span data-stu-id="95061-105">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="95061-106">Olaylardır, temsilciler gibi bir *geç bağlama* mekanizması.</span><span class="sxs-lookup"><span data-stu-id="95061-106">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="95061-107">Aslında, olayları temsilciler dil desteğini üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="95061-107">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="95061-108">(İçin sistemdeki tüm ilgilenen bileşenleri), bir yayın için bir nesne için bir yol gerçekleştirilmedi olaylardır.</span><span class="sxs-lookup"><span data-stu-id="95061-108">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="95061-109">Herhangi bir bileşeni olaya abone olabilir ve bir olay oluşturulduğunda bildirilmesi.</span><span class="sxs-lookup"><span data-stu-id="95061-109">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="95061-110">Büyük olasılıkla programlama bazıları olayları kullandığınız.</span><span class="sxs-lookup"><span data-stu-id="95061-110">You've probably used events in some of your programming.</span></span> <span data-ttu-id="95061-111">Çok sayıda grafik sistemleri rapor kullanıcı etkileşimi olay modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95061-111">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="95061-112">Bu olaylar fare hareketini, düğme basma işlemlerine ve benzer etkileşimler raporlar.</span><span class="sxs-lookup"><span data-stu-id="95061-112">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="95061-113">En yaygın ancak kesinlikle Hayır olayları kullanıldığı tek senaryo birini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="95061-113">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="95061-114">Sınıflar için oluşmalıdır olayları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95061-114">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="95061-115">Olaylarla çalışma, olduğunda bir önemli konu için belirli bir olay kayıtlı herhangi bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="95061-115">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="95061-116">Kodunuzu olaylar hiçbir dinleyicileri zaman oluşturmaz böylece yapılandırılmış olan yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95061-116">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="95061-117">Bir olaya abone (olay kaynağı ve Olay havuzunu) iki nesne arasındaki bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95061-117">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="95061-118">Olay iç havuz olayları artık ilgileniyor olduğunda olay kaynağından işlemleri emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95061-118">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="95061-119">Olay desteği için tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="95061-119">Design Goals for Event Support</span></span>

<span data-ttu-id="95061-120">Olaylar için dil tasarımı bu hedefleri hedefler.</span><span class="sxs-lookup"><span data-stu-id="95061-120">The language design for events targets these goals.</span></span>

<span data-ttu-id="95061-121">İlk olarak, bir olay kaynağı ve bir olay havuz arasında çok az bağ etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="95061-121">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="95061-122">Bu iki bileşenin aynı kuruluş tarafından yazılabilir değil ve farklı zamanlamada bile güncelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="95061-122">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="95061-123">İkincisi, bir olaya abone olmak ve o aynı olayından aboneliği için çok basit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95061-123">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="95061-124">Ve son olarak, olay kaynakları birden çok olay aboneye desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="95061-124">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="95061-125">Ekli olay abone olması desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="95061-125">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="95061-126">Hedefler olayları için temsilciler hedefleri için çok benzer olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95061-126">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="95061-127">İşte bu nedenle olay dil desteği temsilci dil desteği de yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="95061-127">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="95061-128">Olaylar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="95061-128">Language Support for Events</span></span>

<span data-ttu-id="95061-129">Olayları tanımlama ve abone olma ya da olayların aboneliği için sözdizimi temsilciler sözdizimi uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="95061-129">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="95061-130">Kullandığınız bir olay tanımlamak için `event` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="95061-130">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="95061-131">Olay türü (`EventHandler<FileListArgs>` Bu örnekte) bir temsilci türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95061-131">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="95061-132">Bir olay bildirirken izlemelisiniz kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="95061-132">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="95061-133">Genellikle, olay temsilci türü void dönüş sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95061-133">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="95061-134">Olay bildirimleri bir fiil veya bir fiil deyimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95061-134">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="95061-135">Olay gerçekleştirilmedi bir şey bildirdiğinde geçmiş zamanın (Bu örnekte olduğu gibi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="95061-135">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="95061-136">Geçerli zamanın fiil kullanın (örneğin, `Closing`) çakışmasının benzer bildirilecek.</span><span class="sxs-lookup"><span data-stu-id="95061-136">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="95061-137">Genellikle, geçerli zamanın kullanarak sınıfınız özelleştirme davranışı çeşit desteklediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="95061-137">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="95061-138">En sık karşılaşılan senaryolardan biri, iptal desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="95061-138">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="95061-139">Örneğin, bir `Closing` olay kapatma işlemini, veya devam edip etmediğini gösteren bağımsız değişken içerebilir.</span><span class="sxs-lookup"><span data-stu-id="95061-139">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="95061-140">Diğer senaryolar olay bağımsız özelliklerini güncelleştirerek davranışını değiştirmek arayanlar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="95061-140">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="95061-141">Bir algoritma sürer önerilen bir sonraki eylem belirtmek için bir olay neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="95061-141">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="95061-142">Olay işleyicisi olay bağımsız değişkenini özelliklerini değiştirerek farklı bir eylem zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="95061-142">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="95061-143">Olayı oluşturmak istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicileri arayın:</span><span class="sxs-lookup"><span data-stu-id="95061-143">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="95061-144">Üzerinde bölümünde açıklandığı gibi [Temsilciler](delegates-patterns.md),?</span><span class="sxs-lookup"><span data-stu-id="95061-144">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="95061-145">işleci, bu olaya abone olduğunuzda olayı çalışmayın emin olmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="95061-145">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="95061-146">Kullanarak bir olaya abone `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="95061-146">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="95061-147">İşleyici genellikle önekini 'On' olay adından yukarıda gösterildiği gibi yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="95061-147">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="95061-148">Kullanarak aboneliği `-=` işleci:</span><span class="sxs-lookup"><span data-stu-id="95061-148">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="95061-149">Olay işleyicisini temsil eden ifade için yerel bir değişkeni bildirilen olduğunu dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="95061-149">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="95061-150">İşleyici abonelikten kaldırır sağlar.</span><span class="sxs-lookup"><span data-stu-id="95061-150">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="95061-151">Bunun yerine, lambda ifadesi gövdesi kullandıysanız, hiçbir şey yapmaz, hiçbir zaman eklenmiş olup, bir işleyici kaldırmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="95061-151">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="95061-152">Sonraki makalede tipik olay desenleri ve bu örnek farklı çeşidi hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="95061-152">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="95061-153">Sonraki</span><span class="sxs-lookup"><span data-stu-id="95061-153">Next</span></span>](event-pattern.md)
