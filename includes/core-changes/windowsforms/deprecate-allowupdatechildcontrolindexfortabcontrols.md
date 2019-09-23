---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181792"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="1f2f6-101">Switch. System. Windows. Forms. Allowupdatechıldcontrolindexfortabcontrols uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1f2f6-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="1f2f6-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` Uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core 3,0 ' den başlayarak Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1f2f6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1f2f6-103">Change description</span></span>

<span data-ttu-id="1f2f6-104">.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="1f2f6-105">Uyumluluk `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="1f2f6-106">.NET Core 'da, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f2f6-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1f2f6-107">Version introduced</span></span>

<span data-ttu-id="1f2f6-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="1f2f6-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f2f6-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1f2f6-109">Recommended action</span></span>

<span data-ttu-id="1f2f6-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-110">Remove the switch.</span></span> <span data-ttu-id="1f2f6-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1f2f6-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="1f2f6-112">Category</span></span>

<span data-ttu-id="1f2f6-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f2f6-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f2f6-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1f2f6-114">Affected APIs</span></span>

- <span data-ttu-id="1f2f6-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f2f6-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
