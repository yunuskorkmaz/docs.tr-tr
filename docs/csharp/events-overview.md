---
title: Olaylara giriş
description: Bu genel bakışta .NET Core'daki olaylar ve etkinlikler için dil tasarımı hedeflerimiz hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: 4e660f85eecfd5668919baf21a0d26f858faf5a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146120"
---
# <a name="introduction-to-events"></a><span data-ttu-id="d3e1c-103">Olaylara giriş</span><span class="sxs-lookup"><span data-stu-id="d3e1c-103">Introduction to events</span></span>

[<span data-ttu-id="d3e1c-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="d3e1c-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="d3e1c-105">Olaylar, delegeler *gibi, geç bağlama* mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="d3e1c-106">Aslında, olaylar delegeler için dil desteği üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="d3e1c-107">Olaylar, bir nesnenin bir şey olduğunu (sistemdeki tüm ilgili bileşenlere) yayınlamasının bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="d3e1c-108">Başka bir bileşen olaya abone olabilir ve bir olay yükseltildiğinde bilgilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="d3e1c-109">Muhtemelen bazı programlarınızda olayları kullandınız.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="d3e1c-110">Birçok grafik sistemi, kullanıcı etkileşimini bildirmek için bir olay modeline sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="d3e1c-111">Bu olaylar fare hareketini, düğme tuşlarını ve benzer etkileşimleri bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="d3e1c-112">Bu en yaygın, ama kesinlikle olayların kullanıldığı tek senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="d3e1c-113">Sınıflarınız için yükseltilmesi gereken olayları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="d3e1c-114">Olaylarla çalışırken göz önünde bulundurulması gereken önemli noktalardan biri, belirli bir olay için kayıtlı herhangi bir nesne nin olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="d3e1c-115">Hiçbir dinleyici yapılandırılınca olayları yükseltmemesi için kodunuzu yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="d3e1c-116">Bir olaya abone olmak da iki nesne (olay kaynağı ve olay batması) arasında bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="d3e1c-117">Olaylarla artık ilgilenmediğinde olayın etkinlik kaynağından aboneliğini kaldırdığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="d3e1c-118">Etkinlik desteği için tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="d3e1c-118">Design goals for event support</span></span>

<span data-ttu-id="d3e1c-119">Etkinlikler için dil tasarımı şu hedefleri hedefler:</span><span class="sxs-lookup"><span data-stu-id="d3e1c-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="d3e1c-120">Olay kaynağı ile olay lavabosu arasında çok az bağlantı olmasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="d3e1c-121">Bu iki bileşen aynı kuruluş tarafından yazılmayabilir ve hatta tamamen farklı zamanlamalarda güncelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="d3e1c-122">Bir etkinliğe abone olmak ve aynı etkinlikten aboneliğinizi iptal etmek çok basit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="d3e1c-123">Olay kaynakları birden çok olay abonelerini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="d3e1c-124">Ayrıca hiçbir olay aboneleri ekli olan destek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="d3e1c-125">Etkinliklerin hedeflerinin delegelerin hedeflerine çok benzediğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="d3e1c-126">Bu nedenle etkinlik dili desteği temsilci dil desteği üzerine kuruludur.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="d3e1c-127">Etkinlikler için dil desteği</span><span class="sxs-lookup"><span data-stu-id="d3e1c-127">Language support for events</span></span>

<span data-ttu-id="d3e1c-128">Olayları tanımlamak ve olaylardan abone olmak veya aboneliğini bozmak için sözdizimi, temsilciler için sözdiziminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="d3e1c-129">Bir olayı tanımlamak için `event` anahtar kelimeyi kullanın:</span><span class="sxs-lookup"><span data-stu-id="d3e1c-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="d3e1c-130">Olayın türü (bu`EventHandler<FileListArgs>` örnekte) bir temsilci türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="d3e1c-131">Bir olayı bildirirken izlemeniz gereken birkaç kural vardır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="d3e1c-132">Genellikle, olay temsilcisi türü geçersiz bir dönüş vardır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="d3e1c-133">Olay bildirimleri bir fiil veya fiil tümceciği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="d3e1c-134">Olay, olan bir şeyi bildirdiğinde geçmiş zaman'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="d3e1c-135">Olmak üzere olan bir şeyi `Closing`bildirmek için şimdiki zaman fiilini (örneğin,) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="d3e1c-136">Genellikle, şimdiki zaman kullanarak sınıf özelleştirme davranışı çeşit desteklediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="d3e1c-137">En yaygın senaryolardan biri iptali desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="d3e1c-138">Örneğin, bir `Closing` olay, yakın işlemin devam edip etmeyeceğini belirten bir bağımsız değişken içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="d3e1c-139">Diğer senaryolar, arayanların olay bağımsız değişkenlerinin özelliklerini güncelleştirerek davranışı değiştirmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="d3e1c-140">Bir algoritmanın yapacağı önerilen sonraki eylemi belirtmek için bir olay yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="d3e1c-141">Olay işleyicisi olay bağımsız değişkeninin özelliklerini değiştirerek farklı bir eylem görevden alabilir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="d3e1c-142">Olayı yükseltmek istediğinizde, temsilci çağırma sözdizimini kullanarak olay işleyicilerini çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="d3e1c-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="d3e1c-143">[Delegeler](delegates-patterns.md)bölümünde tartışıldığı gibi , ?.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="d3e1c-144">işleci, bu etkinliğe abone olmadığında olayı yükseltmeye çalışmadığınızdan emin olmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>

<span data-ttu-id="d3e1c-145">İşletici kullanarak bir `+=` etkinliğe abone olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d3e1c-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="d3e1c-146">Işleyici yöntemi genellikle yukarıda gösterildiği gibi olay adı ardından 'Açık' öneki vardır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="d3e1c-147">İşleç kullanarak `-=` aboneliğinizi iptal elabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d3e1c-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="d3e1c-148">Olay işleyicisini temsil eden ifade için yerel bir değişken ilân ettiğimi belirtmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="d3e1c-149">Bu, aboneliği iptal etme işleyicisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="d3e1c-150">Bunun yerine, lambda ifadesinin gövdesini kullandıysanız, hiç eklenmiş olmayan ve hiçbir şey yapmayan bir işleyiciyi kaldırmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="d3e1c-151">Sonraki makalede, tipik olay desenleri ve bu örnekte farklı varyasyonlar hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d3e1c-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="d3e1c-152">Sonraki</span><span class="sxs-lookup"><span data-stu-id="d3e1c-152">Next</span></span>](event-pattern.md)
