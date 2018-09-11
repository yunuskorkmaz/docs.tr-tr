---
title: Olaylara Giriş
description: .NET Core ve olayları bu genel bakış için dil tasarım hedeflerimiz olayları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 9f14954dd2e8aeacf3c5ae70a9e891ad11a6f0d7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365309"
---
# <a name="introduction-to-events"></a><span data-ttu-id="a79b7-103">Olaylara Giriş</span><span class="sxs-lookup"><span data-stu-id="a79b7-103">Introduction to Events</span></span>

[<span data-ttu-id="a79b7-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="a79b7-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="a79b7-105">Olaylar, temsilciler gibi bir *geç bağlama* mekanizması.</span><span class="sxs-lookup"><span data-stu-id="a79b7-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="a79b7-106">Aslında, olaylar, temsilciler için dil desteği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a79b7-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="a79b7-107">Bir yol ('ilgilenen tüm sistem bileşenlerinde), bir yayın bir nesne için gerçekleşen olaylardır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="a79b7-108">Başka bir bileşen olaya abone olabilir ve bir olay oluşturulduğunda bildirilmesi.</span><span class="sxs-lookup"><span data-stu-id="a79b7-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="a79b7-109">Büyük olasılıkla programlama bazıları olayları kullandınız.</span><span class="sxs-lookup"><span data-stu-id="a79b7-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="a79b7-110">Pek çok grafik sistemleri rapor kullanıcı etkileşimi bir olay modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="a79b7-111">Bu olaylar, fare hareketini, düğme basma işlemlerine ve benzer etkileşimleri rapor.</span><span class="sxs-lookup"><span data-stu-id="a79b7-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="a79b7-112">Bu en yaygın ancak açmamalı olayları kullanıldığı tek senaryo biridir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="a79b7-113">Sınıfları için harekete Geçirilmemesi gereken olayları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a79b7-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="a79b7-114">Olaylar ile çalışmayla, olduğunda önemli bir husus, belirli bir olay için kaydedilen herhangi bir nesne olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="a79b7-115">Kodunuzu böylece hiçbir dinleyicileri olduğunda olayları geçirmemesi yapılandırılmış yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="a79b7-116">Bir olaya abone olma, iki nesne (olay kaynağı ve olay havuzu) arasında bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a79b7-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="a79b7-117">Olay havuzu olayları artık ilgilenilmiyor olduğunda olay kaynağından abonelikten çıkma emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="a79b7-118">Olay desteği için tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="a79b7-118">Design Goals for Event Support</span></span>

<span data-ttu-id="a79b7-119">Olaylar için dil tasarımını bu hedeflere hedefler.</span><span class="sxs-lookup"><span data-stu-id="a79b7-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="a79b7-120">İlk olarak, bir olay kaynağı ve olay havuzu arasında çok az eşleştirmeye etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a79b7-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="a79b7-121">Bu iki bileşenin aynı kuruluş tarafından yazılabilir değil ve hatta tamamen farklı zamanlamalarda güncelleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="a79b7-122">İkincisi, çok basit bir olaya abone olun ve bu aynı olayın aboneliğini kaldırmak için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="a79b7-123">Ve son olarak, olay kaynakları birden çok etkinlik abonelerinden desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="a79b7-124">Bağlı hiçbir etkinlik abonelerinden sahip desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="a79b7-125">Olaylar için hedef hedefler için temsilciler çok benzer olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a79b7-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="a79b7-126">İşte bu olay dil desteği temsilci dil desteği de yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="a79b7-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="a79b7-127">Olaylar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="a79b7-127">Language Support for Events</span></span>

<span data-ttu-id="a79b7-128">Olayları tanımlama ve abone veya olaylardan aboneliği sözdizimi temsilcileri söz diziminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="a79b7-129">Kullandığınız bir olayı tanımlamak için `event` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="a79b7-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="a79b7-130">Olay türü (`EventHandler<FileListArgs>` Bu örnekte) bir temsilci türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="a79b7-131">Bir olay bildirirken izlemelidir kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="a79b7-132">Genellikle, olay temsilci türü bir void dönüş sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="a79b7-133">Olay bildirimleri, fiil veya bir fiil ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="a79b7-134">Olay gerçekleşen bir sorun bildirdiğinde geçmiş şimdiki (Bu örnekte olduğu gibi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a79b7-134">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="a79b7-135">Şimdiki fiil kullanın (örneğin, `Closing`) gerçekleşmek üzere olan bir sorun bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="a79b7-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="a79b7-136">Genellikle, şimdiki kullanarak sınıfınız özelleştirme davranışı tür desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="a79b7-137">En sık karşılaşılan senaryolardan biri, iptal desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="a79b7-138">Örneğin, bir `Closing` olay kapatma işlemi, veya devam edip etmediğini belirtir bir bağımsız değişken içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="a79b7-139">Olay bağımsız değişkenlerinin özelliklerini güncelleştirerek davranışını değiştirmek çağıranlar diğer senaryoları etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a79b7-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="a79b7-140">Bir algoritma sürer önerilen bir sonraki eylemi belirtmek için bir olay neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="a79b7-141">Olay işleyicisi, olay bağımsız değişkenini özelliklerini değiştirerek farklı bir eylem zorunlu.</span><span class="sxs-lookup"><span data-stu-id="a79b7-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="a79b7-142">Olayı oluşturmak istediğinizde, temsilci çağırma söz dizimi kullanarak olay işleyicileri çağırın:</span><span class="sxs-lookup"><span data-stu-id="a79b7-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="a79b7-143">Üzerinde bölümünde açıklandığı gibi [Temsilciler](delegates-patterns.md),?</span><span class="sxs-lookup"><span data-stu-id="a79b7-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="a79b7-144">işleci, o olaya abone olduğunuzda olayı çalışmayın emin olmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a79b7-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="a79b7-145">Kullanarak bir olaya abone `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="a79b7-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += onProgress;
```

<span data-ttu-id="a79b7-146">İşleyicisi yöntemi genellikle 'On' olay adından önce gelen yukarıda da gösterildiği gibi önekidir.</span><span class="sxs-lookup"><span data-stu-id="a79b7-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="a79b7-147">Kullanarak abonelikten `-=` işleci:</span><span class="sxs-lookup"><span data-stu-id="a79b7-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="a79b7-148">Olay işleyicisi temsil eden ifade için yerel bir değişken bildirildi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a79b7-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="a79b7-149">İşleyici unsubscribe kaldırır sağlar.</span><span class="sxs-lookup"><span data-stu-id="a79b7-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="a79b7-150">Bunun yerine, lambda ifadesinin gövdesinin kullandıysanız, hiçbir şey yapan hiçbir zaman eklenmiş bir işleyici kaldırmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a79b7-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="a79b7-151">Sonraki makalede, tipik olay desenleri ve bu örnekte farklı çeşitlerini hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a79b7-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="a79b7-152">Next</span><span class="sxs-lookup"><span data-stu-id="a79b7-152">Next</span></span>](event-pattern.md)
