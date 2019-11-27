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
ms.openlocfilehash: 81c26214762fba1cac43e42adc1ee9909759972f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430316"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="0cd55-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cd55-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="0cd55-103">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="0cd55-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cd55-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0cd55-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cd55-105">Remarks</span></span>  
 <span data-ttu-id="0cd55-106">`RuntimeResumeFinished` geri çağrısının [ICorProfilerCallback:: RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında oluşması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="0cd55-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="0cd55-107">Ancak, [ICorProfilerCallback:: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırması ile aynı iş parçacığında oluşma garantisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0cd55-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd55-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cd55-108">Requirements</span></span>  
 <span data-ttu-id="0cd55-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cd55-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cd55-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0cd55-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cd55-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0cd55-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cd55-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cd55-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd55-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cd55-113">See also</span></span>

- [<span data-ttu-id="0cd55-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cd55-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
