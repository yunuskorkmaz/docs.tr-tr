---
title: 'Son değişiklik: genel olmayan, parametresiz oluşturucular seri durumundan çıkarma için kullanılmaz'
description: .NET 5 ' teki, genel olmayan ve parametresiz oluşturucuların artık JsonSerializer ile serisini kaldırma için kullanılmayan Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 9781061fa89eb3bffb53a4f08bacbd88f3bc9265
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256276"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="1ff6c-103">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="1ff6c-103">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="1ff6c-104">Tüm desteklenen hedef çerçeve adları (TFMs) genelinde tutarlılık için, genel olmayan ve parametresiz oluşturucular, varsayılan olarak ile seri durumdan çıkarma için artık kullanılmamaktadır <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="1ff6c-104">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

## <a name="change-description"></a><span data-ttu-id="1ff6c-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1ff6c-105">Change description</span></span>

<span data-ttu-id="1ff6c-106">.NET Standard 2,0 ve üstünü destekleyen [ NuGet paketlerindeki](https://www.nuget.org/packages/System.Text.Json/) tek başınaSystem.Text.Js, yani 4.6.0-4.7.2 sürümleri, .net Core 3,0 ve 3,1 yerleşik davranışıyla tutarsız şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-106">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="1ff6c-107">.NET Core 3. x, iç ve özel oluşturucular seri durumundan çıkarma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-107">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="1ff6c-108">Tek başına paketlerde ortak olmayan oluşturuculara izin verilmez ve <xref:System.MissingMethodException> Public, parametresiz Oluşturucu tanımlanmadığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-108">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="1ff6c-109">.NET 5 ve ' den itibaren, NuGet paketi 5.0.0 üzerinde System.Text.Js, bu davranış NuGet paketi ve yerleşik API 'Ler arasında tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-109">Starting with .NET 5 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="1ff6c-110">Parametresiz oluşturucular da dahil olmak üzere genel olmayan oluşturucular varsayılan olarak serileştirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-110">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="1ff6c-111">Serileştirici, seri durumdan çıkarmak için aşağıdaki oluşturuculardan birini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1ff6c-111">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="1ff6c-112">Ortak Oluşturucu ile açıklama eklenir <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1ff6c-112">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="1ff6c-113">Ortak parametresiz Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-113">Public parameterless constructor.</span></span>
- <span data-ttu-id="1ff6c-114">Ortak parametreli Oluşturucu (tek ortak Oluşturucu varsa).</span><span class="sxs-lookup"><span data-stu-id="1ff6c-114">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="1ff6c-115">Bu oluşturuculardan hiçbiri kullanılabilir değilse, <xref:System.NotSupportedException> türün serisini kaldırma girişiminde bulunursa bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-115">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1ff6c-116">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1ff6c-116">Version introduced</span></span>

<span data-ttu-id="1ff6c-117">5.0</span><span class="sxs-lookup"><span data-stu-id="1ff6c-117">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="1ff6c-118">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1ff6c-118">Reason for change</span></span>

- <span data-ttu-id="1ff6c-119"><xref:System.Text.Json?displayProperty=fullName>(.NET Core 3,0 ve üzeri sürümleri ve .NET Standard 2,0) için derleme yapan tüm hedef çerçeve adları (TFMs) arasında tutarlı davranışı zorlamak için</span><span class="sxs-lookup"><span data-stu-id="1ff6c-119">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="1ff6c-120">Çünkü bir <xref:System.Text.Json.JsonSerializer> türün bir Oluşturucu, özellik veya alan gibi genel olmayan yüzey alanını çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-120">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1ff6c-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1ff6c-121">Recommended action</span></span>

- <span data-ttu-id="1ff6c-122">Türü sahibiyseniz ve mümkünse, parametresiz oluşturucuyu herkese açık hale getirin.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-122">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="1ff6c-123">Aksi takdirde, <xref:System.Text.Json.Serialization.JsonConverter%601> türü için bir uygulayın ve serisini kaldırma davranışını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-123">Otherwise, implement a <xref:System.Text.Json.Serialization.JsonConverter%601> for the type and control the deserialization behavior.</span></span> <span data-ttu-id="1ff6c-124"><xref:System.Text.Json.Serialization.JsonConverter%601>Söz konusu senaryoya yönelik C# erişilebilirlik kuralları buna izin verirseniz, bir uygulamadan ortak olmayan bir Oluşturucu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ff6c-124">You can call a non-public constructor from a <xref:System.Text.Json.Serialization.JsonConverter%601> implementation if C# accessibility rules for that scenario allow it.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1ff6c-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1ff6c-125">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
