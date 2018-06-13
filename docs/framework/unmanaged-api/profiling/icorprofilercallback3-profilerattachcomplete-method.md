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
ms.openlocfilehash: 8397900e2dafb69807417090cbb30c85dd884c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454384"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="06c1d-102">ICorProfilerCallback3::ProfilerAttachComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06c1d-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="06c1d-103">Ortak dil çalışma zamanı tarafından profil oluşturucu artık çağırabilirsiniz belirtmek için (CLR) olarak adlandırılan [Icorprofilerınfo3::enumjıtedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) ve [Icorprofilerınfo3::enummodules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) yakalama yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="06c1d-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06c1d-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="06c1d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06c1d-105">Remarks</span></span>  
 <span data-ttu-id="06c1d-106">`ProfilerAttachComplete` Geri çağırma sonra verildiği [Icorprofilercallback3::ınitializeforattach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="06c1d-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="06c1d-107">Aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="06c1d-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="06c1d-108">Profil Oluşturucusu'nda tarafından talep edilen geri çağırmaları `InitializeForAttach` etkinleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="06c1d-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="06c1d-109">Profil Oluşturucu olmaksızın ilişkili kimlikleri hakkında eksik bildirimler ilgilenen üzerinde nım artık gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06c1d-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="06c1d-110">CLR bu geri çağırma yönteminden döndürülen değer yok sayar.</span><span class="sxs-lookup"><span data-stu-id="06c1d-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06c1d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06c1d-111">Requirements</span></span>  
 <span data-ttu-id="06c1d-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06c1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06c1d-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06c1d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06c1d-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06c1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06c1d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06c1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c1d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06c1d-116">See Also</span></span>  
 [<span data-ttu-id="06c1d-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06c1d-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="06c1d-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06c1d-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="06c1d-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="06c1d-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="06c1d-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06c1d-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
