---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643986"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="b62c5-101">Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b62c5-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="b62c5-102">.NET Framework 4.7.1 içinde tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b62c5-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b62c5-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b62c5-103">Change description</span></span>

<span data-ttu-id="b62c5-104">.NET Framework 4.6.2 ve önceki sürümlerde, <xref:System.Windows.Forms.RichTextBox> denetimi Win32 RichEdit denetimi v 3.0 'ı örnekleyebilir ve .NET Framework 4.7.1 hedefleyen uygulamalar için <xref:System.Windows.Forms.RichTextBox> denetimi RichEdit v 4.1 ( *Msftedit. dll*içinde) örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b62c5-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="b62c5-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanması için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b62c5-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="b62c5-106">.NET Core 'da `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b62c5-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="b62c5-107">Yalnızca <xref:System.Windows.Forms.RichTextBox> denetiminin yeni sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b62c5-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b62c5-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b62c5-108">Version introduced</span></span>

<span data-ttu-id="b62c5-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="b62c5-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b62c5-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b62c5-110">Recommended action</span></span>

<span data-ttu-id="b62c5-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b62c5-111">Remove the switch.</span></span> <span data-ttu-id="b62c5-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b62c5-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="b62c5-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="b62c5-113">Category</span></span>

<span data-ttu-id="b62c5-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b62c5-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b62c5-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b62c5-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
