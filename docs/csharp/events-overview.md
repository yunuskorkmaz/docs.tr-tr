---
title: Giriş olayları
description: .NET Core ve dil tasarım hedeflerimiz bu genel bakışta olayları için olay hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 2a2230ea5fba1b0cd5b13319677965e7a776549e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213480"
---
# <a name="introduction-to-events"></a><span data-ttu-id="0310c-103">Giriş olayları</span><span class="sxs-lookup"><span data-stu-id="0310c-103">Introduction to Events</span></span>

[<span data-ttu-id="0310c-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="0310c-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="0310c-105">Olaylardır, temsilciler gibi bir *geç bağlama* mekanizması.</span><span class="sxs-lookup"><span data-stu-id="0310c-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="0310c-106">Aslında, olayları temsilciler dil desteğini üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0310c-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="0310c-107">(İçin sistemdeki tüm ilgilenen bileşenleri), bir yayın için bir nesne için bir yol gerçekleştirilmedi olaylardır.</span><span class="sxs-lookup"><span data-stu-id="0310c-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="0310c-108">Herhangi bir bileşeni olaya abone olabilir ve bir olay oluşturulduğunda bildirilmesi.</span><span class="sxs-lookup"><span data-stu-id="0310c-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="0310c-109">Büyük olasılıkla programlama bazıları olayları kullandığınız.</span><span class="sxs-lookup"><span data-stu-id="0310c-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="0310c-110">Çok sayıda grafik sistemleri rapor kullanıcı etkileşimi olay modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0310c-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="0310c-111">Bu olaylar fare hareketini, düğme basma işlemlerine ve benzer etkileşimler raporlar.</span><span class="sxs-lookup"><span data-stu-id="0310c-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="0310c-112">En yaygın ancak kesinlikle Hayır olayları kullanıldığı tek senaryo birini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0310c-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="0310c-113">Sınıflar için oluşmalıdır olayları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0310c-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="0310c-114">Olaylarla çalışma, olduğunda bir önemli konu için belirli bir olay kayıtlı herhangi bir nesne olabilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="0310c-115">Kodunuzu olaylar hiçbir dinleyicileri zaman oluşturmaz böylece yapılandırılmış olan yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0310c-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="0310c-116">Bir olaya abone (olay kaynağı ve Olay havuzunu) iki nesne arasındaki bir ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0310c-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="0310c-117">Olay iç havuz olayları artık ilgileniyor olduğunda olay kaynağından işlemleri emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0310c-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="0310c-118">Olay desteği için tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="0310c-118">Design Goals for Event Support</span></span>

<span data-ttu-id="0310c-119">Olaylar için dil tasarımı bu hedefleri hedefler.</span><span class="sxs-lookup"><span data-stu-id="0310c-119">The language design for events targets these goals.</span></span>

<span data-ttu-id="0310c-120">İlk olarak, bir olay kaynağı ve bir olay havuz arasında çok az bağ etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0310c-120">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="0310c-121">Bu iki bileşenin aynı kuruluş tarafından yazılabilir değil ve farklı zamanlamada bile güncelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="0310c-122">İkincisi, bir olaya abone olmak ve o aynı olayından aboneliği için çok basit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0310c-122">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="0310c-123">Ve son olarak, olay kaynakları birden çok olay aboneye desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0310c-123">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="0310c-124">Ekli olay abone olması desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="0310c-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="0310c-125">Hedefler olayları için temsilciler hedefleri için çok benzer olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0310c-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="0310c-126">İşte bu nedenle olay dil desteği temsilci dil desteği de yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="0310c-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="0310c-127">Olaylar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="0310c-127">Language Support for Events</span></span>

<span data-ttu-id="0310c-128">Olayları tanımlama ve abone olma ya da olayların aboneliği için sözdizimi temsilciler sözdizimi uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="0310c-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="0310c-129">Kullandığınız bir olay tanımlamak için `event` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="0310c-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="0310c-130">Olay türü (`EventHandler<FileListArgs>` Bu örnekte) bir temsilci türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0310c-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="0310c-131">Bir olay bildirirken izlemelisiniz kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="0310c-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="0310c-132">Genellikle, olay temsilci türü void dönüş sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0310c-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="0310c-133">Olay bildirimleri bir fiil veya bir fiil deyimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0310c-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="0310c-134">Olay gerçekleştirilmedi bir şey bildirdiğinde geçmiş zamanın (Bu örnekte olduğu gibi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0310c-134">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="0310c-135">Geçerli zamanın fiil kullanın (örneğin, `Closing`) çakışmasının benzer bildirilecek.</span><span class="sxs-lookup"><span data-stu-id="0310c-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="0310c-136">Genellikle, geçerli zamanın kullanarak sınıfınız özelleştirme davranışı çeşit desteklediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0310c-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="0310c-137">En sık karşılaşılan senaryolardan biri, iptal desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="0310c-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="0310c-138">Örneğin, bir `Closing` olay kapatma işlemini, veya devam edip etmediğini gösteren bağımsız değişken içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="0310c-139">Diğer senaryolar olay bağımsız özelliklerini güncelleştirerek davranışını değiştirmek arayanlar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="0310c-140">Bir algoritma sürer önerilen bir sonraki eylem belirtmek için bir olay neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="0310c-141">Olay işleyicisi olay bağımsız değişkenini özelliklerini değiştirerek farklı bir eylem zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="0310c-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="0310c-142">Olayı oluşturmak istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicileri arayın:</span><span class="sxs-lookup"><span data-stu-id="0310c-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="0310c-143">Üzerinde bölümünde açıklandığı gibi [Temsilciler](delegates-patterns.md),?</span><span class="sxs-lookup"><span data-stu-id="0310c-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="0310c-144">işleci, bu olaya abone olduğunuzda olayı çalışmayın emin olmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0310c-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="0310c-145">Kullanarak bir olaya abone `+=` işleci:</span><span class="sxs-lookup"><span data-stu-id="0310c-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="0310c-146">İşleyici genellikle önekini 'On' olay adından yukarıda gösterildiği gibi yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="0310c-146">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="0310c-147">Kullanarak aboneliği `-=` işleci:</span><span class="sxs-lookup"><span data-stu-id="0310c-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="0310c-148">Olay işleyicisini temsil eden ifade için yerel bir değişkeni bildirilen olduğunu dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0310c-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="0310c-149">İşleyici abonelikten kaldırır sağlar.</span><span class="sxs-lookup"><span data-stu-id="0310c-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="0310c-150">Bunun yerine, lambda ifadesi gövdesi kullandıysanız, hiçbir şey yapmaz, hiçbir zaman eklenmiş olup, bir işleyici kaldırmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0310c-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="0310c-151">Sonraki makalede tipik olay desenleri ve bu örnek farklı çeşidi hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0310c-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="0310c-152">Next</span><span class="sxs-lookup"><span data-stu-id="0310c-152">Next</span></span>](event-pattern.md)
