---
title: "ICorProfilerCallback::RuntimeSuspendAborted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="630a5-102">ICorProfilerCallback::RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="630a5-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="630a5-103">Profil Oluşturucu çalışma zamanı meydana çalışma zamanı askıya durdurdu bildirir.</span><span class="sxs-lookup"><span data-stu-id="630a5-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="630a5-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="630a5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="630a5-105">Remarks</span></span>  
 <span data-ttu-id="630a5-106">İki iş parçacığı aynı anda çalışma zamanı askıya çalışırsanız, çalışma zamanı askıya iptal.</span><span class="sxs-lookup"><span data-stu-id="630a5-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="630a5-107">Her iki [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) geri çağırma veya `RuntimeSuspendAborted` geri çağırma tek iş parçacığı şu sunuculara oluşacak bir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="630a5-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="630a5-108">`RuntimeSuspendAborted` Geri çağırma aynı iş parçacığı üzerinde gerçekleşmesi için garanti `RuntimeSuspendStarted` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="630a5-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="630a5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="630a5-109">Requirements</span></span>  
 <span data-ttu-id="630a5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="630a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="630a5-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="630a5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="630a5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="630a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="630a5-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="630a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630a5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="630a5-114">See Also</span></span>  
 [<span data-ttu-id="630a5-115">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="630a5-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
