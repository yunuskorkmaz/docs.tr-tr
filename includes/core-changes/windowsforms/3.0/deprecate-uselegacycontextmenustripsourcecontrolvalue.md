---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936986"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="f858a-101">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f858a-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="f858a-102">.NET Framework 4.7.2 içinde tanıtılan `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f858a-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f858a-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f858a-103">Change description</span></span>

<span data-ttu-id="f858a-104">.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` uyumluluk anahtarı, geliştiricinin artık kaynak denetimine bir başvuru döndüren <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliğinin yeni davranışını geri almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f858a-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="f858a-105">Özelliğin önceki davranışı `null`döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f858a-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="f858a-106">Daha fazla bilgi için bkz. [\<AppContextSwitchOverrides > öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="f858a-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="f858a-107">.NET Core 'da `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f858a-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f858a-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f858a-108">Version introduced</span></span>

<span data-ttu-id="f858a-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f858a-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f858a-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f858a-110">Recommended action</span></span>

<span data-ttu-id="f858a-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f858a-111">Remove the switch.</span></span> <span data-ttu-id="f858a-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f858a-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="f858a-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="f858a-113">Category</span></span>

<span data-ttu-id="f858a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f858a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f858a-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f858a-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
