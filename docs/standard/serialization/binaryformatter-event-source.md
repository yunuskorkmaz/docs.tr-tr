---
title: BinaryFormatter olay kaynağı
description: Seri hale getirme veya seri durumundan çıkarma sırasında günlüğe kaydetmek için BinaryFormatter olay kaynağını nasıl kullanacağınızı öğrenin.
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740422"
---
# <a name="binaryformatter-event-source"></a><span data-ttu-id="5d578-103">BinaryFormatter olay kaynağı</span><span class="sxs-lookup"><span data-stu-id="5d578-103">BinaryFormatter event source</span></span>

<span data-ttu-id="5d578-104">.NET 5,0 ' den itibaren, bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Diagnostics.Tracing.EventSource> nesne serileştirme veya serisini kaldırma gerçekleşirken görünürlük sağlayan yerleşik bir derleme içerir.</span><span class="sxs-lookup"><span data-stu-id="5d578-104">Starting with .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> includes a built-in <xref:System.Diagnostics.Tracing.EventSource> that gives you visibility into when an object serialization or deserialization is occurring.</span></span> <span data-ttu-id="5d578-105">Uygulamalar, <xref:System.Diagnostics.Tracing.EventListener> Bu bildirimleri dinlemek ve günlüğe kaydetmek için türetilmiş türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-105">Apps can use <xref:System.Diagnostics.Tracing.EventListener>-derived types to listen for these notifications and log them.</span></span>

<span data-ttu-id="5d578-106">Bu işlevsellik bir veya için bir alternatif değildir <xref:System.Runtime.Serialization.SerializationBinder> <xref:System.Runtime.Serialization.ISerializationSurrogate> ve serileştirilmiş veya seri durumdan çıkarılan verileri değiştirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5d578-106">This functionality is not a substitute for a <xref:System.Runtime.Serialization.SerializationBinder> or an <xref:System.Runtime.Serialization.ISerializationSurrogate> and can't be used to modify the data being serialized or deserialized.</span></span> <span data-ttu-id="5d578-107">Bunun yerine, bu olay sistemi seri hale getirilen veya seri durumdan çıkarılan türlerin içgörüleri sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d578-107">Rather, this eventing system is intended to provide insight into the types being serialized or deserialized.</span></span> <span data-ttu-id="5d578-108">Ayrıca `BinaryFormatter` , altyapıda, üçüncü taraf kitaplık kodundan kaynaklanan çağrılar gibi istenmeyen çağrıları algılamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-108">It can also be used to detect unintended calls into the `BinaryFormatter` infrastructure, such as calls originating from third-party library code.</span></span>

## <a name="description-of-events"></a><span data-ttu-id="5d578-109">Olayların açıklaması</span><span class="sxs-lookup"><span data-stu-id="5d578-109">Description of events</span></span>

