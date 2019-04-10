---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235957"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="f8159-101">Metin kutusu etkin olduğunda WPF seçili TextBox metni farklı bir renkte görünür.</span><span class="sxs-lookup"><span data-stu-id="f8159-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f8159-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f8159-102">Details</span></span>|<span data-ttu-id="f8159-103">.NET Framework 4.5 WPF metin kutusu denetimi devre dışı olduğunda, (odağı almasa), kutu içerisinde seçili metin denetimi etkin olduğunda daha farklı bir renkte görünür.</span><span class="sxs-lookup"><span data-stu-id="f8159-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="f8159-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="f8159-104">Suggestion</span></span>|<span data-ttu-id="f8159-105">Ayarlayarak önceki (.NET Framework 4.0) davranış geri yüklenebilir <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> özelliğini <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="f8159-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="f8159-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f8159-106">Scope</span></span>|<span data-ttu-id="f8159-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="f8159-107">Edge</span></span>|
|<span data-ttu-id="f8159-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f8159-108">Version</span></span>|<span data-ttu-id="f8159-109">4,5</span><span class="sxs-lookup"><span data-stu-id="f8159-109">4.5</span></span>|
|<span data-ttu-id="f8159-110">Tür</span><span class="sxs-lookup"><span data-stu-id="f8159-110">Type</span></span>|<span data-ttu-id="f8159-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f8159-111">Runtime</span></span>|
|<span data-ttu-id="f8159-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f8159-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
