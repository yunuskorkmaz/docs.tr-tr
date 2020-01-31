---
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
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865434"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="f5033-102">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5033-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="f5033-103">Profil oluşturucunun artık [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) ve [ICorProfilerInfo3:: EnumModules](icorprofilerinfo3-enummodules-method.md) yakalama yöntemlerini çağırabelirtemeyeceğini belirtmek için ortak DIL çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f5033-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5033-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5033-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5033-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5033-105">Remarks</span></span>  
 <span data-ttu-id="f5033-106">`ProfilerAttachComplete` geri çağırma, [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi çağrıldıktan sonra verilir.</span><span class="sxs-lookup"><span data-stu-id="f5033-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="f5033-107">Şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="f5033-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="f5033-108">`InitializeForAttach` içinde profil oluşturucu tarafından istenen geri çağrılar etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="f5033-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="f5033-109">Profil Oluşturucu artık eksik bildirimlerle ilgilenmeden ilişkili kimliklerde catch gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f5033-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="f5033-110">CLR bu geri aramadan döndürülen değeri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f5033-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5033-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5033-111">Requirements</span></span>  
 <span data-ttu-id="f5033-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5033-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5033-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f5033-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5033-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5033-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5033-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5033-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5033-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5033-116">See also</span></span>

- [<span data-ttu-id="f5033-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5033-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f5033-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5033-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f5033-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5033-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f5033-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5033-120">Profiling</span></span>](index.md)
