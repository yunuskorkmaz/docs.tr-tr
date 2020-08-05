---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556235"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="819eb-101">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="819eb-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="819eb-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı .NET Framework 4,6 ve sonraki sürümlerde Windows Forms desteklenir, ancak .NET Core veya .net 5,0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="819eb-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="819eb-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="819eb-103">Change description</span></span>

<span data-ttu-id="819eb-104">.NET Framework 4,6 ve sonraki sürümlerde, bir sekmeyi seçmek denetim koleksiyonunu yeniden sıralar.</span><span class="sxs-lookup"><span data-stu-id="819eb-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="819eb-105">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Uyumluluk anahtarı, bu davranış istenmeyen olduğunda bir uygulamanın bu yeniden sıralamayı atlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="819eb-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="819eb-106">.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="819eb-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="819eb-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="819eb-107">Version introduced</span></span>

<span data-ttu-id="819eb-108">3,0</span><span class="sxs-lookup"><span data-stu-id="819eb-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="819eb-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="819eb-109">Recommended action</span></span>

<span data-ttu-id="819eb-110">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="819eb-110">Remove the switch.</span></span> <span data-ttu-id="819eb-111">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="819eb-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="819eb-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="819eb-112">Category</span></span>

<span data-ttu-id="819eb-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="819eb-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="819eb-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="819eb-114">Affected APIs</span></span>

- <span data-ttu-id="819eb-115">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="819eb-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
