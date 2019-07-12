---
ms.openlocfilehash: 2674edc595d8e4e1e4c2ee42b39aa59265127462
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803254"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="89a87-101">Aralıklı olarak oluşturulamıyor (örneğin, liste ve DataGrid) ItemsControls alt öğeye ilerlemek özel DataTemplates kullanırken</span><span class="sxs-lookup"><span data-stu-id="89a87-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

|   |   |
|---|---|
|<span data-ttu-id="89a87-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="89a87-102">Details</span></span>|<span data-ttu-id="89a87-103">Bazı durumlarda, .NET Framework 4.5 hatada ItemsControls neden oluyor (gibi <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, vs.) için kendi alt öğesi özel DataTemplates kullanırken kaydırma değil.</span><span class="sxs-lookup"><span data-stu-id="89a87-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="89a87-104">Kaydırma (Yedekleme kaydırma sonra) ikinci bir kez girişiminde bulunulursa, sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="89a87-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>|
|<span data-ttu-id="89a87-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="89a87-105">Suggestion</span></span>|<span data-ttu-id="89a87-106">Bu sorun, .NET Framework 4.5.2 sabit ve bu sürümü (veya sonraki bir sürümü) .NET Framework'ün yükselterek desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="89a87-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="89a87-107">Alternatif olarak, kullanıcılar yine de bu koleksiyonlardaki son öğelerine kaydırma çubukları sürükleyebilirsiniz, ancak iki kez başarıyla Bunu yapmak denemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="89a87-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>|
|<span data-ttu-id="89a87-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="89a87-108">Scope</span></span>|<span data-ttu-id="89a87-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="89a87-109">Minor</span></span>|
|<span data-ttu-id="89a87-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="89a87-110">Version</span></span>|<span data-ttu-id="89a87-111">4,5</span><span class="sxs-lookup"><span data-stu-id="89a87-111">4.5</span></span>|
|<span data-ttu-id="89a87-112">Tür</span><span class="sxs-lookup"><span data-stu-id="89a87-112">Type</span></span>|<span data-ttu-id="89a87-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="89a87-113">Runtime</span></span>|

