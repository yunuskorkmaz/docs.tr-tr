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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6bd3326aa5807bd7f2dd882991d211cbbf873067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150416"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="53bb7-102">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bb7-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="53bb7-103">Ortak dil çalışma zamanı tarafından profil oluşturucu artık çağırabilirsiniz belirtmek için (CLR) olarak adlandırılan [Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) ve [Icorprofilerınfo3::enummodules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) yakalama yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="53bb7-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53bb7-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="53bb7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53bb7-105">Remarks</span></span>  
 <span data-ttu-id="53bb7-106">`ProfilerAttachComplete` Geri çağırma sonra verildiği [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="53bb7-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="53bb7-107">Aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="53bb7-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="53bb7-108">Profil Oluşturucu tarafından talep edilen geri çağırmaları `InitializeForAttach` etkinleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="53bb7-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="53bb7-109">Profil Oluşturucu olmaksızın ilişkili kimlikler eksik bildirimler hakkında endişe üzerinde yakalama artık gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53bb7-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="53bb7-110">CLR, bu geri dönüş değerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="53bb7-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bb7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53bb7-111">Requirements</span></span>  
 <span data-ttu-id="53bb7-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53bb7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bb7-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53bb7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53bb7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53bb7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53bb7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bb7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bb7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bb7-116">See also</span></span>

- [<span data-ttu-id="53bb7-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53bb7-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="53bb7-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bb7-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="53bb7-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53bb7-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="53bb7-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="53bb7-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
