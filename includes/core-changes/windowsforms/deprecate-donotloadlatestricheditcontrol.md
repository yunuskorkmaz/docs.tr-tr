---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181841"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="9dbea-101">Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9dbea-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="9dbea-102">.NET Framework 4.7.1 ' de tanıtılan Uyumlulukanahtarı.NETCore3,0'deWindowsFormsdesteklenmez.`Switch.System.Windows.Forms.UseLegacyImages`</span><span class="sxs-lookup"><span data-stu-id="9dbea-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9dbea-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9dbea-103">Change description</span></span>

<span data-ttu-id="9dbea-104">.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Windows.Forms.RichTextBox> denetim, Win32 RichEdit denetimi v 3.0 örneğini oluşturur ve .NET Framework 4.7.1 hedefleyen uygulamalar için <xref:System.Windows.Forms.RichTextBox> , denetim RichEdit v 4.1 örneğini oluşturur (  *Msftedit. dll*).</span><span class="sxs-lookup"><span data-stu-id="9dbea-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="9dbea-105">Uyumluluk `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanması için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9dbea-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="9dbea-106">.NET Core 'da, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9dbea-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="9dbea-107">Yalnızca <xref:System.Windows.Forms.RichTextBox> denetimin yeni sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9dbea-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9dbea-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9dbea-108">Version introduced</span></span>

<span data-ttu-id="9dbea-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="9dbea-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9dbea-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9dbea-110">Recommended action</span></span>

<span data-ttu-id="9dbea-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9dbea-111">Remove the switch.</span></span> <span data-ttu-id="9dbea-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9dbea-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="9dbea-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="9dbea-113">Category</span></span>

<span data-ttu-id="9dbea-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dbea-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9dbea-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9dbea-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
