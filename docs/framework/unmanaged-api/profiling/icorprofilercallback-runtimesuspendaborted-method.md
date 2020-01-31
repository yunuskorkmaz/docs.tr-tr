---
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
ms.openlocfilehash: 285bdd3f2a96d3c6cb0039382d9944e48c49971a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865915"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="e1365-102">ICorProfilerCallback::RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1365-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="e1365-103">Profil oluşturucuyu, çalışma zamanının oluşan çalışma zamanı askıya alma işlemi durdurdu olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e1365-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1365-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1365-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1365-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1365-105">Remarks</span></span>  
 <span data-ttu-id="e1365-106">Çalışma zamanı askıya alma, iki iş parçacığını eşzamanlı olarak askıya almaya çalışıyorsa durdurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1365-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="e1365-107">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) geri araması veya `RuntimeSuspendAborted` geri çağırma, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağrısından sonraki tek bir iş parçacığında gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="e1365-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="e1365-108">`RuntimeSuspendAborted` geri çağrısının aynı iş parçacığında `RuntimeSuspendStarted` geri çağırmada oluşması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="e1365-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1365-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1365-109">Requirements</span></span>  
 <span data-ttu-id="e1365-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1365-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1365-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1365-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1365-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1365-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1365-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1365-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1365-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1365-114">See also</span></span>

- [<span data-ttu-id="e1365-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1365-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
