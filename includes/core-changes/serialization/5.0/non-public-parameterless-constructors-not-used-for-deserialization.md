---
ms.openlocfilehash: 3692848a0cbd4bbbe3c7bb4d2c22a2b19de732e4
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050487"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="127c6-101">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="127c6-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="127c6-102">Tüm desteklenen hedef çerçeve adları (TFMs) genelinde tutarlılık için, genel olmayan ve parametresiz oluşturucular, varsayılan olarak ile seri durumdan çıkarma için artık kullanılmamaktadır <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="127c6-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="127c6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="127c6-103">Change description</span></span>

<span data-ttu-id="127c6-104">.NET Standard 2,0 ve üstünü destekleyen [ NuGet paketlerindeki](https://www.nuget.org/packages/System.Text.Json/) tek başınaSystem.Text.Js, yani 4.6.0-4.7.2 sürümleri, .net Core 3,0 ve 3,1 yerleşik davranışıyla tutarsız şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="127c6-104">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="127c6-105">.NET Core 3. x, iç ve özel oluşturucular seri durumundan çıkarma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="127c6-105">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="127c6-106">Tek başına paketlerde ortak olmayan oluşturuculara izin verilmez ve <xref:System.MissingMethodException> Public, parametresiz Oluşturucu tanımlanmadığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="127c6-106">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="127c6-107">.NET 5,0 ve System.Text.Js'den başlayarak, bu davranış NuGet paketi ve yerleşik API 'Ler arasında tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="127c6-107">Starting with .NET 5.0 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="127c6-108">Parametresiz oluşturucular da dahil olmak üzere genel olmayan oluşturucular varsayılan olarak serileştirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="127c6-108">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="127c6-109">Serileştirici, seri durumdan çıkarmak için aşağıdaki oluşturuculardan birini kullanır:</span><span class="sxs-lookup"><span data-stu-id="127c6-109">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="127c6-110">Ortak Oluşturucu ile açıklama eklenir <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="127c6-110">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="127c6-111">Ortak parametresiz Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="127c6-111">Public parameterless constructor.</span></span>
- <span data-ttu-id="127c6-112">Ortak parametreli Oluşturucu (tek ortak Oluşturucu varsa).</span><span class="sxs-lookup"><span data-stu-id="127c6-112">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="127c6-113">Bu oluşturuculardan hiçbiri kullanılabilir değilse, <xref:System.NotSupportedException> türün serisini kaldırma girişiminde bulunursa bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="127c6-113">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="127c6-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="127c6-114">Version introduced</span></span>

<span data-ttu-id="127c6-115">5.0</span><span class="sxs-lookup"><span data-stu-id="127c6-115">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="127c6-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="127c6-116">Reason for change</span></span>

- <span data-ttu-id="127c6-117"><xref:System.Text.Json?displayProperty=fullName>(.NET Core 3,0 ve üzeri sürümleri ve .NET Standard 2,0) için derleme yapan tüm hedef çerçeve adları (TFMs) arasında tutarlı davranışı zorlamak için</span><span class="sxs-lookup"><span data-stu-id="127c6-117">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="127c6-118">Çünkü bir <xref:System.Text.Json.JsonSerializer> türün bir Oluşturucu, özellik veya alan gibi genel olmayan yüzey alanını çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="127c6-118">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="127c6-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="127c6-119">Recommended action</span></span>

- <span data-ttu-id="127c6-120">Türü sahibiyseniz ve mümkünse, parametresiz oluşturucuyu herkese açık hale getirin.</span><span class="sxs-lookup"><span data-stu-id="127c6-120">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="127c6-121">Aksi takdirde, `JsonConverter<T>` türü için bir uygulayın ve serisini kaldırma davranışını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="127c6-121">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="127c6-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="127c6-122">Category</span></span>

<span data-ttu-id="127c6-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="127c6-123">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="127c6-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="127c6-124">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
