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
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499837"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="4fc50-102">ICorProfilerCallback2::GarbageCollectionFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fc50-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="4fc50-103">Profil oluşturucuyu çöp toplamanın tamamlandığını ve tüm çöp toplama geri çağırmaları için verildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fc50-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fc50-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4fc50-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fc50-105">Remarks</span></span>  
 <span data-ttu-id="4fc50-106">Profil oluşturucunun, yöntemi çağrıldığında son konumlarında nesneleri incelemesi güvenlidir `GarbageCollectionFinished` .</span><span class="sxs-lookup"><span data-stu-id="4fc50-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc50-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fc50-107">Requirements</span></span>  
 <span data-ttu-id="4fc50-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc50-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc50-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4fc50-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fc50-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4fc50-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc50-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc50-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc50-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fc50-112">See also</span></span>

- [<span data-ttu-id="4fc50-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fc50-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4fc50-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fc50-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
