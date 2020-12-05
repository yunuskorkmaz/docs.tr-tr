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
# <a name="binaryformatter-event-source"></a>BinaryFormatter olay kaynağı

.NET 5,0 ' den itibaren, bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Diagnostics.Tracing.EventSource> nesne serileştirme veya serisini kaldırma gerçekleşirken görünürlük sağlayan yerleşik bir derleme içerir. Uygulamalar, <xref:System.Diagnostics.Tracing.EventListener> Bu bildirimleri dinlemek ve günlüğe kaydetmek için türetilmiş türleri kullanabilir.

Bu işlevsellik bir veya için bir alternatif değildir <xref:System.Runtime.Serialization.SerializationBinder> <xref:System.Runtime.Serialization.ISerializationSurrogate> ve serileştirilmiş veya seri durumdan çıkarılan verileri değiştirmek için kullanılamaz. Bunun yerine, bu olay sistemi seri hale getirilen veya seri durumdan çıkarılan türlerin içgörüleri sağlamak üzere tasarlanmıştır. Ayrıca `BinaryFormatter` , altyapıda, üçüncü taraf kitaplık kodundan kaynaklanan çağrılar gibi istenmeyen çağrıları algılamak için de kullanılabilir.

## <a name="description-of-events"></a>Olayların açıklaması

`BinaryFormatter`Olay kaynağı iyi bilinen ada sahiptir `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` . Dinleyiciler 6 olaya abone olabilir.

### <a name="serializationstart-event-id--10"></a>SerializationStart olayı (ID = `10` )

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>Çağrıldığında ve serileştirme işlemini başlatmışsa tetiklenir. Bu olay `SerializationEnd` olayla eşleştirilmiş. `SerializationStart`Bir nesne `BinaryFormatter.Serialize` kendi serileştirme yordamı içinde çağrılırsa, olay yinelemeli olarak çağrılabilir.

Bu olay yük içermiyor.

### <a name="serializationend-event-id--11"></a>SerializationEnd olayı (kimlik = `11` )

`BinaryFormatter.Serialize`, İşini tamamladığında tetiklenir. Her bir oluşumu, `SerializationEnd` son eşlenmemiş etkinliğin tamamlanmasını gösterir `SerializationStart` .

Bu olay yük içermiyor.

### <a name="serializingobject-event-id--12"></a>SerializingObject olayı (ID = `12` )

`BinaryFormatter.Serialize`Temel olmayan bir türü serileştirme işleminde olduğunda tetiklenir. `BinaryFormatter`Altyapı özel-belirli türleri ( `string` ve gibi `int` ) ve bu türlere rastlarınca bu olayı oluşturmaz. Bu olay, Kullanıcı tanımlı türler ve yerel olarak anlayan diğer türler için oluşturulur `BinaryFormatter` .

Bu olay, ve olayları arasında sıfır veya daha fazla kez oluşturulabilir `SerializationStart` `SerializationEnd` .

Bu olay bir bağımsız değişken içeren bir yük içerir:

* `typeName` ( `string` ): <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> Serileştirilmekte olan türün derleme nitelikli adı (bkz.).

### <a name="deserializationstart-event-id--20"></a>DeserializationStart olayı (ID = `20` )

Çağrıldığında oluşturulur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> ve serisini kaldırma işlemini başlattı. Bu olay `DeserializationEnd` olayla eşleştirilmiş. `DeserializationStart`Bir nesne `BinaryFormatter.Deserialize` kendi seri kaldırma yordamı içinde çağrılırsa, olay yinelemeli olarak çağrılabilir.

Bu olay yük içermiyor.

### <a name="deserializationend-event-id--21"></a>DeserializationEnd olayı (ID = `21` )

`BinaryFormatter.Deserialize`, İşini tamamladığında tetiklenir. Her bir oluşumu, `DeserializationEnd` son eşlenmemiş etkinliğin tamamlanmasını gösterir `DeserializationStart` .

Bu olay yük içermiyor.

### <a name="deserializingobject-event-id--22"></a>DeserializingObject olayı (ID = `22` )

`BinaryFormatter.Deserialize`İlkel olmayan bir türün serisini kaldırma işleminde olduğunda tetiklenir. `BinaryFormatter`Altyapı özel-belirli türleri ( `string` ve gibi `int` ) ve bu türlere rastlarınca bu olayı oluşturmaz. Bu olay, Kullanıcı tanımlı türler ve yerel olarak anlayan diğer türler için oluşturulur `BinaryFormatter` .

Bu olay, ve olayları arasında sıfır veya daha fazla kez oluşturulabilir `DeserializationStart` `DeserializationEnd` .

Bu olay bir bağımsız değişken içeren bir yük içerir.

* `typeName` ( `string` ): Serisi kaldırılan türün derleme nitelikli adı (bkz <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> .).

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a>\[Gelişmiş \] bir bildirim alt kümesine abone olma

Yalnızca bir bildirim alt kümesine abone olmak isteyen dinleyiciler, etkinleştirilecek anahtar sözcükleri seçebilir.

* `Serialization` = `(EventKeywords)1`: `SerializationStart` , `SerializationEnd` Ve `SerializingObject` olaylarını başlatır.
* `Deserialization` = `(EventKeywords)2`: `DeserializationStart` , `DeserializationEnd` Ve `DeserializingObject` olaylarını başlatır.

Kayıt sırasında anahtar sözcük filtresi sağlanmazsa `EventListener` , tüm olaylar oluşturulur.

Daha fazla bilgi için bkz. <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.

## <a name="sample-code"></a>Örnek kod

Aşağıdaki kod:

- `EventListener`öğesine yazan bir türetilmiş tür oluşturur `System.Console` ,
- Bu dinleyicinin tarafından `BinaryFormatter` üretilen bildirimlere abone olur,
- ve kullanarak basit bir nesne grafiğinin serileştirmesi ve çıkarılması `BinaryFormatter`
- Yükseltilen olayları analiz eder.

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

Yukarıdaki kod, aşağıdaki örneğe benzer bir çıktı üretir:

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

Bu örnekte, `EventListener` serileştirmenin başladığı konsol tabanlı Günlükler, `Person` ve örnekleri `Book` serileştirilir ve ardından serileştirme tamamlanır. Benzer şekilde, seri durumdan çıkarma başladıktan sonra, `Person` ve örnekleri `Book` seri durumdan çıkarıldıktan sonra işlem tamamlanır.

Daha sonra uygulama, `Person` nesnenin aslında seri hale getirme ve doğru şekilde serileştirildiğini göstermek için seri durumdan çıkarılan ' de yer alan değerleri yazdırır.

## <a name="see-also"></a>Ayrıca bkz.

Tabanlı bildirimleri almak için kullanma hakkında daha fazla bilgi için `EventListener` `EventSource` , [ `EventListener` sınıfına](xref:System.Diagnostics.Tracing.EventListener)bakın.
