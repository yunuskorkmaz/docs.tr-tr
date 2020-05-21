---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721133"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="98162-101">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="98162-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="98162-102">`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.NET Framework 4.7.2 ' de tanıtılan uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="98162-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="98162-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="98162-103">Change description</span></span>

<span data-ttu-id="98162-104">.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` Uyumluluk anahtarı, geliştiricinin özelliğin yeni davranışını devre dışı bırakmanıza olanak tanır <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> . Bu, şimdi kaynak denetimine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="98162-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="98162-105">Özelliğin önceki davranışı döndürülecek `null` .</span><span class="sxs-lookup"><span data-stu-id="98162-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="98162-106">Daha fazla bilgi için bkz. [ \< AppContextSwitchOverrides> öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="98162-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="98162-107">.NET Core 'da, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="98162-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98162-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="98162-108">Version introduced</span></span>

<span data-ttu-id="98162-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="98162-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98162-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="98162-110">Recommended action</span></span>

<span data-ttu-id="98162-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="98162-111">Remove the switch.</span></span> <span data-ttu-id="98162-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98162-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="98162-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="98162-113">Category</span></span>

<span data-ttu-id="98162-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98162-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98162-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="98162-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
