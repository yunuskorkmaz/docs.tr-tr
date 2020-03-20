---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804484"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="cdabe-101">HtmlTextWriter öğeyi `<br/>` doğru işlemez</span><span class="sxs-lookup"><span data-stu-id="cdabe-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cdabe-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cdabe-102">Details</span></span>|<span data-ttu-id="cdabe-103">.NET Framework 4.6'dan <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> başlayarak, arama ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> bir <code>&lt;BR /&gt;</code> öğeyle yalnızca bir <code>&lt;BR /&gt;</code> tane (iki yerine) doğru bir şekilde ekler</span><span class="sxs-lookup"><span data-stu-id="cdabe-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="cdabe-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="cdabe-104">Suggestion</span></span>|<span data-ttu-id="cdabe-105">Bir uygulama ek <code>&lt;BR /&gt;</code> etikete bağlıysa, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdabe-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="cdabe-106">Bu davranış değişikliğinin yalnızca .NET Framework 4.6 veya sonraki leri hedefleyen uygulamaları etkilediğini unutmayın, bu nedenle başka bir seçenek de eski davranışı elde etmek için .NET Framework'ün önceki bir sürümünü hedeflemektir.</span><span class="sxs-lookup"><span data-stu-id="cdabe-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="cdabe-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="cdabe-107">Scope</span></span>|<span data-ttu-id="cdabe-108">Edge</span><span class="sxs-lookup"><span data-stu-id="cdabe-108">Edge</span></span>|
|<span data-ttu-id="cdabe-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="cdabe-109">Version</span></span>|<span data-ttu-id="cdabe-110">4.6</span><span class="sxs-lookup"><span data-stu-id="cdabe-110">4.6</span></span>|
|<span data-ttu-id="cdabe-111">Tür</span><span class="sxs-lookup"><span data-stu-id="cdabe-111">Type</span></span>|<span data-ttu-id="cdabe-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="cdabe-112">Retargeting</span></span>|
|<span data-ttu-id="cdabe-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cdabe-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
