---
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175076"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="71ea0-102">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71ea0-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="71ea0-103">[ICorProfilerInfo9'un](icorprofilerinfo9-interface.md) işlev IL'sini değiştirme, çalışma zamanındaki sorgu bilgilerini ve çalışma süresini askıya alma ve devam ettirme yöntemleri sağlayan bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71ea0-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="71ea0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71ea0-104">Methods</span></span>  

| <span data-ttu-id="71ea0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="71ea0-105">Method</span></span>|<span data-ttu-id="71ea0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71ea0-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="71ea0-107">EnumerateObjectReferences Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="71ea0-108">ObjectID, geri arama ve istemciData göz önüne alındığında, her nesne başvuru (varsa) numarasılandırır.</span><span class="sxs-lookup"><span data-stu-id="71ea0-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="71ea0-109">IsFrozenObject Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="71ea0-110">ObjectID verildiğinde, nesnenin salt okunur segmentte olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="71ea0-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="71ea0-111">GetLOHObjectSizeThreshold Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="71ea0-112">Yapılandırılan LOH eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="71ea0-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="71ea0-113">RequestReJITWithInliners Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="71ea0-114">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir inliners rejits.</span><span class="sxs-lookup"><span data-stu-id="71ea0-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="71ea0-115">SuspendRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="71ea0-116">GC gerçekleştirmeden çalışma süresini askıya aldı.</span><span class="sxs-lookup"><span data-stu-id="71ea0-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="71ea0-117">ResumeRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="71ea0-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="71ea0-118">GC gerçekleştirmeden çalışma süresini devam ettirer.</span><span class="sxs-lookup"><span data-stu-id="71ea0-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="71ea0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71ea0-119">Requirements</span></span>  
<span data-ttu-id="71ea0-120">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri.](../../../core/install/dependencies.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="71ea0-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="71ea0-121">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71ea0-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="71ea0-122">**.NET Sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ea0-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="71ea0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71ea0-123">See also</span></span>

- [<span data-ttu-id="71ea0-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71ea0-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
