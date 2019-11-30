---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644021"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="a6b72-101">Switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="a6b72-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="a6b72-102">.NET Framework 4.7.2 içinde tanıtılan `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a6b72-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a6b72-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a6b72-103">Change description</span></span>

<span data-ttu-id="a6b72-104">.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı, geliştiricinin artık kaynak denetimine bir başvuru döndüren <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliğinin yeni davranışını geri almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a6b72-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="a6b72-105">Özelliğin önceki davranışı `null`döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a6b72-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="a6b72-106">Daha fazla bilgi için bkz. [\<AppContextSwitchOverrides > öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="a6b72-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="a6b72-107">.NET Core 'da `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a6b72-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a6b72-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a6b72-108">Version introduced</span></span>

<span data-ttu-id="a6b72-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a6b72-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a6b72-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a6b72-110">Recommended action</span></span>

<span data-ttu-id="a6b72-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a6b72-111">Remove the switch.</span></span> <span data-ttu-id="a6b72-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6b72-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a6b72-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="a6b72-113">Category</span></span>

<span data-ttu-id="a6b72-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6b72-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a6b72-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a6b72-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
