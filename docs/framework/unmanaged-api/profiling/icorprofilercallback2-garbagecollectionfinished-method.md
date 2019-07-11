---
title: ICorProfilerCallback2::GarbageCollectionFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 736e76a57e6dbce76267ad0fdd242897b4bfdbd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746896"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="b39b8-102">ICorProfilerCallback2::GarbageCollectionFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b39b8-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="b39b8-103">Profil Oluşturucu, çöp toplama tamamlandı ve tüm çöp toplama geri aramaları için verilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="b39b8-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b39b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b39b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b39b8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b39b8-105">Remarks</span></span>  
 <span data-ttu-id="b39b8-106">Son konumlarına nesneleri incelemek profil oluşturucu güvenlidir, `GarbageCollectionFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b39b8-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b39b8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b39b8-107">Requirements</span></span>  
 <span data-ttu-id="b39b8-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b39b8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b39b8-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b39b8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b39b8-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b39b8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b39b8-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b39b8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39b8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b39b8-112">See also</span></span>

- [<span data-ttu-id="b39b8-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b39b8-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b39b8-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b39b8-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
