---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093618"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="30a60-101">IL ret deneyin bölgede izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="30a60-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30a60-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30a60-102">Details</span></span>|<span data-ttu-id="30a60-103">JIT64 tam zamanında derleyici, bir IL yönergesi bir try bölgede ret (.NET Framework 4. 6'içinde kullanılan) Ryujıt izin vermez.</span><span class="sxs-lookup"><span data-stu-id="30a60-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="30a60-104">Bir try bölgeden döndüren ECMA-335 belirtimine göre izin verilmez ve bu tür IL bilinen hiçbir yönetilen derleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30a60-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="30a60-105">Bununla birlikte, yansıma kullanarak oluşturulursa JIT64 derleyici böyle IL yürütecek gösterin.</span><span class="sxs-lookup"><span data-stu-id="30a60-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="30a60-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="30a60-106">Suggestion</span></span>|<span data-ttu-id="30a60-107">Bir uygulama bir try bölgede ret opcode içeren IL oluşturuyorsa, uygulama .NET Framework 4. 5'i eski JIT kullanın ve bu kesmesinden kaçınılmasını sağlar hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="30a60-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="30a60-108">Alternatif olarak, oluşturulan IL sonra deneyin bölge döndürmek için güncelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="30a60-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="30a60-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="30a60-109">Scope</span></span>|<span data-ttu-id="30a60-110">Kenar</span><span class="sxs-lookup"><span data-stu-id="30a60-110">Edge</span></span>|
|<span data-ttu-id="30a60-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="30a60-111">Version</span></span>|<span data-ttu-id="30a60-112">4.6</span><span class="sxs-lookup"><span data-stu-id="30a60-112">4.6</span></span>|
|<span data-ttu-id="30a60-113">Tür</span><span class="sxs-lookup"><span data-stu-id="30a60-113">Type</span></span>|<span data-ttu-id="30a60-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="30a60-114">Retargeting</span></span>|
