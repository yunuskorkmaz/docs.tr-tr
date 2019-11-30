---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644000"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="82fda-101">Switch. System. Windows. Forms. Allowupdatechıldcontrolindexfortabcontrols uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="82fda-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="82fda-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core 3,0 ' den itibaren Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="82fda-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82fda-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="82fda-103">Change description</span></span>

<span data-ttu-id="82fda-104">.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar.</span><span class="sxs-lookup"><span data-stu-id="82fda-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="82fda-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` uyumluluk anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="82fda-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="82fda-106">.NET Core 'da `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="82fda-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82fda-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="82fda-107">Version introduced</span></span>

<span data-ttu-id="82fda-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="82fda-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82fda-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="82fda-109">Recommended action</span></span>

<span data-ttu-id="82fda-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="82fda-110">Remove the switch.</span></span> <span data-ttu-id="82fda-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="82fda-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="82fda-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="82fda-112">Category</span></span>

<span data-ttu-id="82fda-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82fda-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82fda-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="82fda-114">Affected APIs</span></span>

- <span data-ttu-id="82fda-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="82fda-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
