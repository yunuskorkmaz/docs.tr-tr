---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback2:: GarbageCollectionFinished yöntemi'
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
ms.openlocfilehash: 9e41c5ced76af40866269fdff74fd302b937b70e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657120"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="ba62e-103">ICorProfilerCallback2::GarbageCollectionFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba62e-103">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>

<span data-ttu-id="ba62e-104">Profil oluşturucuyu çöp toplamanın tamamlandığını ve tüm çöp toplama geri çağırmaları için verildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ba62e-104">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba62e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba62e-105">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba62e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba62e-106">Remarks</span></span>  

 <span data-ttu-id="ba62e-107">Profil oluşturucunun, yöntemi çağrıldığında son konumlarında nesneleri incelemesi güvenlidir `GarbageCollectionFinished` .</span><span class="sxs-lookup"><span data-stu-id="ba62e-107">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba62e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba62e-108">Requirements</span></span>  

 <span data-ttu-id="ba62e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba62e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba62e-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ba62e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba62e-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba62e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba62e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba62e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba62e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba62e-113">See also</span></span>

- [<span data-ttu-id="ba62e-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba62e-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ba62e-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba62e-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
