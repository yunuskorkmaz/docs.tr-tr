---
title: "ICorProfilerCallback::RuntimeThreadSuspended Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadSuspended
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d2ab0244e898a60db8fe392ccbd8c0ebfd5523
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="12172-102">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12172-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="12172-103">Profil Oluşturucu, belirtilen iş parçacığı askıya alındı veya askıya alınmasına olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="12172-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12172-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12172-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12172-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12172-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="12172-106">[in] Askıya alındı iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="12172-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12172-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12172-107">Remarks</span></span>  
 <span data-ttu-id="12172-108">`RuntimeThreadSuspended` Bildirim arasında herhangi bir zaman meydana gelebilir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) ve ilişkili [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="12172-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="12172-109">Arasında oluşan bildirimleri [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve `RuntimeResumeStarted` çalışmakta olan içinde iş parçacıklarını yönetilmeyen kod ve çalışma zamanının girişte askıya alınan olursunuz.</span><span class="sxs-lookup"><span data-stu-id="12172-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="12172-110">Genellikle, yalnızca bir iş parçacığı askıya sonra bu geri çağırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="12172-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="12172-111">Ancak, şu anda yürütülen iş parçacığı (Bu geri çağırma adlı iş parçacığı) askıya alınmış bir ise, bu geri çağırma yalnızca iş parçacığı askıya alınmadan önce meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="12172-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12172-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12172-112">Requirements</span></span>  
 <span data-ttu-id="12172-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12172-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12172-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12172-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12172-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12172-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12172-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12172-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12172-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12172-117">See Also</span></span>  
 [<span data-ttu-id="12172-118">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="12172-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="12172-119">RuntimeThreadResumed yöntemi</span><span class="sxs-lookup"><span data-stu-id="12172-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
