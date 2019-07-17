---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237604"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="b68b8-101">Kılavuz satırları yıldız alanı algoritması ayırma geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b68b8-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b68b8-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b68b8-102">Details</span></span>|<span data-ttu-id="b68b8-103">Bir hata düzeltildi [boyutları için ayırma algoritmasını](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) içinde bir <xref:System.Windows.Controls.Grid> içinde .NET Framework 4.7 sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="b68b8-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="b68b8-104">Bazı durumlarda, içeren bir kılavuz gibi <code>Height=&quot;Auto&quot;</code> boş satırları içeren, satırları kılavuz dışında muhtemelen yanlış konumunda tamamen düzenlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b68b8-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="b68b8-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b68b8-105">Suggestion</span></span>|<span data-ttu-id="b68b8-106">Sırayla bu değişiklikleri yararlanmak uygulama için .NET Framework 4.8 veya üzeri çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b68b8-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="b68b8-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b68b8-107">Scope</span></span>|<span data-ttu-id="b68b8-108">Ana</span><span class="sxs-lookup"><span data-stu-id="b68b8-108">Major</span></span>|
|<span data-ttu-id="b68b8-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b68b8-109">Version</span></span>|<span data-ttu-id="b68b8-110">4.8</span><span class="sxs-lookup"><span data-stu-id="b68b8-110">4.8</span></span>|
|<span data-ttu-id="b68b8-111">Tür</span><span class="sxs-lookup"><span data-stu-id="b68b8-111">Type</span></span>|<span data-ttu-id="b68b8-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="b68b8-112">Runtime</span></span>|
