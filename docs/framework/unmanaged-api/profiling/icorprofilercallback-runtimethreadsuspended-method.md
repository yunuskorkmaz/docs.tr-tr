---
title: "ICorProfilerCallback::RuntimeThreadSuspended Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f22e9a6ed8c62256bb3e614dbc1278dea24d4e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="df6d8-102">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df6d8-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="df6d8-103">Profil Oluşturucu, belirtilen iş parçacığı askıya alındı veya askıya alınmasına olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="df6d8-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df6d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df6d8-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df6d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df6d8-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="df6d8-106">[in] Askıya alındı iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="df6d8-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df6d8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df6d8-107">Remarks</span></span>  
 <span data-ttu-id="df6d8-108">`RuntimeThreadSuspended` Bildirim arasında herhangi bir zaman meydana gelebilir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) ve ilişkili [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="df6d8-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="df6d8-109">Arasında oluşan bildirimleri [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve `RuntimeResumeStarted` çalışmakta olan içinde iş parçacıklarını yönetilmeyen kod ve çalışma zamanının girişte askıya alınan olursunuz.</span><span class="sxs-lookup"><span data-stu-id="df6d8-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="df6d8-110">Genellikle, yalnızca bir iş parçacığı askıya sonra bu geri çağırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="df6d8-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="df6d8-111">Ancak, şu anda yürütülen iş parçacığı (Bu geri çağırma adlı iş parçacığı) askıya alınmış bir ise, bu geri çağırma yalnızca iş parçacığı askıya alınmadan önce meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="df6d8-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df6d8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df6d8-112">Requirements</span></span>  
 <span data-ttu-id="df6d8-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df6d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df6d8-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df6d8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df6d8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df6d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df6d8-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df6d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6d8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df6d8-117">See Also</span></span>  
 [<span data-ttu-id="df6d8-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df6d8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="df6d8-119">RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df6d8-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
