---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10 Interface'
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: fd24491cb1ca55ad48137522c63e78e6387d33e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753295"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="7bb95-103">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bb95-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="7bb95-104">İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](icorprofilerinfo9-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7bb95-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="7bb95-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7bb95-105">Methods</span></span>  

| <span data-ttu-id="7bb95-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7bb95-106">Method</span></span>|<span data-ttu-id="7bb95-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb95-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="7bb95-108">EnumerateObjectReferences Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="7bb95-109">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7bb95-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="7bb95-110">IsFrozenObject Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="7bb95-111">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7bb95-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="7bb95-112">GetLOHObjectSizeThreshold Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="7bb95-113">Yapılandırılan LOH eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="7bb95-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="7bb95-114">RequestReJITWithInliners Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="7bb95-115">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="7bb95-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="7bb95-116">SuspendRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="7bb95-117">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="7bb95-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="7bb95-118">ResumeRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb95-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="7bb95-119">GC yapmadan çalışma zamanını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="7bb95-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7bb95-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bb95-120">Requirements</span></span>  

<span data-ttu-id="7bb95-121">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="7bb95-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="7bb95-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7bb95-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="7bb95-123">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb95-123">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7bb95-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb95-124">See also</span></span>

- [<span data-ttu-id="7bb95-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bb95-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
