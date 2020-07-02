---
ms.openlocfilehash: ae0f68a19d6eae53998d61e924cfef3aaaec1784
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620568"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>NetDataContractSerializer ile .NET Framework 4,5 ' de seri hale getirilen bir ConcurrentDictionary, .NET Framework 4.5.1 veya 4.5.2 tarafından seri durumdan çıkarılamıyor

#### <a name="details"></a>Ayrıntılar

Türünde yapılan iç değişiklikler nedeniyle <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , kullanılarak 4,5 .NET Framework seri hale getirilen nesneler <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> .NET Framework 4.5.1 veya .NET Framework 4.5.2 içinde seri durumdan çıkarılamıyor. diğer yönde (.NET Framework 4.5. x ile serileştirilmesi ve .NET Framework 4,5 ile serisini kaldırma) çalışmadığına emin olun. Benzer şekilde, tüm 4. x sürümler arası serileştirme .NET Framework 4.6 ile çalışır. .NET Framework tek bir sürümü ile serileştirilmesi ve seri durumdan çıkarma etkilenmez.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,5 ve .NET Framework 4.5.1/4.5.2 arasında bir seri hale getirmek ve seri durumdan çıkarmak gerekirse, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> seri hale getirici gibi alternatif bir serileştirici yerine kullanılmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> . Alternatif olarak, bu sorun .NET Framework 4,6 ' de giderildiği için .NET Framework sürümüne yükseltilerek çözülebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|
