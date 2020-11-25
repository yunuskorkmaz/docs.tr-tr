---
title: 'Son değişiklik: etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir'
description: .NET 5,0 önemli .NET kitaplıklarında etkinlik. Etiketler eklendiği sıraya göre öğeleri artık depolar.
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761497"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="5ea3f-103">Etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir</span><span class="sxs-lookup"><span data-stu-id="5ea3f-103">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="5ea3f-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Artık öğeleri eklendiği sıraya göre listede depolar, diğer bir deyişle, eklenen ilk öğe listede ilk olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="5ea3f-105">Bu değişiklik, [Opentelemetri öznitelikleri belirtimiyle](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)eşleşecek şekilde yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-105">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

## <a name="change-description"></a><span data-ttu-id="5ea3f-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5ea3f-106">Change description</span></span>

<span data-ttu-id="5ea3f-107">Önceki .NET sürümlerinde, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> öğeleri eklendikleri ters sırada depolar.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-107">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="5ea3f-108">Diğer bir deyişle, eklenen ilk öğe listenin en son öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-108">That is, the first item added is last in the list.</span></span> <span data-ttu-id="5ea3f-109">.NET 5,0 ' den başlayarak, öğelerin sırası tersine çevrilir ve eklenen ilk öğe her zaman listede ilk olarak olur.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-109">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5ea3f-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5ea3f-110">Version introduced</span></span>

<span data-ttu-id="5ea3f-111">5.0</span><span class="sxs-lookup"><span data-stu-id="5ea3f-111">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5ea3f-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5ea3f-112">Recommended action</span></span>

<span data-ttu-id="5ea3f-113">Uygulamanızda <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste sırası bağımlılığı varsa ve .net 5,0 veya sonraki bir sürüme yükseltiyorsanız, kodunuzun bu bölümünü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ea3f-113">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5ea3f-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5ea3f-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
