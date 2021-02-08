---
description: ': ICorProfilerCallback:: RuntimeResumeFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a8a38ff8372df9890239966c90175d72bda4b09d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788858"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="3f069-103">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f069-103">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="3f069-104">Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f069-104">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f069-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f069-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f069-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f069-106">Remarks</span></span>  

 <span data-ttu-id="3f069-107">`RuntimeResumeFinished`Geri aramanın, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağırması ile aynı iş parçacığında gerçekleşmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="3f069-107">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="3f069-108">Ancak, [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırması ile aynı iş parçacığında oluşma garantisi vardır.</span><span class="sxs-lookup"><span data-stu-id="3f069-108">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f069-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f069-109">Requirements</span></span>  

 <span data-ttu-id="3f069-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f069-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f069-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3f069-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f069-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f069-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f069-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f069-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f069-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f069-114">See also</span></span>

- [<span data-ttu-id="3f069-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f069-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
