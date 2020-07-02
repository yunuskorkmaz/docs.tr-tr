---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620658"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter, Hashtable ve benzer sıralı koleksiyon nesneleri serisini kaldıramıyor

#### <a name="details"></a>Ayrıntılar

, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> Bir .NET Framework sürümünde seri hale getirilen nesnelerin farklı bir sürüm altında başarıyla seri durumdan çıkaracağının garantisi yoktur. Özellikle, bazı sıralı Koleksiyonlar (gibi <xref:System.Collections.Hashtable?displayProperty=fullName> ), bu türlerin nesnelerinin .NET Framework 4,5 ile serileştirildiği .NET Framework 4,0 ile seri durumdan çıkaramamaları için 4,0 ve 4,5 arasında Üyeler ekledi. Serileştirilmiş verilerin hem serileştirildiği hem de aynı .NET Framework sürümüyle seri durumdan çıkarılmışsa, hiçbir sorunun gerçekleşmediğini unutmayın.

#### <a name="suggestion"></a>Öneri

<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>serileştirme, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> .NET Framework değişiklikler için serileştirme ile değiştirilmelidir veya dayanıklı <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> olmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
