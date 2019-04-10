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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0748802599926f4ec218362e6f7d086aab2d8f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080234"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="1ecdb-102">ICorProfilerCallback::RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ecdb-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="1ecdb-103">Belirtilen iş parçacığını askıya alındı veya askıya alınması için profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecdb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ecdb-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ecdb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ecdb-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1ecdb-106">[in] Askıya alındı iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ecdb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ecdb-107">Remarks</span></span>  
 <span data-ttu-id="1ecdb-108">`RuntimeThreadSuspended` Bildirim arasında istediğiniz zaman meydana gelebilir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) ve ilişkili [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="1ecdb-109">Bildirimler arasında gerçekleşen [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve `RuntimeResumeStarted` çalışmakta olan, iş parçacıklarını yönetilmeyen kod ve çalışma zamanı girişte askıya alındığından.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="1ecdb-110">Genellikle, yalnızca bir iş parçacığı askıda sonra bu geri çağırma gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="1ecdb-111">Ancak, yürütülmekte olan iş parçacığını (Bu geri çağırma çağıran iş parçacığının) askıya alınmış bir ise, bu geri arama yalnızca iş parçacığını askıya alınmadan önce ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ecdb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ecdb-112">Requirements</span></span>  
 <span data-ttu-id="1ecdb-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ecdb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ecdb-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ecdb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ecdb-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ecdb-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1ecdb-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1ecdb-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ecdb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ecdb-117">See also</span></span>

- [<span data-ttu-id="1ecdb-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ecdb-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1ecdb-119">RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ecdb-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
