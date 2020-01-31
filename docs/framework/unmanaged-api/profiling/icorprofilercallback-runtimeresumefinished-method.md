---
title: ICorProfilerCallback::RuntimeResumeFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: 5cafbca75992a5fe8a7d3d95628e0018f1a2e8fa
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865954"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="5df84-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5df84-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="5df84-103">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="5df84-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5df84-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5df84-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5df84-105">Remarks</span></span>  
 <span data-ttu-id="5df84-106">`RuntimeResumeFinished` geri çağrısının [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında oluşması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="5df84-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="5df84-107">Ancak, [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırması ile aynı iş parçacığında oluşma garantisi vardır.</span><span class="sxs-lookup"><span data-stu-id="5df84-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df84-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5df84-108">Requirements</span></span>  
 <span data-ttu-id="5df84-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5df84-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df84-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5df84-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5df84-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5df84-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5df84-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df84-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df84-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df84-113">See also</span></span>

- [<span data-ttu-id="5df84-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5df84-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
