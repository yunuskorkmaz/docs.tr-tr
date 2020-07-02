---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615742"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="41c9d-101">HtmlTextWriter `<br/>` öğeyi doğru işlemiyor</span><span class="sxs-lookup"><span data-stu-id="41c9d-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="41c9d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="41c9d-102">Details</span></span>

<span data-ttu-id="41c9d-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> içeren bir `<BR />` öğe çağırmak doğru bir şekilde yalnızca bir tane eklenir `<BR />` (iki yerine)</span><span class="sxs-lookup"><span data-stu-id="41c9d-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="41c9d-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="41c9d-104">Suggestion</span></span>

<span data-ttu-id="41c9d-105">Bir uygulama ekstra etikete bağımlılarsa `<BR />` <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41c9d-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="41c9d-106">Bu davranış değişikliğinin yalnızca .NET Framework 4,6 veya üstünü hedefleyen uygulamaları etkilediğini unutmayın. bu nedenle, eski davranışı almak için başka bir seçenek .NET Framework önceki bir sürümünü hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="41c9d-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="41c9d-107">Name</span><span class="sxs-lookup"><span data-stu-id="41c9d-107">Name</span></span>    | <span data-ttu-id="41c9d-108">Değer</span><span class="sxs-lookup"><span data-stu-id="41c9d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="41c9d-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="41c9d-109">Scope</span></span>   | <span data-ttu-id="41c9d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="41c9d-110">Edge</span></span>        |
| <span data-ttu-id="41c9d-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="41c9d-111">Version</span></span> | <span data-ttu-id="41c9d-112">4.6</span><span class="sxs-lookup"><span data-stu-id="41c9d-112">4.6</span></span>         |
| <span data-ttu-id="41c9d-113">Tür</span><span class="sxs-lookup"><span data-stu-id="41c9d-113">Type</span></span>    | <span data-ttu-id="41c9d-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="41c9d-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="41c9d-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="41c9d-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
