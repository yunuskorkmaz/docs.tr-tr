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
ms.openlocfilehash: e7bd07205a87ecefb658e01db17100a48681b54b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732040"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="fdf81-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdf81-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="fdf81-103">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="fdf81-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf81-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fdf81-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fdf81-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdf81-105">Remarks</span></span>  

 <span data-ttu-id="fdf81-106">`RuntimeResumeFinished`Geri aramanın, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında gerçekleşmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="fdf81-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="fdf81-107">Ancak, [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırması ile aynı iş parçacığında oluşma garantisi vardır.</span><span class="sxs-lookup"><span data-stu-id="fdf81-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdf81-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdf81-108">Requirements</span></span>  

 <span data-ttu-id="fdf81-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdf81-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf81-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fdf81-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdf81-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fdf81-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdf81-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf81-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdf81-113">See also</span></span>

- [<span data-ttu-id="fdf81-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdf81-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
