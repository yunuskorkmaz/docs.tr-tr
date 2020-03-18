---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936986"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="c80eb-101">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="c80eb-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="c80eb-102">.NET Framework 4.7.2'de tanıtılan `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı ,NET Core 3.0'daki Windows Formlar'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c80eb-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c80eb-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="c80eb-103">Change description</span></span>

<span data-ttu-id="c80eb-104">.NET Framework 4.7.2 ile `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` başlayarak, uyumluluk anahtarı geliştiricinin <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> artık kaynak denetimine bir başvuru döndüren özelliğin yeni davranışını devre dışı bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c80eb-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="c80eb-105">Özelliğin önceki davranışı dönmek `null`oldu.</span><span class="sxs-lookup"><span data-stu-id="c80eb-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="c80eb-106">Daha fazla bilgi için [ \<AppContextSwitchOverrides> öğesine](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c80eb-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="c80eb-107">.NET Core'da `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c80eb-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c80eb-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c80eb-108">Version introduced</span></span>

<span data-ttu-id="c80eb-109">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="c80eb-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c80eb-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c80eb-110">Recommended action</span></span>

<span data-ttu-id="c80eb-111">Anahtarı çıkarın.</span><span class="sxs-lookup"><span data-stu-id="c80eb-111">Remove the switch.</span></span> <span data-ttu-id="c80eb-112">Anahtar desteklenmez ve alternatif bir işlevsellik yok.</span><span class="sxs-lookup"><span data-stu-id="c80eb-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c80eb-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="c80eb-113">Category</span></span>

<span data-ttu-id="c80eb-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c80eb-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c80eb-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c80eb-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
