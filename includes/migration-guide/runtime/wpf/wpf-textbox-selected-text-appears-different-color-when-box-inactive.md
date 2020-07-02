---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620706"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="ee038-101">Metin kutusu etkin olmadığında WPF metin kutusu seçili metni farklı bir renk görünüyor</span><span class="sxs-lookup"><span data-stu-id="ee038-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="ee038-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ee038-102">Details</span></span>

<span data-ttu-id="ee038-103">.NET Framework 4,5 ' de, bir WPF metin kutusu denetimi etkin olmadığında (odağa sahip değilse), kutudaki seçili metin, denetimin etkin olduğu değerden farklı bir renkle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ee038-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ee038-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ee038-104">Suggestion</span></span>

<span data-ttu-id="ee038-105">Önceki (.NET Framework 4,0) davranışı özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> <code>false</code> .</span><span class="sxs-lookup"><span data-stu-id="ee038-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="ee038-106">Name</span><span class="sxs-lookup"><span data-stu-id="ee038-106">Name</span></span>    | <span data-ttu-id="ee038-107">Değer</span><span class="sxs-lookup"><span data-stu-id="ee038-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ee038-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ee038-108">Scope</span></span>   |<span data-ttu-id="ee038-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ee038-109">Edge</span></span>|
|<span data-ttu-id="ee038-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ee038-110">Version</span></span>|<span data-ttu-id="ee038-111">4,5</span><span class="sxs-lookup"><span data-stu-id="ee038-111">4.5</span></span>|
|<span data-ttu-id="ee038-112">Tür</span><span class="sxs-lookup"><span data-stu-id="ee038-112">Type</span></span>|<span data-ttu-id="ee038-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="ee038-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee038-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ee038-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
