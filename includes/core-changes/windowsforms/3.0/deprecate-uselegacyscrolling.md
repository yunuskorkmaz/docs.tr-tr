---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937036"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="c3fa0-101">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="c3fa0-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="c3fa0-102">.NET Framework 4.7.1 içinde tanıtılan `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c3fa0-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c3fa0-103">Change description</span></span>

<span data-ttu-id="c3fa0-104">.NET Framework 4.7.1 ile başlayarak, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` uyumluluk anahtarı geliştiricilerin bağımsız <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemleri geri çevirme yapmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="c3fa0-105">Anahtar, bağlam metni varsa <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> yoksayıldığı eski davranışı geri yükledi ve geliştirici, <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eyleminden önce denetimde <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemi kullanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="c3fa0-106">Daha fazla bilgi için bkz. [\<AppContextSwitchOverrides > öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="c3fa0-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="c3fa0-107">.NET Core 'da `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c3fa0-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c3fa0-108">Version introduced</span></span>

<span data-ttu-id="c3fa0-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="c3fa0-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c3fa0-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c3fa0-110">Recommended action</span></span>

<span data-ttu-id="c3fa0-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-111">Remove the switch.</span></span> <span data-ttu-id="c3fa0-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c3fa0-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c3fa0-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="c3fa0-113">Category</span></span>

<span data-ttu-id="c3fa0-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c3fa0-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c3fa0-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c3fa0-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
