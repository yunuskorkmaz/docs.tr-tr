---
ms.openlocfilehash: c01705002ad87a12389078d75ffd0f91f934d36e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496917"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="5a45b-101">Metin kutusu etkin olmadığında WPF metin kutusu seçili metni farklı bir renk görünüyor</span><span class="sxs-lookup"><span data-stu-id="5a45b-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="5a45b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5a45b-102">Details</span></span>

<span data-ttu-id="5a45b-103">.NET Framework 4,5 ' de, bir WPF metin kutusu denetimi etkin olmadığında (odağa sahip değilse), kutudaki seçili metin, denetimin etkin olduğu değerden farklı bir renkle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5a45b-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a45b-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="5a45b-104">Suggestion</span></span>

<span data-ttu-id="5a45b-105">Önceki (.NET Framework 4,0) davranışı özelliği olarak ayarlanarak geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> <code>false</code> .</span><span class="sxs-lookup"><span data-stu-id="5a45b-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="5a45b-106">Name</span><span class="sxs-lookup"><span data-stu-id="5a45b-106">Name</span></span>    | <span data-ttu-id="5a45b-107">Değer</span><span class="sxs-lookup"><span data-stu-id="5a45b-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a45b-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5a45b-108">Scope</span></span>   |<span data-ttu-id="5a45b-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5a45b-109">Edge</span></span>|
|<span data-ttu-id="5a45b-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5a45b-110">Version</span></span>|<span data-ttu-id="5a45b-111">4,5</span><span class="sxs-lookup"><span data-stu-id="5a45b-111">4.5</span></span>|
|<span data-ttu-id="5a45b-112">Tür</span><span class="sxs-lookup"><span data-stu-id="5a45b-112">Type</span></span>|<span data-ttu-id="5a45b-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5a45b-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5a45b-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5a45b-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
