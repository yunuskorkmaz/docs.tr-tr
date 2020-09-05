---
ms.openlocfilehash: 71cc7119710a2b381626dd9cf4ab66265eb3deba
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497143"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="93c54-101">SoapFormatter, Hashtable ve benzer sıralı koleksiyon nesneleri serisini kaldıramıyor</span><span class="sxs-lookup"><span data-stu-id="93c54-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="93c54-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="93c54-102">Details</span></span>

<span data-ttu-id="93c54-103">, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> Bir .NET Framework sürümünde seri hale getirilen nesnelerin farklı bir sürüm altında başarıyla seri durumdan çıkaracağının garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="93c54-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="93c54-104">Özellikle, bazı sıralı Koleksiyonlar (gibi <xref:System.Collections.Hashtable?displayProperty=fullName> ), bu türlerin nesnelerinin .NET Framework 4,5 ile serileştirildiği .NET Framework 4,0 ile seri durumdan çıkaramamaları için 4,0 ve 4,5 arasında Üyeler ekledi.</span><span class="sxs-lookup"><span data-stu-id="93c54-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="93c54-105">Serileştirilmiş verilerin hem serileştirildiği hem de aynı .NET Framework sürümüyle seri durumdan çıkarılmışsa, hiçbir sorunun gerçekleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="93c54-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="93c54-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="93c54-106">Suggestion</span></span>

<span data-ttu-id="93c54-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serileştirme, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> .NET Framework değişiklikler için serileştirme ile değiştirilmelidir veya dayanıklı <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93c54-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="93c54-108">Name</span><span class="sxs-lookup"><span data-stu-id="93c54-108">Name</span></span>    | <span data-ttu-id="93c54-109">Değer</span><span class="sxs-lookup"><span data-stu-id="93c54-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="93c54-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="93c54-110">Scope</span></span>   |<span data-ttu-id="93c54-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="93c54-111">Minor</span></span>|
|<span data-ttu-id="93c54-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="93c54-112">Version</span></span>|<span data-ttu-id="93c54-113">4,5</span><span class="sxs-lookup"><span data-stu-id="93c54-113">4.5</span></span>|
|<span data-ttu-id="93c54-114">Tür</span><span class="sxs-lookup"><span data-stu-id="93c54-114">Type</span></span>|<span data-ttu-id="93c54-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="93c54-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="93c54-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="93c54-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
