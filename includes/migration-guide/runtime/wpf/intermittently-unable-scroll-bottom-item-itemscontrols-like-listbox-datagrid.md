---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622122"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="b7d25-101">Özel veri şablonları kullanılırken, ara sıra ıtemcontrols (ListBox ve DataGrid gibi) alt öğeye kaydırılamıyor</span><span class="sxs-lookup"><span data-stu-id="b7d25-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="b7d25-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7d25-102">Details</span></span>

<span data-ttu-id="b7d25-103">Bazı örneklerde, 4,5 .NET Framework bir hata, ıtemcontrols (gibi,, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> vb.), özel veri şablonları kullanırken kendi alt öğelerini kaydırmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b7d25-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="b7d25-104">Kaydırmanın ikinci kez denendiğinde (geri alındıktan sonra), daha sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7d25-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b7d25-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b7d25-105">Suggestion</span></span>

<span data-ttu-id="b7d25-106">Bu sorun .NET Framework 4.5.2 düzeltilmiştir ve bu sürüme (veya sonraki bir sürüme) yükselterek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7d25-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="b7d25-107">Alternatif olarak, kullanıcılar kaydırma çubuklarını bu koleksiyonlardaki son öğelere sürüklemeye devam edebilir, ancak bunu iki kez denemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b7d25-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="b7d25-108">Name</span><span class="sxs-lookup"><span data-stu-id="b7d25-108">Name</span></span>    | <span data-ttu-id="b7d25-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b7d25-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b7d25-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b7d25-110">Scope</span></span>   |<span data-ttu-id="b7d25-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="b7d25-111">Minor</span></span>|
|<span data-ttu-id="b7d25-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b7d25-112">Version</span></span>|<span data-ttu-id="b7d25-113">4,5</span><span class="sxs-lookup"><span data-stu-id="b7d25-113">4.5</span></span>|
|<span data-ttu-id="b7d25-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b7d25-114">Type</span></span>|<span data-ttu-id="b7d25-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b7d25-115">Runtime</span></span>|
