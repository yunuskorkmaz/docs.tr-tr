---
title: ICorProfilerCallback::RuntimeThreadResumed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 57ad0bd3ed76376421d22a84c0863d36ec2707c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430274"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="e2f21-102">ICorProfilerCallback::RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2f21-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="e2f21-103">Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e2f21-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2f21-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2f21-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="e2f21-106">'ndaki Devam eden iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e2f21-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f21-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2f21-107">Requirements</span></span>  
 <span data-ttu-id="e2f21-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f21-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f21-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2f21-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2f21-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2f21-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2f21-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f21-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f21-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f21-112">See also</span></span>

- [<span data-ttu-id="e2f21-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2f21-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e2f21-114">RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2f21-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
