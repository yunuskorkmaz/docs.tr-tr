---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937071"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="c4f20-101">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="c4f20-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="c4f20-102">.NET Framework 4.8'de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c4f20-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4f20-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="c4f20-103">Change description</span></span>

<span data-ttu-id="c4f20-104">.NET Framework 4.8'den `Switch.System.Windows.Forms.UseLegacyImages` başlayarak, uyumluluk anahtarı yüksek DPI ortamlarında ClickOnce senaryolarında olası görüntü ölçekleme sorunlarını ele aldı.</span><span class="sxs-lookup"><span data-stu-id="c4f20-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="c4f20-105">`true`Ayarlandığında, anahtar, ölçeği %100'den büyük olan yüksek DPI ekranlarda eski görüntü ölçeklendirmesini geri yüklemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c4f20-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="c4f20-106">Daha fazla bilgi için github'daki [.NET Framework 4.8 Yayın Notları'na](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) bakın.</span><span class="sxs-lookup"><span data-stu-id="c4f20-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="c4f20-107">.NET Core'da `Switch.System.Windows.Forms.UseLegacyImages` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c4f20-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4f20-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c4f20-108">Version introduced</span></span>

<span data-ttu-id="c4f20-109">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="c4f20-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4f20-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c4f20-110">Recommended action</span></span>

<span data-ttu-id="c4f20-111">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="c4f20-111">Remove the switch.</span></span> <span data-ttu-id="c4f20-112">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="c4f20-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c4f20-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="c4f20-113">Category</span></span>

<span data-ttu-id="c4f20-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4f20-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4f20-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c4f20-115">Affected APIs</span></span>

- <span data-ttu-id="c4f20-116">None</span><span class="sxs-lookup"><span data-stu-id="c4f20-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
