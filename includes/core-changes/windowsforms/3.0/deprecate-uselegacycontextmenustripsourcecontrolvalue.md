---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556236"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="1d18b-101">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1d18b-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="1d18b-102">`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.NET Framework 4.7.2 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve üzeri sürümlerde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1d18b-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1d18b-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1d18b-103">Change description</span></span>

<span data-ttu-id="1d18b-104">.NET Framework 4.7.2 ile başlayarak, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` Uyumluluk anahtarı, geliştiricinin özelliğin yeni davranışını devre dışı bırakmanıza olanak tanır <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> . Bu, şimdi kaynak denetimine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d18b-104">Starting with .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="1d18b-105">Özelliğin önceki davranışı döndürülecek `null` .</span><span class="sxs-lookup"><span data-stu-id="1d18b-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="1d18b-106">Daha fazla bilgi için bkz. [ \<AppContextSwitchOverrides> öğesi](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="1d18b-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="1d18b-107">.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1d18b-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1d18b-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1d18b-108">Version introduced</span></span>

<span data-ttu-id="1d18b-109">3,0</span><span class="sxs-lookup"><span data-stu-id="1d18b-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1d18b-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1d18b-110">Recommended action</span></span>

<span data-ttu-id="1d18b-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1d18b-111">Remove the switch.</span></span> <span data-ttu-id="1d18b-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d18b-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1d18b-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="1d18b-113">Category</span></span>

<span data-ttu-id="1d18b-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d18b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d18b-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1d18b-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
