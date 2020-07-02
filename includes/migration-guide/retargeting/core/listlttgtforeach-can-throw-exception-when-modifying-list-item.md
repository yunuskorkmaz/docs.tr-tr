---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617287"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="7bd36-101">List&lt;T&gt;.ForEach, liste öğesi değiştirilirken özel durum oluşturabilir</span><span class="sxs-lookup"><span data-stu-id="7bd36-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="7bd36-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7bd36-102">Details</span></span>

<span data-ttu-id="7bd36-103">.NET Framework 4.5 sürümünden başlayarak, çağrı koleksiyonundaki bir öğe değiştirilirse bir <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> numaralandırıcısı bir <xref:System.InvalidOperationException?displayProperty=fullName> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bd36-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="7bd36-104">Daha önceden, bu bir özel durum oluşturmuyordu ancak yarış durumlarına neden olabiliyordu.</span><span class="sxs-lookup"><span data-stu-id="7bd36-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7bd36-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7bd36-105">Suggestion</span></span>

<span data-ttu-id="7bd36-106">İdeal olarak, bu hiçbir zaman güvenli bir işlem olmadığından kod, liste öğelerini listelerken, listeleri değiştirmeyecek şekilde düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7bd36-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="7bd36-107">Bununla birlikte, bir uygulama önceki davranışa dönmek için .NET Framework 4.0’ı hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7bd36-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="7bd36-108">Name</span><span class="sxs-lookup"><span data-stu-id="7bd36-108">Name</span></span>    | <span data-ttu-id="7bd36-109">Değer</span><span class="sxs-lookup"><span data-stu-id="7bd36-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7bd36-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7bd36-110">Scope</span></span>   | <span data-ttu-id="7bd36-111">Edge</span><span class="sxs-lookup"><span data-stu-id="7bd36-111">Edge</span></span>        |
| <span data-ttu-id="7bd36-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7bd36-112">Version</span></span> | <span data-ttu-id="7bd36-113">4,5</span><span class="sxs-lookup"><span data-stu-id="7bd36-113">4.5</span></span>         |
| <span data-ttu-id="7bd36-114">Tür</span><span class="sxs-lookup"><span data-stu-id="7bd36-114">Type</span></span>    | <span data-ttu-id="7bd36-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7bd36-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7bd36-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7bd36-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
