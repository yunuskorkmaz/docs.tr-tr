---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback3::P Rofilerattachtamamlamaya Me yöntemi'
title: ICorProfilerCallback3::ProfilerAttachComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: dcd8ab9fed402593fc955050b0d3be6f8a46730a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788793"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="4bcf3-103">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bcf3-103">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>

<span data-ttu-id="4bcf3-104">Profil oluşturucunun artık [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) ve [ICorProfilerInfo3:: EnumModules](icorprofilerinfo3-enummodules-method.md) yakalama yöntemlerini çağırabelirtemeyeceğini belirtmek için ortak DIL çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-104">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bcf3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4bcf3-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4bcf3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bcf3-106">Remarks</span></span>  

 <span data-ttu-id="4bcf3-107">`ProfilerAttachComplete`Geri çağırma, [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi çağrıldıktan sonra verilir.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-107">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="4bcf3-108">Şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="4bcf3-108">It indicates the following:</span></span>  
  
- <span data-ttu-id="4bcf3-109">İçinde profil oluşturucu tarafından istenen geri çağrılar `InitializeForAttach` etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-109">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="4bcf3-110">Profil Oluşturucu artık eksik bildirimlerle ilgilenmeden ilişkili kimliklerde catch gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-110">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="4bcf3-111">CLR bu geri aramadan döndürülen değeri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-111">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bcf3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bcf3-112">Requirements</span></span>  

 <span data-ttu-id="4bcf3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bcf3-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4bcf3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4bcf3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4bcf3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bcf3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bcf3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcf3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bcf3-117">See also</span></span>

- [<span data-ttu-id="4bcf3-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bcf3-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4bcf3-119">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bcf3-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4bcf3-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4bcf3-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4bcf3-121">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4bcf3-121">Profiling</span></span>](index.md)
