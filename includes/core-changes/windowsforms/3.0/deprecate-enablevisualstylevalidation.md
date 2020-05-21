---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721663"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="42084-101">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="42084-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="42084-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`Uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="42084-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="42084-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="42084-103">Change description</span></span>

<span data-ttu-id="42084-104">.NET Framework, `Switch.System.Windows.Forms.EnableVisualStyleValidation` Uyumluluk anahtarı bir uygulamanın sayısal biçimde sağlanan görsel stillerin doğrulanmasını geri açmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="42084-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="42084-105">.NET Core 'da, `Switch.System.Windows.Forms.EnableVisualStyleValidation` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="42084-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="42084-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="42084-106">Version introduced</span></span>

<span data-ttu-id="42084-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="42084-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="42084-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="42084-108">Recommended action</span></span>

<span data-ttu-id="42084-109">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="42084-109">Remove the switch.</span></span> <span data-ttu-id="42084-110">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="42084-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="42084-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="42084-111">Category</span></span>

<span data-ttu-id="42084-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42084-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="42084-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="42084-113">Affected APIs</span></span>

- <span data-ttu-id="42084-114">Yok</span><span class="sxs-lookup"><span data-stu-id="42084-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
