---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937036"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="d31d0-101">DomainUpDown.UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d31d0-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="d31d0-102">.NET Framework 4.7.1'de tanıtılan `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d31d0-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d31d0-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="d31d0-103">Change description</span></span>

<span data-ttu-id="d31d0-104">.NET Framework 4.7.1 ile `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` başlayan uyumluluk anahtarı, geliştiricilerin bağımsız <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve eylemleri devre dışı bırakmalarına olanak sağladı.</span><span class="sxs-lookup"><span data-stu-id="d31d0-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="d31d0-105">Anahtar, bağlam metni varsa göz <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ardı edildiği ve geliştiricinin <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemden önce denetimüzerinde eylem kullanması gereken eski davranışı geri yükledi.</span><span class="sxs-lookup"><span data-stu-id="d31d0-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="d31d0-106">Daha fazla bilgi için [ \<AppContextSwitchOverrides> öğesine](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d31d0-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="d31d0-107">.NET Core'da `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d31d0-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d31d0-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="d31d0-108">Version introduced</span></span>

<span data-ttu-id="d31d0-109">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="d31d0-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d31d0-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d31d0-110">Recommended action</span></span>

<span data-ttu-id="d31d0-111">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="d31d0-111">Remove the switch.</span></span> <span data-ttu-id="d31d0-112">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="d31d0-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d31d0-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="d31d0-113">Category</span></span>

<span data-ttu-id="d31d0-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d31d0-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d31d0-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d31d0-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
