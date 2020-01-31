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
ms.openlocfilehash: 30f2e675532848c2dbb1f055a0f1489cf3b2baa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865799"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="8f874-102">ICorProfilerCallback2::GarbageCollectionFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f874-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="8f874-103">Profil oluşturucuyu çöp toplamanın tamamlandığını ve tüm çöp toplama geri çağırmaları için verildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="8f874-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f874-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f874-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f874-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f874-105">Remarks</span></span>  
 <span data-ttu-id="8f874-106">`GarbageCollectionFinished` yöntemi çağrıldığında profil oluşturucunun nesneleri son konumlarında incelemesi güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="8f874-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f874-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f874-107">Requirements</span></span>  
 <span data-ttu-id="8f874-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f874-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f874-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8f874-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f874-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f874-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f874-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f874-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f874-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f874-112">See also</span></span>

- [<span data-ttu-id="8f874-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f874-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8f874-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f874-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
