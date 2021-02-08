---
description: ': ICorProfilerCallback:: Runtimesuspendadted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RuntimeSuspendAborted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 892de7ce0b4537f5526a58b6e70f66cd295be2df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788832"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="200c6-103">ICorProfilerCallback::RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="200c6-103">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>

<span data-ttu-id="200c6-104">Profil oluşturucuyu, çalışma zamanının oluşan çalışma zamanı askıya alma işlemi durdurdu olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="200c6-104">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200c6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="200c6-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="200c6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="200c6-106">Remarks</span></span>  

 <span data-ttu-id="200c6-107">Çalışma zamanı askıya alma, iki iş parçacığını eşzamanlı olarak askıya almaya çalışıyorsa durdurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="200c6-107">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="200c6-108">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) geri çağırması veya `RuntimeSuspendAborted` geri çağırma, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağrısından sonraki tek bir iş parçacığında gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="200c6-108">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="200c6-109">Geri aramanın, `RuntimeSuspendAborted` geri çağırma ile aynı iş parçacığında oluşması garanti edilir `RuntimeSuspendStarted` .</span><span class="sxs-lookup"><span data-stu-id="200c6-109">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200c6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="200c6-110">Requirements</span></span>  

 <span data-ttu-id="200c6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="200c6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="200c6-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="200c6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="200c6-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="200c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="200c6-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="200c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200c6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="200c6-115">See also</span></span>

- [<span data-ttu-id="200c6-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="200c6-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
