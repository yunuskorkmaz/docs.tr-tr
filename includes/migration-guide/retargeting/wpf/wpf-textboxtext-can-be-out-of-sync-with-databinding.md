---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617295"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="f52e4-101">WPF TextBox.Text veri bağlama ile zaman uyumsuz olabilir</span><span class="sxs-lookup"><span data-stu-id="f52e4-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="f52e4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f52e4-102">Details</span></span>

<span data-ttu-id="f52e4-103">Bazı durumlarda, veri bağlama yazma işlemi sırasında <xref:System.Windows.Controls.TextBox.Text> özelliği değiştirilirse, özellik, veriye bağlı özellik değerinin önceki değerini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f52e4-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f52e4-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="f52e4-104">Suggestion</span></span>

<span data-ttu-id="f52e4-105">Bunun negatif bir etkisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f52e4-105">This should have no negative impact.</span></span> <span data-ttu-id="f52e4-106">Ancak, <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> özelliğini `false` olarak ayarlayarak önceki davranışı geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f52e4-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="f52e4-107">Name</span><span class="sxs-lookup"><span data-stu-id="f52e4-107">Name</span></span>    | <span data-ttu-id="f52e4-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f52e4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f52e4-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f52e4-109">Scope</span></span>   | <span data-ttu-id="f52e4-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f52e4-110">Edge</span></span>        |
| <span data-ttu-id="f52e4-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f52e4-111">Version</span></span> | <span data-ttu-id="f52e4-112">4,5</span><span class="sxs-lookup"><span data-stu-id="f52e4-112">4.5</span></span>         |
|<span data-ttu-id="f52e4-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f52e4-113">Type</span></span>|<span data-ttu-id="f52e4-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f52e4-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f52e4-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f52e4-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
