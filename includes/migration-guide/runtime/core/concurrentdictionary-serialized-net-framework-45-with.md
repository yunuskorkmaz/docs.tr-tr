---
ms.openlocfilehash: b7953aab434de3b081f22acc43cf6c4a00ac0742
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858443"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>.NET Framework 4.5 NetDataContractSerializer ile seri hale getirilmiş bir ConcurrentDictionary .NET Framework 4.5.1 veya 4.5.2 tarafından seri durumdan çıkarılamıyor

|   |   |
|---|---|
|Ayrıntılar|Tür, iç değişiklikler nedeniyle <xref:System.Collections.Concurrent.ConcurrentDictionary%602> .NET Framework 4.5 ile serileştirilmiş nesneler kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> .NET Framework 4.5.1 veya .NET Framework 4.5.2.Note seri durumdan çıkarılamıyor, bir yönü (taşıma .NET Framework ile seri hale getirme 4.5.x ve .NET Framework 4.5 ile seri durumdan çıkarılırken) çalışır. Benzer şekilde, tüm 4.x sürümler arası serileştirme ile .NET Framework 4.6.Serializing çalışır ve tek bir .NET Framework sürümü ile seri durumdan çıkarılırken etkilenmez.|
|Öneri|Seri hale getrime ve gerekiyorsa, bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> .NET Framework 4.5 ve .NET Framework 4.5.1/4.5.2 arasında alternatif bir seri hale getirici ister <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> seri hale getirici yerine kullanılmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Bu sorun .NET Framework 4.6 yönelik olduğundan, alternatif olarak, .NET Framework'ün bu sürümüne yükselterek çözülmesi.|
|`Scope`|Küçük|
|Version|4.5.1|
|Type|Çalışma zamanı|

