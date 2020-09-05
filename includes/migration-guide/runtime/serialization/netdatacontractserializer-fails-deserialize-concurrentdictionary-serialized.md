---
ms.openlocfilehash: 6c120f155660863ce5ae3cf5bd81ea858a68ef8d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496990"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="69379-101">NetDataContractSerializer, farklı bir .NET sürümü ile serileştirilmiş bir ConcurrentDictionary serisini kaldıramıyor</span><span class="sxs-lookup"><span data-stu-id="69379-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="69379-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="69379-102">Details</span></span>

<span data-ttu-id="69379-103">Tasarıma göre <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> yalnızca serileştirme ve seri durumdan çıkarma, aynı CLR türlerini paylaşıyorsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69379-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="69379-104">Bu nedenle, .NET Framework bir sürümü ile seri hale getirilen bir nesnenin, farklı bir sürüm tarafından seri durumdan çıkarılacağından garanti edilmez.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="69379-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="69379-105">, .NET Framework 4,5 veya daha önceki bir sürümü ile serileştirildiğinde ve .NET Framework 4.5.1 veya sonraki bir sürümüyle serisi kaldırıldığında doğru bir şekilde seri durumdan çıkarılamadı bilinen bir türdür.</span><span class="sxs-lookup"><span data-stu-id="69379-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69379-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="69379-106">Suggestion</span></span>

<span data-ttu-id="69379-107">Bu sorun için bir dizi olası iş arounds vardır:</span><span class="sxs-lookup"><span data-stu-id="69379-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="69379-108">Serileştirme bilgisayarı, .NET Framework 4.5.1 kullanmak üzere yükseltin.</span><span class="sxs-lookup"><span data-stu-id="69379-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="69379-109"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>Bunun yerine kullanın <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> çünkü bu, hem serileştirilmede hem de seri durumdan çıkarılırken tam olarak aynı CLR türlerini beklemez.</span><span class="sxs-lookup"><span data-stu-id="69379-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="69379-110"><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> Bu belirli 4,5-4.5.1 kesmesini sergilemediğinden yerine kullanın &gt; .</span><span class="sxs-lookup"><span data-stu-id="69379-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="69379-111">Name</span><span class="sxs-lookup"><span data-stu-id="69379-111">Name</span></span>    | <span data-ttu-id="69379-112">Değer</span><span class="sxs-lookup"><span data-stu-id="69379-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69379-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69379-113">Scope</span></span>   |<span data-ttu-id="69379-114">İkincil</span><span class="sxs-lookup"><span data-stu-id="69379-114">Minor</span></span>|
|<span data-ttu-id="69379-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="69379-115">Version</span></span>|<span data-ttu-id="69379-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="69379-116">4.5.1</span></span>|
|<span data-ttu-id="69379-117">Tür</span><span class="sxs-lookup"><span data-stu-id="69379-117">Type</span></span>|<span data-ttu-id="69379-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="69379-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="69379-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="69379-119">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)`

-->
