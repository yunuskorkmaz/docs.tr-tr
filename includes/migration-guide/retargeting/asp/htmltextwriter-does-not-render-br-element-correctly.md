---
ms.openlocfilehash: 0ab6be6f2c6d8ebbe67051e4e3f967a325e654c8
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761152"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="b8371-101">HtmlTextWriter işleme değil `<br/>` öğesi doğru</span><span class="sxs-lookup"><span data-stu-id="b8371-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b8371-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b8371-102">Details</span></span>|<span data-ttu-id="b8371-103">.NET Framework 4.6, çağırma başlayarak <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> ile bir <code>&lt;BR /&gt;</code> öğesi doğru ekler tek <code>&lt;BR /&gt;</code> (yerine iki)</span><span class="sxs-lookup"><span data-stu-id="b8371-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="b8371-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b8371-104">Suggestion</span></span>|<span data-ttu-id="b8371-105">Bir uygulama üzerinde fazladan bağlıysa <code>&lt;BR /&gt;</code> etiketi <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci bir kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8371-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="b8371-106">Bu davranışı değiştirmek yalnızca unutmayın .NET Framework 4.6 veya üzeri, eski davranışı sağlamak için .NET Framework'ün önceki bir sürümü hedeflemek için başka bir seçenek, bu nedenle hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="b8371-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="b8371-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b8371-107">Scope</span></span>|<span data-ttu-id="b8371-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="b8371-108">Edge</span></span>|
|<span data-ttu-id="b8371-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b8371-109">Version</span></span>|<span data-ttu-id="b8371-110">4.6</span><span class="sxs-lookup"><span data-stu-id="b8371-110">4.6</span></span>|
|<span data-ttu-id="b8371-111">Tür</span><span class="sxs-lookup"><span data-stu-id="b8371-111">Type</span></span>|<span data-ttu-id="b8371-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b8371-112">Retargeting</span></span>|
|<span data-ttu-id="b8371-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b8371-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

