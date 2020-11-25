---
title: ICorProfilerInfo10 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: a99fa8410bbd0dedeaeb9e1713107a3dcc9ada6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727230"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="0f835-102">ICorProfilerInfo10 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f835-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="0f835-103">İşlev Il 'yi değiştirme, çalışma zamanındaki sorgu bilgileri ve çalışma zamanını askıya alma ve sürdürmeyi sağlayan yöntemler sağlayan bir [ICorProfilerInfo9](icorprofilerinfo9-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f835-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="0f835-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f835-104">Methods</span></span>  

| <span data-ttu-id="0f835-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f835-105">Method</span></span>|<span data-ttu-id="0f835-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f835-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="0f835-107">EnumerateObjectReferences Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="0f835-108">Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0f835-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="0f835-109">IsFrozenObject Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="0f835-110">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0f835-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="0f835-111">GetLOHObjectSizeThreshold Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="0f835-112">Yapılandırılan LOH eşiğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0f835-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="0f835-113">RequestReJITWithInliners Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="0f835-114">İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="0f835-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="0f835-115">SuspendRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="0f835-116">GC yapmadan çalışma zamanını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="0f835-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="0f835-117">ResumeRuntime Metodu</span><span class="sxs-lookup"><span data-stu-id="0f835-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="0f835-118">GC yapmadan çalışma zamanını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="0f835-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="0f835-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f835-119">Requirements</span></span>  

<span data-ttu-id="0f835-120">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="0f835-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="0f835-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0f835-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="0f835-122">**.NET sürümleri:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f835-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0f835-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f835-123">See also</span></span>

- [<span data-ttu-id="0f835-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f835-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
