---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805296"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="ac620-101">Metin kutusu etkin olduğunda WPF seçili TextBox metni farklı bir renkte görünür.</span><span class="sxs-lookup"><span data-stu-id="ac620-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ac620-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ac620-102">Details</span></span>|<span data-ttu-id="ac620-103">.NET Framework 4.5 WPF metin kutusu denetimi devre dışı olduğunda, (odağı almasa), kutu içerisinde seçili metin denetimi etkin olduğunda daha farklı bir renkte görünür.</span><span class="sxs-lookup"><span data-stu-id="ac620-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="ac620-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ac620-104">Suggestion</span></span>|<span data-ttu-id="ac620-105">Ayarlayarak önceki (.NET Framework 4.0) davranış geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> özelliğini <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="ac620-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="ac620-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ac620-106">Scope</span></span>|<span data-ttu-id="ac620-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="ac620-107">Edge</span></span>|
|<span data-ttu-id="ac620-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ac620-108">Version</span></span>|<span data-ttu-id="ac620-109">4,5</span><span class="sxs-lookup"><span data-stu-id="ac620-109">4.5</span></span>|
|<span data-ttu-id="ac620-110">Tür</span><span class="sxs-lookup"><span data-stu-id="ac620-110">Type</span></span>|<span data-ttu-id="ac620-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ac620-111">Runtime</span></span>|
|<span data-ttu-id="ac620-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ac620-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
