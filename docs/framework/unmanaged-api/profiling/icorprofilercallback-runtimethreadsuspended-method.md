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
ms.openlocfilehash: 33a39cf2781f49ff0e31989831c4c9829889ec3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732009"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="79fed-102">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79fed-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>

<span data-ttu-id="79fed-103">Profil oluşturucuyu belirtilen iş parçacığının askıya alındığını veya askıya alınmayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="79fed-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79fed-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79fed-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79fed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79fed-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="79fed-106">'ndaki Askıya alınmış olan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="79fed-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79fed-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79fed-107">Remarks</span></span>  

 <span data-ttu-id="79fed-108">`RuntimeThreadSuspended`Bildirim, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) ve Ilişkili [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında herhangi bir zaman oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="79fed-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="79fed-109">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) arasında oluşan bildirimler ve `RuntimeResumeStarted` yönetilmeyen kodda çalışan ve çalışma zamanına giriş yapıldığında askıya alınan iş parçacıkları içindir.</span><span class="sxs-lookup"><span data-stu-id="79fed-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="79fed-110">Genellikle, bu geri çağrı yalnızca bir iş parçacığı askıya alındıktan sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="79fed-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="79fed-111">Ancak, şu anda yürütülmekte olan iş parçacığı (Bu geri çağırma işlemini çağıran iş parçacığı) askıya alınmışsa, bu geri arama iş parçacığı askıya alınmadan hemen önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="79fed-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79fed-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79fed-112">Requirements</span></span>  

 <span data-ttu-id="79fed-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79fed-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79fed-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="79fed-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79fed-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79fed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79fed-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79fed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fed-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79fed-117">See also</span></span>

- [<span data-ttu-id="79fed-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79fed-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="79fed-119">RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79fed-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
