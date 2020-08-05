---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556228"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="82ed1-101">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="82ed1-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="82ed1-102">`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4.7.1 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="82ed1-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82ed1-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="82ed1-103">Change description</span></span>

<span data-ttu-id="82ed1-104">.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Windows.Forms.RichTextBox> Denetim, Win32 RichEdit denetimi v 3.0 'ı başlatır ve .NET Framework 4.7.1 hedefleyen uygulamalar için, <xref:System.Windows.Forms.RichTextBox> Denetim RichEdit v 4.1 ( *msftedit.dll*) örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82ed1-104">In .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control instantiates the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control instantiates RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="82ed1-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v 4.1 denetimini devre dışı bırakmak ve bunun yerine eski RichEdit v3 denetimini kullanmasını sağlamak için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="82ed1-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="82ed1-106">.NET Core ve .NET 5,0 ve sonraki sürümlerinde, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="82ed1-106">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="82ed1-107">Yalnızca denetimin yeni sürümleri <xref:System.Windows.Forms.RichTextBox> desteklenir.</span><span class="sxs-lookup"><span data-stu-id="82ed1-107">Only new versions of the <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82ed1-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="82ed1-108">Version introduced</span></span>

<span data-ttu-id="82ed1-109">3,0</span><span class="sxs-lookup"><span data-stu-id="82ed1-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82ed1-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="82ed1-110">Recommended action</span></span>

<span data-ttu-id="82ed1-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="82ed1-111">Remove the switch.</span></span> <span data-ttu-id="82ed1-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="82ed1-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="82ed1-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="82ed1-113">Category</span></span>

<span data-ttu-id="82ed1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82ed1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82ed1-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="82ed1-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