<span data-ttu-id="5d578-110">`BinaryFormatter`Olay kaynağı iyi bilinen ada sahiptir `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` .</span><span class="sxs-lookup"><span data-stu-id="5d578-110">The `BinaryFormatter` event source has the well-known name `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span></span> <span data-ttu-id="5d578-111">Dinleyiciler 6 olaya abone olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-111">Listeners may subscribe to 6 events.</span></span>

### <a name="serializationstart-event-id--10"></a><span data-ttu-id="5d578-112">SerializationStart olayı (ID = `10` )</span><span class="sxs-lookup"><span data-stu-id="5d578-112">SerializationStart event (id = `10`)</span></span>

<span data-ttu-id="5d578-113"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>Çağrıldığında ve serileştirme işlemini başlatmışsa tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5d578-113">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> has been called and has started the serialization process.</span></span> <span data-ttu-id="5d578-114">Bu olay `SerializationEnd` olayla eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="5d578-114">This event is paired with the `SerializationEnd` event.</span></span> <span data-ttu-id="5d578-115">`SerializationStart`Bir nesne `BinaryFormatter.Serialize` kendi serileştirme yordamı içinde çağrılırsa, olay yinelemeli olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-115">The `SerializationStart` event can be called recursively if an object calls `BinaryFormatter.Serialize` within its own serialization routine.</span></span>

<span data-ttu-id="5d578-116">Bu olay yük içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5d578-116">This event doesn't contain a payload.</span></span>

### <a name="serializationend-event-id--11"></a><span data-ttu-id="5d578-117">SerializationEnd olayı (kimlik = `11` )</span><span class="sxs-lookup"><span data-stu-id="5d578-117">SerializationEnd event (id = `11`)</span></span>

<span data-ttu-id="5d578-118">`BinaryFormatter.Serialize`, İşini tamamladığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5d578-118">Raised when `BinaryFormatter.Serialize` has completed its work.</span></span> <span data-ttu-id="5d578-119">Her bir oluşumu, `SerializationEnd` son eşlenmemiş etkinliğin tamamlanmasını gösterir `SerializationStart` .</span><span class="sxs-lookup"><span data-stu-id="5d578-119">Each occurrence of `SerializationEnd` denotes the completion of the last unpaired `SerializationStart` event.</span></span>

<span data-ttu-id="5d578-120">Bu olay yük içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5d578-120">This event doesn't contain a payload.</span></span>

### <a name="serializingobject-event-id--12"></a><span data-ttu-id="5d578-121">SerializingObject olayı (ID = `12` )</span><span class="sxs-lookup"><span data-stu-id="5d578-121">SerializingObject event (id = `12`)</span></span>

<span data-ttu-id="5d578-122">`BinaryFormatter.Serialize`Temel olmayan bir türü serileştirme işleminde olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5d578-122">Raised when `BinaryFormatter.Serialize` is in the process of serializing a non-primitive type.</span></span> <span data-ttu-id="5d578-123">`BinaryFormatter`Altyapı özel-belirli türleri ( `string` ve gibi `int` ) ve bu türlere rastlarınca bu olayı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="5d578-123">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="5d578-124">Bu olay, Kullanıcı tanımlı türler ve yerel olarak anlayan diğer türler için oluşturulur `BinaryFormatter` .</span><span class="sxs-lookup"><span data-stu-id="5d578-124">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="5d578-125">Bu olay, ve olayları arasında sıfır veya daha fazla kez oluşturulabilir `SerializationStart` `SerializationEnd` .</span><span class="sxs-lookup"><span data-stu-id="5d578-125">This event may be raised zero or more times between `SerializationStart` and `SerializationEnd` events.</span></span>

<span data-ttu-id="5d578-126">Bu olay bir bağımsız değişken içeren bir yük içerir:</span><span class="sxs-lookup"><span data-stu-id="5d578-126">This event contains a payload with one argument:</span></span>

* <span data-ttu-id="5d578-127">`typeName` ( `string` ): <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> Serileştirilmekte olan türün derleme nitelikli adı (bkz.).</span><span class="sxs-lookup"><span data-stu-id="5d578-127">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being serialized.</span></span>

### <a name="deserializationstart-event-id--20"></a><span data-ttu-id="5d578-128">DeserializationStart olayı (ID = `20` )</span><span class="sxs-lookup"><span data-stu-id="5d578-128">DeserializationStart event (id = `20`)</span></span>

<span data-ttu-id="5d578-129">Çağrıldığında oluşturulur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> ve serisini kaldırma işlemini başlattı.</span><span class="sxs-lookup"><span data-stu-id="5d578-129">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> has been called and has started the deserialization process.</span></span> <span data-ttu-id="5d578-130">Bu olay `DeserializationEnd` olayla eşleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="5d578-130">This event is paired with the `DeserializationEnd` event.</span></span> <span data-ttu-id="5d578-131">`DeserializationStart`Bir nesne `BinaryFormatter.Deserialize` kendi seri kaldırma yordamı içinde çağrılırsa, olay yinelemeli olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-131">The `DeserializationStart` event can be called recursively if an object calls `BinaryFormatter.Deserialize` within its own deserialization routine.</span></span>

<span data-ttu-id="5d578-132">Bu olay yük içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5d578-132">This event doesn't contain a payload.</span></span>

### <a name="deserializationend-event-id--21"></a><span data-ttu-id="5d578-133">DeserializationEnd olayı (ID = `21` )</span><span class="sxs-lookup"><span data-stu-id="5d578-133">DeserializationEnd event (id = `21`)</span></span>

<span data-ttu-id="5d578-134">`BinaryFormatter.Deserialize`, İşini tamamladığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5d578-134">Raised when `BinaryFormatter.Deserialize` has completed its work.</span></span> <span data-ttu-id="5d578-135">Her bir oluşumu, `DeserializationEnd` son eşlenmemiş etkinliğin tamamlanmasını gösterir `DeserializationStart` .</span><span class="sxs-lookup"><span data-stu-id="5d578-135">Each occurrence of `DeserializationEnd` denotes the completion of the last unpaired `DeserializationStart` event.</span></span>

<span data-ttu-id="5d578-136">Bu olay yük içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5d578-136">This event doesn't contain a payload.</span></span>

### <a name="deserializingobject-event-id--22"></a><span data-ttu-id="5d578-137">DeserializingObject olayı (ID = `22` )</span><span class="sxs-lookup"><span data-stu-id="5d578-137">DeserializingObject event (id = `22`)</span></span>

<span data-ttu-id="5d578-138">`BinaryFormatter.Deserialize`İlkel olmayan bir türün serisini kaldırma işleminde olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5d578-138">Raised when `BinaryFormatter.Deserialize` is in the process of deserializing a non-primitive type.</span></span> <span data-ttu-id="5d578-139">`BinaryFormatter`Altyapı özel-belirli türleri ( `string` ve gibi `int` ) ve bu türlere rastlarınca bu olayı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="5d578-139">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="5d578-140">Bu olay, Kullanıcı tanımlı türler ve yerel olarak anlayan diğer türler için oluşturulur `BinaryFormatter` .</span><span class="sxs-lookup"><span data-stu-id="5d578-140">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="5d578-141">Bu olay, ve olayları arasında sıfır veya daha fazla kez oluşturulabilir `DeserializationStart` `DeserializationEnd` .</span><span class="sxs-lookup"><span data-stu-id="5d578-141">This event may be raised zero or more times between `DeserializationStart` and `DeserializationEnd` events.</span></span>

<span data-ttu-id="5d578-142">Bu olay bir bağımsız değişken içeren bir yük içerir.</span><span class="sxs-lookup"><span data-stu-id="5d578-142">This event contains a payload with one argument.</span></span>

* <span data-ttu-id="5d578-143">`typeName` ( `string` ): Serisi kaldırılan türün derleme nitelikli adı (bkz <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> .).</span><span class="sxs-lookup"><span data-stu-id="5d578-143">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being deserialized.</span></span>

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a><span data-ttu-id="5d578-144">\[Gelişmiş \] bir bildirim alt kümesine abone olma</span><span class="sxs-lookup"><span data-stu-id="5d578-144">\[Advanced\] Subscribing to a subset of notifications</span></span>

<span data-ttu-id="5d578-145">Yalnızca bir bildirim alt kümesine abone olmak isteyen dinleyiciler, etkinleştirilecek anahtar sözcükleri seçebilir.</span><span class="sxs-lookup"><span data-stu-id="5d578-145">Listeners who wish to subscribe to only a subset of notifications can choose which keywords to enable.</span></span>

* <span data-ttu-id="5d578-146">`Serialization` = `(EventKeywords)1`: `SerializationStart` , `SerializationEnd` Ve `SerializingObject` olaylarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="5d578-146">`Serialization` = `(EventKeywords)1`: Raises the `SerializationStart`, `SerializationEnd`, and `SerializingObject` events.</span></span>
* <span data-ttu-id="5d578-147">`Deserialization` = `(EventKeywords)2`: `DeserializationStart` , `DeserializationEnd` Ve `DeserializingObject` olaylarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="5d578-147">`Deserialization` = `(EventKeywords)2`: Raises the `DeserializationStart`, `DeserializationEnd`, and `DeserializingObject` events.</span></span>

<span data-ttu-id="5d578-148">Kayıt sırasında anahtar sözcük filtresi sağlanmazsa `EventListener` , tüm olaylar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d578-148">If no keyword filters are provided during `EventListener` registration, all events are raised.</span></span>

<span data-ttu-id="5d578-149">Daha fazla bilgi için bkz. <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d578-149">For more information, see <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span></span>

## <a name="sample-code"></a><span data-ttu-id="5d578-150">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="5d578-150">Sample code</span></span>

<span data-ttu-id="5d578-151">Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="5d578-151">The following code:</span></span>

- <span data-ttu-id="5d578-152">`EventListener`öğesine yazan bir türetilmiş tür oluşturur `System.Console` ,</span><span class="sxs-lookup"><span data-stu-id="5d578-152">creates an `EventListener`-derived type that writes to `System.Console`,</span></span>
- <span data-ttu-id="5d578-153">Bu dinleyicinin tarafından `BinaryFormatter` üretilen bildirimlere abone olur,</span><span class="sxs-lookup"><span data-stu-id="5d578-153">subscribes that listener to `BinaryFormatter`-produced notifications,</span></span>
- <span data-ttu-id="5d578-154">ve kullanarak basit bir nesne grafiğinin serileştirmesi ve çıkarılması `BinaryFormatter`</span><span class="sxs-lookup"><span data-stu-id="5d578-154">serializes and deserializes a simple object graph using `BinaryFormatter`, and</span></span>
- <span data-ttu-id="5d578-155">Yükseltilen olayları analiz eder.</span><span class="sxs-lookup"><span data-stu-id="5d578-155">analyzes the events that have been raised.</span></span>

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

<span data-ttu-id="5d578-156">Yukarıdaki kod, aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="5d578-156">The preceding code produces output similar to the following example:</span></span>

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

<span data-ttu-id="5d578-157">Bu örnekte, `EventListener` serileştirmenin başladığı konsol tabanlı Günlükler, `Person` ve örnekleri `Book` serileştirilir ve ardından serileştirme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="5d578-157">In this sample, the console-based `EventListener` logs that serialization starts, instances of `Person` and `Book` are serialized, and then serialization completes.</span></span> <span data-ttu-id="5d578-158">Benzer şekilde, seri durumdan çıkarma başladıktan sonra, `Person` ve örnekleri `Book` seri durumdan çıkarıldıktan sonra işlem tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="5d578-158">Similarly, once deserialization has started, instances of `Person` and `Book` are deserialized, and then deserialization completes.</span></span>

<span data-ttu-id="5d578-159">Daha sonra uygulama, `Person` nesnenin aslında seri hale getirme ve doğru şekilde serileştirildiğini göstermek için seri durumdan çıkarılan ' de yer alan değerleri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5d578-159">The app then prints the values contained in the deserialized `Person` to demonstrate that the object did in fact serialize and deserialize properly.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d578-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d578-160">See also</span></span>

<span data-ttu-id="5d578-161">Tabanlı bildirimleri almak için kullanma hakkında daha fazla bilgi için `EventListener` `EventSource` , [ `EventListener` sınıfına](xref:System.Diagnostics.Tracing.EventListener)bakın.</span><span class="sxs-lookup"><span data-stu-id="5d578-161">For more information on using `EventListener` to receive `EventSource`-based notifications, see [the `EventListener` class](xref:System.Diagnostics.Tracing.EventListener).</span></span>
