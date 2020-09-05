---
ms.openlocfilehash: 450bfc56c99a3df9be71be2ef7df6e4e12d4ed76
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497107"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a><span data-ttu-id="9ea33-101">NetDataContractSerializer ile .NET Framework 4,5 ' de seri hale getirilen bir ConcurrentDictionary, .NET Framework 4.5.1 veya 4.5.2 tarafından seri durumdan çıkarılamıyor</span><span class="sxs-lookup"><span data-stu-id="9ea33-101">A ConcurrentDictionary serialized in .NET Framework 4.5 with NetDataContractSerializer cannot be deserialized by .NET Framework 4.5.1 or 4.5.2</span></span>

#### <a name="details"></a><span data-ttu-id="9ea33-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9ea33-102">Details</span></span>

<span data-ttu-id="9ea33-103">Türünde yapılan iç değişiklikler nedeniyle <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , kullanılarak 4,5 .NET Framework seri hale getirilen nesneler <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> .NET Framework 4.5.1 veya .NET Framework 4.5.2 içinde seri durumdan çıkarılamıyor. diğer yönde (.NET Framework 4.5. x ile serileştirilmesi ve .NET Framework 4,5 ile serisini kaldırma) çalışmadığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ea33-103">Due to internal changes to the type, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objects that are serialized with the .NET Framework 4.5 using the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> cannot be deserialized in the .NET Framework 4.5.1 or in the .NET Framework 4.5.2.Note that moving in the other direction (serializing with the .NET Framework 4.5.x and deserializing with the .NET Framework 4.5) works.</span></span> <span data-ttu-id="9ea33-104">Benzer şekilde, tüm 4. x sürümler arası serileştirme .NET Framework 4.6 ile çalışır. .NET Framework tek bir sürümü ile serileştirilmesi ve seri durumdan çıkarma etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="9ea33-104">Similarly, all 4.x cross-version serialization works with the .NET Framework 4.6.Serializing and deserializing with a single version of the .NET Framework is not affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9ea33-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9ea33-105">Suggestion</span></span>

<span data-ttu-id="9ea33-106">.NET Framework 4,5 ve .NET Framework 4.5.1/4.5.2 arasında bir seri hale getirmek ve seri durumdan çıkarmak gerekirse, <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> seri hale getirici gibi alternatif bir serileştirici yerine kullanılmalıdır <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> . Alternatif olarak, bu sorun .NET Framework 4,6 ' de giderildiği için .NET Framework sürümüne yükseltilerek çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="9ea33-106">If it is necessary to serialize and deserialize a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> between the .NET Framework 4.5 and .NET Framework 4.5.1/4.5.2, an alternate serializer like the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializer should be used instead of the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>.Alternatively, because this issue is addressed in the .NET Framework 4.6, it may be solved by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="9ea33-107">Name</span><span class="sxs-lookup"><span data-stu-id="9ea33-107">Name</span></span>    | <span data-ttu-id="9ea33-108">Değer</span><span class="sxs-lookup"><span data-stu-id="9ea33-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9ea33-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9ea33-109">Scope</span></span>   |<span data-ttu-id="9ea33-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="9ea33-110">Minor</span></span>|
|<span data-ttu-id="9ea33-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9ea33-111">Version</span></span>|<span data-ttu-id="9ea33-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="9ea33-112">4.5.1</span></span>|
|<span data-ttu-id="9ea33-113">Tür</span><span class="sxs-lookup"><span data-stu-id="9ea33-113">Type</span></span>|<span data-ttu-id="9ea33-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9ea33-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9ea33-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9ea33-115">Affected APIs</span></span>

<span data-ttu-id="9ea33-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="9ea33-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
