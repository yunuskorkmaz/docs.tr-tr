---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937069"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="142cd-101">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="142cd-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="142cd-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı .NET Core 3,0 üzerinde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="142cd-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="142cd-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="142cd-103">Change description</span></span>

<span data-ttu-id="142cd-104">.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` uyumluluk anahtarı bir uygulamanın sayısal bir biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="142cd-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="142cd-105">.NET Core 'da `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="142cd-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="142cd-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="142cd-106">Version introduced</span></span>

<span data-ttu-id="142cd-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="142cd-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="142cd-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="142cd-108">Recommended action</span></span>

<span data-ttu-id="142cd-109">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="142cd-109">Remove the switch.</span></span> <span data-ttu-id="142cd-110">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="142cd-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="142cd-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="142cd-111">Category</span></span>

<span data-ttu-id="142cd-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="142cd-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="142cd-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="142cd-113">Affected APIs</span></span>

- <span data-ttu-id="142cd-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="142cd-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
