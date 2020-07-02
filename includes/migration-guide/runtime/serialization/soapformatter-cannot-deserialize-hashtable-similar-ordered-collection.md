---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620658"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="961d0-101">SoapFormatter, Hashtable ve benzer sıralı koleksiyon nesneleri serisini kaldıramıyor</span><span class="sxs-lookup"><span data-stu-id="961d0-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="961d0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="961d0-102">Details</span></span>

<span data-ttu-id="961d0-103">, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> Bir .NET Framework sürümünde seri hale getirilen nesnelerin farklı bir sürüm altında başarıyla seri durumdan çıkaracağının garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="961d0-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="961d0-104">Özellikle, bazı sıralı Koleksiyonlar (gibi <xref:System.Collections.Hashtable?displayProperty=fullName> ), bu türlerin nesnelerinin .NET Framework 4,5 ile serileştirildiği .NET Framework 4,0 ile seri durumdan çıkaramamaları için 4,0 ve 4,5 arasında Üyeler ekledi.</span><span class="sxs-lookup"><span data-stu-id="961d0-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="961d0-105">Serileştirilmiş verilerin hem serileştirildiği hem de aynı .NET Framework sürümüyle seri durumdan çıkarılmışsa, hiçbir sorunun gerçekleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="961d0-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="961d0-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="961d0-106">Suggestion</span></span>

<span data-ttu-id="961d0-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>serileştirme, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> .NET Framework değişiklikler için serileştirme ile değiştirilmelidir veya dayanıklı <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="961d0-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="961d0-108">Name</span><span class="sxs-lookup"><span data-stu-id="961d0-108">Name</span></span>    | <span data-ttu-id="961d0-109">Değer</span><span class="sxs-lookup"><span data-stu-id="961d0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="961d0-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="961d0-110">Scope</span></span>   |<span data-ttu-id="961d0-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="961d0-111">Minor</span></span>|
|<span data-ttu-id="961d0-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="961d0-112">Version</span></span>|<span data-ttu-id="961d0-113">4,5</span><span class="sxs-lookup"><span data-stu-id="961d0-113">4.5</span></span>|
|<span data-ttu-id="961d0-114">Tür</span><span class="sxs-lookup"><span data-stu-id="961d0-114">Type</span></span>|<span data-ttu-id="961d0-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="961d0-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="961d0-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="961d0-116">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
