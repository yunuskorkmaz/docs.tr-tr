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
ms.openlocfilehash: 21f7e9fa0e567063c49caa390ace09c43454b092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451688"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="13368-102">ICorProfilerCallback2::GarbageCollectionFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13368-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="13368-103">Profil Oluşturucu çöp toplama tamamlandı ve tüm atık toplama geri aramalar için verilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="13368-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13368-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13368-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="13368-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13368-105">Remarks</span></span>  
 <span data-ttu-id="13368-106">Son konumlarına nesneleri incelemek profil oluşturucu güvenlidir, `GarbageCollectionFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="13368-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13368-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13368-107">Requirements</span></span>  
 <span data-ttu-id="13368-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13368-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13368-109">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13368-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13368-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13368-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13368-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13368-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13368-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13368-112">See Also</span></span>  
 [<span data-ttu-id="13368-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13368-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="13368-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13368-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
