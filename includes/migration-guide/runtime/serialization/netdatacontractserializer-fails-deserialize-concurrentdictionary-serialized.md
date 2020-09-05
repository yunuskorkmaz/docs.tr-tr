---
ms.openlocfilehash: 6c120f155660863ce5ae3cf5bd81ea858a68ef8d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496990"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer, farklı bir .NET sürümü ile serileştirilmiş bir ConcurrentDictionary serisini kaldıramıyor

#### <a name="details"></a>Ayrıntılar

Tasarıma göre <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> yalnızca serileştirme ve seri durumdan çıkarma, aynı CLR türlerini paylaşıyorsa kullanılabilir. Bu nedenle, .NET Framework bir sürümü ile seri hale getirilen bir nesnenin, farklı bir sürüm tarafından seri durumdan çıkarılacağından garanti edilmez.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> , .NET Framework 4,5 veya daha önceki bir sürümü ile serileştirildiğinde ve .NET Framework 4.5.1 veya sonraki bir sürümüyle serisi kaldırıldığında doğru bir şekilde seri durumdan çıkarılamadı bilinen bir türdür.

#### <a name="suggestion"></a>Öneri

Bu sorun için bir dizi olası iş arounds vardır:<ul><li>Serileştirme bilgisayarı, .NET Framework 4.5.1 kullanmak üzere yükseltin.</li><li><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>Bunun yerine kullanın <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> çünkü bu, hem serileştirilmede hem de seri durumdan çıkarılırken tam olarak aynı CLR türlerini beklemez.</li><li><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> Bu belirli 4,5-4.5.1 kesmesini sergilemediğinden yerine kullanın &gt; .</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)`

-->
