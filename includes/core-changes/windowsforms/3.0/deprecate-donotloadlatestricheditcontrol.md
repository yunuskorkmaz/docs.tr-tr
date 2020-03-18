---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936999"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="f76a0-101">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f76a0-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="f76a0-102">.NET Framework 4.7.1'de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f76a0-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f76a0-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f76a0-103">Change description</span></span>

<span data-ttu-id="f76a0-104">.NET Framework 4.6.2 ve önceki <xref:System.Windows.Forms.RichTextBox> sürümlerde, kontrol Win32 RichEdit kontrol v3.0 anında ve .NET Framework 4.7.1 <xref:System.Windows.Forms.RichTextBox> hedef uygulamalar için, kontrol RichEdit v4.1 *(msftedit.dll)* anında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f76a0-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="f76a0-105">`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` Uyumluluk anahtarı, .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamaların yeni RichEdit v4.1 denetimini devre dışı bırakmalarına ve bunun yerine eski RichEdit v3 denetimini kullanmalarına olanak sağlamak için kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f76a0-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="f76a0-106">.NET Core'da `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f76a0-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="f76a0-107">Denetimin <xref:System.Windows.Forms.RichTextBox> yalnızca yeni sürümleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f76a0-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f76a0-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f76a0-108">Version introduced</span></span>

<span data-ttu-id="f76a0-109">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="f76a0-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f76a0-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f76a0-110">Recommended action</span></span>

<span data-ttu-id="f76a0-111">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="f76a0-111">Remove the switch.</span></span> <span data-ttu-id="f76a0-112">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="f76a0-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="f76a0-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="f76a0-113">Category</span></span>

<span data-ttu-id="f76a0-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f76a0-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f76a0-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f76a0-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
