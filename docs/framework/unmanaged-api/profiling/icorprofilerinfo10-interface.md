---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo10 Interface'
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2fa0115f6894ac737696b63c1f0f00a0cb028ec
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106910"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="45f8f-103">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45f8f-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="45f8f-104">İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](icorprofilerinfo9-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45f8f-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="45f8f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="45f8f-105">Methods</span></span>  

| <span data-ttu-id="45f8f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="45f8f-106">Method</span></span>|<span data-ttu-id="45f8f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45f8f-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="45f8f-108">EnumerateObjectReferences Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="45f8f-109">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="45f8f-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="45f8f-110">IsFrozenObject Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="45f8f-111">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="45f8f-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="45f8f-112">GetLOHObjectSizeThreshold Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="45f8f-113">Yapılandırılan LOH eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="45f8f-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="45f8f-114">RequestReJITWithInliners Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="45f8f-115">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="45f8f-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="45f8f-116">SuspendRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="45f8f-117">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="45f8f-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="45f8f-118">ResumeRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="45f8f-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="45f8f-119">GC yapmadan çalışma zamanını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="45f8f-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="45f8f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45f8f-120">Requirements</span></span>  

<span data-ttu-id="45f8f-121">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="45f8f-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="45f8f-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="45f8f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="45f8f-123">**.NET sürümleri:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f8f-123">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="45f8f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45f8f-124">See also</span></span>

- [<span data-ttu-id="45f8f-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45f8f-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
