---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858600"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="41853-101">Null coalescer değerleri bir adım sonraya kadar hata ayıklama görünmez</span><span class="sxs-lookup"><span data-stu-id="41853-101">Null coalescer values are not visible in debugger until one step later</span></span>

|   |   |
|---|---|
|<span data-ttu-id="41853-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="41853-102">Details</span></span>|<span data-ttu-id="41853-103">.NET Framework 4.5'teki bir hata, null coalescing işlemi aracılığıyla ayarlanan değerlerin, Çerçeve'nin 64 bit sürümünde çalışırken atama işlemi yürütüldükten hemen sonra hata ayıklayıcıda görünmemelerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="41853-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>|
|<span data-ttu-id="41853-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="41853-104">Suggestion</span></span>|<span data-ttu-id="41853-105">Hata ayıklamada bir kez daha zaman ayırMak, yerel/alanın değerinin doğru şekilde güncelleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="41853-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="41853-106">Ayrıca, bu sorun .NET Framework 4.6'da giderilmiştir; Çerçeve'nin bu sürümüne yükseltme sorunu çözmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="41853-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>|
|<span data-ttu-id="41853-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="41853-107">Scope</span></span>|<span data-ttu-id="41853-108">Edge</span><span class="sxs-lookup"><span data-stu-id="41853-108">Edge</span></span>|
|<span data-ttu-id="41853-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="41853-109">Version</span></span>|<span data-ttu-id="41853-110">4,5</span><span class="sxs-lookup"><span data-stu-id="41853-110">4.5</span></span>|
|<span data-ttu-id="41853-111">Tür</span><span class="sxs-lookup"><span data-stu-id="41853-111">Type</span></span>|<span data-ttu-id="41853-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="41853-112">Runtime</span></span>|
