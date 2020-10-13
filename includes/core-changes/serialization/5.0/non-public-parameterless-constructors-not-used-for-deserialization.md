---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997721"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="76696-101">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="76696-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="76696-102">Tüm desteklenen hedef çerçeve adları (TFMs) genelinde tutarlılık için, genel olmayan ve parametresiz oluşturucular, varsayılan olarak ile seri durumdan çıkarma için artık kullanılmamaktadır <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="76696-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="76696-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="76696-103">Change description</span></span>

<span data-ttu-id="76696-104">.NET Core 3,0 ve 3,1 ' de iç ve özel oluşturucular seri durumundan çıkarma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76696-104">On .NET Core 3.0 and 3.1, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="76696-105">.NET Standard 2,0 ve 2,1 ' de iç ve özel oluşturuculara izin verilmez ve <xref:System.MissingMethodException> hiçbir ortak, parametresiz Oluşturucu tanımlanmadığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76696-105">On .NET Standard 2.0 and 2.1, internal and private constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="76696-106">.NET 5,0 ' den başlayarak, parametresiz oluşturucular da dahil olmak üzere genel olmayan oluşturucular varsayılan olarak serileştirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="76696-106">Starting in .NET 5.0, non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="76696-107">Serileştirici, seri durumdan çıkarmak için aşağıdaki oluşturuculardan birini kullanır:</span><span class="sxs-lookup"><span data-stu-id="76696-107">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="76696-108">Ortak Oluşturucu ile açıklama eklenir <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="76696-108">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="76696-109">Ortak parametresiz Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="76696-109">Public parameterless constructor.</span></span>
- <span data-ttu-id="76696-110">Ortak parametreli Oluşturucu (tek ortak Oluşturucu varsa).</span><span class="sxs-lookup"><span data-stu-id="76696-110">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="76696-111">Bu oluşturuculardan hiçbiri kullanılabilir değilse, <xref:System.NotSupportedException> türün serisini kaldırma girişiminde bulunursa bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76696-111">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="76696-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="76696-112">Version introduced</span></span>

<span data-ttu-id="76696-113">5.0</span><span class="sxs-lookup"><span data-stu-id="76696-113">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="76696-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="76696-114">Reason for change</span></span>

- <span data-ttu-id="76696-115"><xref:System.Text.Json?displayProperty=fullName>(.NET Core 3,0 ve sonraki sürümleri ve .NET Standard 2,0 ve 2,1) için derleme yapan tüm hedef çerçeve adları (TFMs) arasında tutarlı davranışları zorlamak için</span><span class="sxs-lookup"><span data-stu-id="76696-115">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions, and .NET Standard 2.0 and 2.1)</span></span>
- <span data-ttu-id="76696-116">Çünkü bir <xref:System.Text.Json.JsonSerializer> türün bir Oluşturucu, özellik veya alan gibi genel olmayan yüzey alanını çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="76696-116">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="76696-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="76696-117">Recommended action</span></span>

- <span data-ttu-id="76696-118">Türü sahibiyseniz ve mümkünse, parametresiz oluşturucuyu herkese açık hale getirin.</span><span class="sxs-lookup"><span data-stu-id="76696-118">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="76696-119">Aksi takdirde, `JsonConverter<T>` türü için bir uygulayın ve serisini kaldırma davranışını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="76696-119">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="76696-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="76696-120">Category</span></span>

<span data-ttu-id="76696-121">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="76696-121">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="76696-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="76696-122">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
