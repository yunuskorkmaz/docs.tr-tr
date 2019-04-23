---
ms.openlocfilehash: 6ed7438a7f6e7710fcce03c8260a1360143f8d93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235823"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter Hashtable seri durumdan olamaz ve benzer sıralı koleksiyon nesneleri

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Nesneleri'nin altında bir .NET Framework sürümü seri hale getirilmiş garantisi başarıyla altında farklı bir sürüm serisini yapar. Özellikle, bazı koleksiyonlar sıralı (gibi <xref:System.Collections.Hashtable?displayProperty=name>) .NET Framework 4.5 ile seri hale, bu tür nesneler .NET Framework 4.0 ile seri durumdan çıkarılamıyor, üyeleri arasında 4.0 ve 4.5 eklendi. Serileştirilmiş veriler ise hem serileştirilmiş ve seri durumdan aynı .NET Framework sürümüyle sorun oluşacağını unutmayın.|
|Öneri|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Serileştirme yerine <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serileştirme veya <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> .NET Framework değişikliklere dayanıklı olmasını.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
