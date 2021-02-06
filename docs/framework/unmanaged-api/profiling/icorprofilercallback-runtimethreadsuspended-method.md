---
description: ': ICorProfilerCallback:: Runtimethreadaskıya alındı yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RuntimeThreadSuspended Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: f7c2f5baf5a320375d9a2606ca05b13d522336be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657340"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="1733e-103">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1733e-103">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>

<span data-ttu-id="1733e-104">Profil oluşturucuyu belirtilen iş parçacığının askıya alındığını veya askıya alınmayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1733e-104">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1733e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1733e-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1733e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1733e-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="1733e-107">'ndaki Askıya alınmış olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1733e-107">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1733e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1733e-108">Remarks</span></span>  

 <span data-ttu-id="1733e-109">`RuntimeThreadSuspended`Bildirim, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) ve Ilişkili [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında herhangi bir zaman oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="1733e-109">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="1733e-110">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) arasında oluşan bildirimler ve `RuntimeResumeStarted` yönetilmeyen kodda çalışan ve çalışma zamanına giriş yapıldığında askıya alınan iş parçacıkları içindir.</span><span class="sxs-lookup"><span data-stu-id="1733e-110">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="1733e-111">Genellikle, bu geri çağrı yalnızca bir iş parçacığı askıya alındıktan sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="1733e-111">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="1733e-112">Ancak, şu anda yürütülmekte olan iş parçacığı (Bu geri çağırma işlemini çağıran iş parçacığı) askıya alınmışsa, bu geri arama iş parçacığı askıya alınmadan hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1733e-112">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1733e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1733e-113">Requirements</span></span>  

 <span data-ttu-id="1733e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1733e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1733e-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1733e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1733e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1733e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1733e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1733e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1733e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1733e-118">See also</span></span>

- [<span data-ttu-id="1733e-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1733e-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1733e-120">RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1733e-120">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
