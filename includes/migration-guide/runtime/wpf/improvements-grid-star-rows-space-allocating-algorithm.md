---
ms.openlocfilehash: bd3b1cc6a98f01d8c40b4cd67002e79a2c4fe714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982240"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="9e79a-101">Kılavuz satırları yıldız alanı algoritması ayırma geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="9e79a-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9e79a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9e79a-102">Details</span></span>|<span data-ttu-id="9e79a-103">Bir hata düzeltildi [boyutları için ayırma algoritmasını \*-satır](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) içinde bir <xref:System.Windows.Controls.Grid> .NET Framework 4.7 içinde tanıtılan.</span><span class="sxs-lookup"><span data-stu-id="9e79a-103">Fixed a bug in the [algorithm for allocating sizes to \*-rows](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="9e79a-104">Bazı durumlarda, içeren bir kılavuz gibi <code>Height=&quot;Auto&quot;</code> boş satırları içeren, satırları kılavuz dışında muhtemelen yanlış konumunda tamamen düzenlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e79a-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="9e79a-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9e79a-105">Suggestion</span></span>|<span data-ttu-id="9e79a-106">Sırayla bu değişiklikleri yararlanmak uygulama için .NET Framework 4.8 veya üzeri çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e79a-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="9e79a-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9e79a-107">Scope</span></span>|<span data-ttu-id="9e79a-108">Ana</span><span class="sxs-lookup"><span data-stu-id="9e79a-108">Major</span></span>|
|<span data-ttu-id="9e79a-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9e79a-109">Version</span></span>|<span data-ttu-id="9e79a-110">4.8</span><span class="sxs-lookup"><span data-stu-id="9e79a-110">4.8</span></span>|
|<span data-ttu-id="9e79a-111">Tür</span><span class="sxs-lookup"><span data-stu-id="9e79a-111">Type</span></span>|<span data-ttu-id="9e79a-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="9e79a-112">Runtime</span></span>|
