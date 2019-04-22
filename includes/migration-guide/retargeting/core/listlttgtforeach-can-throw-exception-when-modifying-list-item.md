---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774407"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="ec349-101">Liste\<T >. ForEach liste öğesi değiştirirken özel durumu oluşturabilecek</span><span class="sxs-lookup"><span data-stu-id="ec349-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ec349-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ec349-102">Details</span></span>|<span data-ttu-id="ec349-103">.NET Framework 4.5 sürümünden başlayarak, çağrı koleksiyonundaki bir öğe değiştirilirse bir <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> numaralandırıcısı bir <xref:System.InvalidOperationException?displayProperty=name> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec349-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="ec349-104">Daha önceden, bu bir özel durum oluşturmuyordu ancak yarış durumlarına neden olabiliyordu.</span><span class="sxs-lookup"><span data-stu-id="ec349-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="ec349-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="ec349-105">Suggestion</span></span>|<span data-ttu-id="ec349-106">İdeal olarak, bu hiçbir zaman güvenli bir işlem olmadığından kod, liste öğelerini listelerken, listeleri değiştirmeyecek şekilde düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec349-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="ec349-107">Bununla birlikte, bir uygulama önceki davranışa dönmek için .NET Framework 4.0’ı hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ec349-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="ec349-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ec349-108">Scope</span></span>|<span data-ttu-id="ec349-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="ec349-109">Edge</span></span>|
|<span data-ttu-id="ec349-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ec349-110">Version</span></span>|<span data-ttu-id="ec349-111">4,5</span><span class="sxs-lookup"><span data-stu-id="ec349-111">4.5</span></span>|
|<span data-ttu-id="ec349-112">Tür</span><span class="sxs-lookup"><span data-stu-id="ec349-112">Type</span></span>|<span data-ttu-id="ec349-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ec349-113">Retargeting</span></span>|
|<span data-ttu-id="ec349-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ec349-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
