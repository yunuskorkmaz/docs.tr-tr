---
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
ms.openlocfilehash: 509d6cd2e65c2eb8c92f6d79deae9e01e75298f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433451"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="d6fca-102">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6fca-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="d6fca-103">Profil oluşturucuyu belirtilen iş parçacığının askıya alındığını veya askıya alınmayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d6fca-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6fca-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6fca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6fca-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d6fca-106">'ndaki Askıya alınmış olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d6fca-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6fca-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6fca-107">Remarks</span></span>  
 <span data-ttu-id="d6fca-108">`RuntimeThreadSuspended` bildirimi [ICorProfilerCallback:: RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) ve Ilişkili [ICorProfilerCallback:: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında herhangi bir zaman oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="d6fca-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="d6fca-109">[ICorProfilerCallback:: RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve `RuntimeResumeStarted` arasında oluşan bildirimler, yönetilmeyen kodda çalışan ve çalışma zamanına giriş yapıldığında askıya alınan iş parçacıklarında yapılır.</span><span class="sxs-lookup"><span data-stu-id="d6fca-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="d6fca-110">Genellikle, bu geri çağrı yalnızca bir iş parçacığı askıya alındıktan sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="d6fca-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="d6fca-111">Ancak, şu anda yürütülmekte olan iş parçacığı (Bu geri çağırma işlemini çağıran iş parçacığı) askıya alınmışsa, bu geri arama iş parçacığı askıya alınmadan hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d6fca-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6fca-112">Requirements</span></span>  
 <span data-ttu-id="d6fca-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6fca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fca-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d6fca-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6fca-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d6fca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6fca-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fca-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6fca-117">See also</span></span>

- [<span data-ttu-id="d6fca-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6fca-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d6fca-119">RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6fca-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
