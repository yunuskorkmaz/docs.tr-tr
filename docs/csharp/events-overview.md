---
title: Olaylara giriş
description: Bu genel bakışta olaylar için .NET Core ve dil tasarımı hedeflerimizin olayları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: ceae2b9319a1de9f01102987735c7db2c2883f18
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138525"
---
# <a name="introduction-to-events"></a><span data-ttu-id="9d3bc-103">Olaylara giriş</span><span class="sxs-lookup"><span data-stu-id="9d3bc-103">Introduction to events</span></span>

[<span data-ttu-id="9d3bc-104">Öncekini</span><span class="sxs-lookup"><span data-stu-id="9d3bc-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="9d3bc-105">Olaylar, bir *geç bağlama* mekanizması gibi bir temsilcidir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="9d3bc-106">Aslında, olaylar, temsilciler için dil desteği üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="9d3bc-107">Olaylar, bir şeyin meydana geldiği bir nesnenin (sistemdeki tüm ilgi bileşenlerine) bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="9d3bc-108">Başka herhangi bir bileşen olaya abone olabilir ve bir olay ortaya çıktığında bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="9d3bc-109">Büyük olasılıkla bazı programlarınızdaki olayları kullandınız.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="9d3bc-110">Birçok grafik sisteminde kullanıcı etkileşimini raporlamak için bir olay modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="9d3bc-111">Bu olaylar, fare hareketini, düğme basışlarını ve benzer etkileşimleri rapor edecektir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="9d3bc-112">Bu en yaygın bir deyişle, olayların kullanıldığı tek senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="9d3bc-113">Sınıflarınız için oluşturulması gereken olayları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="9d3bc-114">Olaylarla çalışırken dikkat edilmesi gereken önemli bir nokta, belirli bir olay için kayıtlı herhangi bir nesne olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="9d3bc-115">Bir dinleyici yapılandırılmadığında olayları tetiklememeleri için kodunuzu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="9d3bc-116">Bir olaya abone olmak Ayrıca iki nesne (olay kaynağı ve olay havuzu) arasında bir Ida oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="9d3bc-117">Olay havuzunun artık olaylarla ilgilenmemesi durumunda olay kaynağından abone olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="9d3bc-118">Olay desteği için tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="9d3bc-118">Design goals for event support</span></span>

<span data-ttu-id="9d3bc-119">Olaylar için dil tasarımı bu hedefleri hedefler:</span><span class="sxs-lookup"><span data-stu-id="9d3bc-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="9d3bc-120">Bir olay kaynağı ve olay havuzu arasında çok az sayıda bağlantısı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="9d3bc-121">Bu iki bileşen aynı kuruluş tarafından yazılamaz ve tamamen farklı zamanlamalarda bile güncelleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="9d3bc-122">Bir olaya abone olmak ve aynı olaydan aboneliği kaldırmak çok basittir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="9d3bc-123">Olay kaynakları birden çok olay abonesini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="9d3bc-124">Ayrıca, ekli olay abonesi olmadan da destek sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="9d3bc-125">Olayların hedeflerinin temsilcilerle ilgili hedeflere çok benzediğinden emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="9d3bc-126">Bu nedenle, olay dili desteğinin temsilci dili desteği üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="9d3bc-127">Olaylar için dil desteği</span><span class="sxs-lookup"><span data-stu-id="9d3bc-127">Language support for events</span></span>

<span data-ttu-id="9d3bc-128">Olayları tanımlama ve olayları abone olma sözdizimi, temsilcilerin sözdizimi uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="9d3bc-129">Bir olayı tanımlamak için `event` anahtar sözcüğünü kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="9d3bc-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="9d3bc-130">Olayın türü (Bu örnekteki`EventHandler<FileListArgs>`) bir temsilci türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="9d3bc-131">Bir olayı bildirirken izlemeniz gereken birçok kural vardır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="9d3bc-132">Genellikle, olay temsilci türünün void dönüşü vardır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="9d3bc-133">Olay bildirimleri bir fiil veya bir fiil ifadesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="9d3bc-134">Olay gerçekleşen bir şeyi raporladığında geçmiş zaman hali kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="9d3bc-135">Gerçekleşmeyen bir şeyi raporlamak için, mevcut bir zaman hali fiilini (örneğin, `Closing`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="9d3bc-136">Genellikle, var zaman hali kullanımı, sınıfınızın bazı özelleştirme davranışlarını desteklediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="9d3bc-137">En yaygın senaryolardan biri iptali destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="9d3bc-138">Örneğin, `Closing` bir olay, kapatma işleminin devam edip edemeyeceğini belirten bir bağımsız değişken içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="9d3bc-139">Diğer senaryolar, olay bağımsız değişkenlerinin özelliklerini güncelleştirerek çağıranların davranış değiştirmesine olanak sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="9d3bc-140">Algoritmanın yapması önerilen sonraki eylemi belirten bir olay oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="9d3bc-141">Olay işleyicisi, olay bağımsız değişkeninin özelliklerini değiştirerek farklı bir eylemi zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="9d3bc-142">Olayı yükseltmek istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicilerini çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d3bc-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="9d3bc-143">[Temsilciler](delegates-patterns.md)hakkında bölümünde açıklandığı gibi,?.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="9d3bc-144">işleci, bu olaya abone olmadığında olayı yapmayı denediğinizden emin olmanızı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="9d3bc-145">`+=` işlecini kullanarak bir olaya abone olursunuz:</span><span class="sxs-lookup"><span data-stu-id="9d3bc-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="9d3bc-146">Handler yöntemi, yukarıda gösterildiği gibi genellikle ' on ' önekini ve olay adını izler.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="9d3bc-147">`-=` işlecini kullanarak aboneliğinizi kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d3bc-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="9d3bc-148">Olay işleyicisini temsil eden ifade için yerel bir değişken bildirdiğim unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="9d3bc-149">Bu sayede abonelik kaldırma, işleyiciyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="9d3bc-150">Bunun yerine, lambda ifadesinin gövdesini kullandıysanız, hiçbir şey iliştirilmemiş hiçbir şey olmayan bir işleyiciyi kaldırmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="9d3bc-151">Sonraki makalede, tipik olay desenleri ve bu örnekteki farklı Çeşitlemeler hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9d3bc-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="9d3bc-152">Next</span><span class="sxs-lookup"><span data-stu-id="9d3bc-152">Next</span></span>](event-pattern.md)
