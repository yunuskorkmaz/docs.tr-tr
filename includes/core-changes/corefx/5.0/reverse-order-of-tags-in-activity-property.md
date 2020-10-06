---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756122"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="6d1bb-101">Etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir</span><span class="sxs-lookup"><span data-stu-id="6d1bb-101">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="6d1bb-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Artık öğeleri eklendiği sıraya göre listede depolar, diğer bir deyişle, eklenen ilk öğe listede ilk olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="6d1bb-103">Bu değişiklik, [Opentelemetri öznitelikleri belirtimiyle](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)eşleşecek şekilde yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-103">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

#### <a name="change-description"></a><span data-ttu-id="6d1bb-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6d1bb-104">Change description</span></span>

<span data-ttu-id="6d1bb-105">Önceki .NET sürümlerinde, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> öğeleri eklendikleri ters sırada depolar.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-105">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="6d1bb-106">Diğer bir deyişle, eklenen ilk öğe listenin en son öğesidir.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-106">That is, the first item added is last in the list.</span></span> <span data-ttu-id="6d1bb-107">.NET 5,0 ' den başlayarak, öğelerin sırası tersine çevrilir ve eklenen ilk öğe her zaman listede ilk olarak olur.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-107">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6d1bb-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6d1bb-108">Version introduced</span></span>

<span data-ttu-id="6d1bb-109">5.0</span><span class="sxs-lookup"><span data-stu-id="6d1bb-109">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6d1bb-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6d1bb-110">Recommended action</span></span>

<span data-ttu-id="6d1bb-111">Uygulamanızda <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste sırası bağımlılığı varsa ve .net 5,0 veya sonraki bir sürüme yükseltiyorsanız, kodunuzun bu bölümünü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d1bb-111">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

#### <a name="category"></a><span data-ttu-id="6d1bb-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="6d1bb-112">Category</span></span>

<span data-ttu-id="6d1bb-113">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="6d1bb-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6d1bb-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6d1bb-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
