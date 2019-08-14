---
title: ICorProfilerInfo10 arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973752"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="bfe0a-102">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="bfe0a-103">İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="bfe0a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bfe0a-104">Methods</span></span>  

| <span data-ttu-id="bfe0a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bfe0a-105">Method</span></span>|<span data-ttu-id="bfe0a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfe0a-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="bfe0a-107">EnumerateObjectReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="bfe0a-108">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="bfe0a-109">Ifrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="bfe0a-110">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="bfe0a-111">GetLOHObjectSizeThreshold yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="bfe0a-112">Yapılandırılan LOH eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="bfe0a-113">RequestReJITWithInliners yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="bfe0a-114">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="bfe0a-115">SuspendRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="bfe0a-116">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="bfe0a-117">ResumeRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfe0a-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="bfe0a-118">GC yapmadan çalışma zamanını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="bfe0a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfe0a-119">Requirements</span></span>  
<span data-ttu-id="bfe0a-120">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="bfe0a-120">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="bfe0a-121">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bfe0a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="bfe0a-122">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe0a-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
## <a name="see-also"></a><span data-ttu-id="bfe0a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe0a-123">See also</span></span>
- [<span data-ttu-id="bfe0a-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bfe0a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
