---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093643"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="73a35-101">WPF TextBox.Text veri bağlama ile zaman uyumsuz olabilir</span><span class="sxs-lookup"><span data-stu-id="73a35-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

|   |   |
|---|---|
|<span data-ttu-id="73a35-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="73a35-102">Details</span></span>|<span data-ttu-id="73a35-103">Bazı durumlarda, veri bağlama yazma işlemi sırasında <xref:System.Windows.Controls.TextBox.Text> özelliği değiştirilirse, özellik, veriye bağlı özellik değerinin önceki değerini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="73a35-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>|
|<span data-ttu-id="73a35-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="73a35-104">Suggestion</span></span>|<span data-ttu-id="73a35-105">Bunun negatif bir etkisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73a35-105">This should have no negative impact.</span></span> <span data-ttu-id="73a35-106">Ancak, <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini <code>false</code> olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73a35-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to <code>false</code>.</span></span>|
|<span data-ttu-id="73a35-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="73a35-107">Scope</span></span>|<span data-ttu-id="73a35-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="73a35-108">Edge</span></span>|
|<span data-ttu-id="73a35-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="73a35-109">Version</span></span>|<span data-ttu-id="73a35-110">4,5</span><span class="sxs-lookup"><span data-stu-id="73a35-110">4.5</span></span>|
|<span data-ttu-id="73a35-111">Tür</span><span class="sxs-lookup"><span data-stu-id="73a35-111">Type</span></span>|<span data-ttu-id="73a35-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="73a35-112">Retargeting</span></span>|
|<span data-ttu-id="73a35-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="73a35-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
