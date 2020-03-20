---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858443"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>.NETFramework 4.5'te netdatacontractSerializer ile seri hale getirilen Eşzamanlı Bir Sözlük .NET Framework 4.5.1 veya 4.5.2 ile deserialized olamaz

|   |   |
|---|---|
|Ayrıntılar|Türündeki iç değişiklikler nedeniyle <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ,NET Framework 4.5 ile seri hale <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> getirilen nesneler .NET Framework 4.5.1 veya .NET Framework 4.5.2.Note'ta diğer yönde hareket eden (.NET Framework 4.5.x ile serileştirme ve .NET Framework 4.5 ile serileştirme) kullanılarak serihale getirilemez. Benzer şekilde, 4.x çapraz sürüm serileştirme ,NET Framework 4.6.Serializing ve .NET Framework tek bir sürümü ile deserializing ile çalışır etkilenmez.|
|Öneri|.NET Framework 4.5 ve .NET Framework 4.5.1/4.5.2 arasındaki <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> bir seriyi serihale getirmek ve deserialize etmek gerekiyorsa, .net framework 4.5.1/4.5.2 gibi <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> alternatif bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serileştirici yerine <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>kullanılmalıdır. Alternatif olarak, bu sorun .NET Framework 4.6'da ele alındığından, .NET Framework'ün bu sürümüne yükseltilerek çözülebilir.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|
