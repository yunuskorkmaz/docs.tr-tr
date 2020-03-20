---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237604"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="5dedd-101">Grid yıldız satırları alan ayırma algoritması geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="5dedd-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5dedd-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5dedd-102">Details</span></span>|<span data-ttu-id="5dedd-103">.NET Framework 4.7'de tanıtılan boyutlarda <xref:System.Windows.Controls.Grid> ) ayırmak [için algoritmadaki](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)bir hata düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="5dedd-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="5dedd-104">Boş satırlar <code>Height=&quot;Auto&quot;</code> içeren bir Izgara gibi bazı durumlarda, satırlar yanlış konumda, muhtemelen Tamamen Izgara dışında düzenlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5dedd-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="5dedd-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="5dedd-105">Suggestion</span></span>|<span data-ttu-id="5dedd-106">Uygulamanın bu değişikliklerden yararlanabilmesi için .NET Framework 4.8 veya sonraki yerlerde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5dedd-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="5dedd-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5dedd-107">Scope</span></span>|<span data-ttu-id="5dedd-108">Ana</span><span class="sxs-lookup"><span data-stu-id="5dedd-108">Major</span></span>|
|<span data-ttu-id="5dedd-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5dedd-109">Version</span></span>|<span data-ttu-id="5dedd-110">4.8</span><span class="sxs-lookup"><span data-stu-id="5dedd-110">4.8</span></span>|
|<span data-ttu-id="5dedd-111">Tür</span><span class="sxs-lookup"><span data-stu-id="5dedd-111">Type</span></span>|<span data-ttu-id="5dedd-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5dedd-112">Runtime</span></span>|
