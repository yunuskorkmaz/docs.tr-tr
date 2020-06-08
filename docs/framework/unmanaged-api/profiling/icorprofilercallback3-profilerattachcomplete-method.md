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
ms.openlocfilehash: bcc938ff9322fca4f45366fdc695e0c3901484b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499668"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="9a1f6-102">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a1f6-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="9a1f6-103">Profil oluşturucunun artık [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) ve [ICorProfilerInfo3:: EnumModules](icorprofilerinfo3-enummodules-method.md) yakalama yöntemlerini çağırabelirtemeyeceğini belirtmek için ortak DIL çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a1f6-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a1f6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a1f6-105">Remarks</span></span>  
 <span data-ttu-id="9a1f6-106">`ProfilerAttachComplete`Geri çağırma, [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi çağrıldıktan sonra verilir.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="9a1f6-107">Şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="9a1f6-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="9a1f6-108">İçinde profil oluşturucu tarafından istenen geri çağrılar `InitializeForAttach` etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="9a1f6-109">Profil Oluşturucu artık eksik bildirimlerle ilgilenmeden ilişkili kimliklerde catch gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="9a1f6-110">CLR bu geri aramadan döndürülen değeri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1f6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a1f6-111">Requirements</span></span>  
 <span data-ttu-id="9a1f6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1f6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1f6-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9a1f6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a1f6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9a1f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a1f6-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1f6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a1f6-116">See also</span></span>

- [<span data-ttu-id="9a1f6-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f6-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9a1f6-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f6-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9a1f6-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a1f6-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9a1f6-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a1f6-120">Profiling</span></span>](index.md)
