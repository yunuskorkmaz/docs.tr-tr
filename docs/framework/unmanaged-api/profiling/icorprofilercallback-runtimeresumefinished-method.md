---
title: "ICorProfilerCallback::RuntimeResumeFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeResumeFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5d923db2d9614a4cf7ebc4f1d910a86fee85a0bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="70eb1-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb1-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="70eb1-103">Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını sürdürdü ve normal çalışmasına geri döndü bildirir.</span><span class="sxs-lookup"><span data-stu-id="70eb1-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70eb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70eb1-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="70eb1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70eb1-105">Remarks</span></span>  
 <span data-ttu-id="70eb1-106">`RuntimeResumeFinished` Geri çağırma aynı iş parçacığı üzerinde gerçekleşmesi için garanti edilmez [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="70eb1-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="70eb1-107">Ancak, iş parçacığı gerçekleşecek şekilde sağlanır [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="70eb1-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70eb1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70eb1-108">Requirements</span></span>  
 <span data-ttu-id="70eb1-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70eb1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70eb1-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70eb1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70eb1-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70eb1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70eb1-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70eb1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70eb1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70eb1-113">See Also</span></span>  
 [<span data-ttu-id="70eb1-114">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="70eb1-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
