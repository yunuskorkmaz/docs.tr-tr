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
ms.openlocfilehash: 0996d7eb5b7354a67106ec7aa8818d5e4d46232e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717294"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="e6ef5-102">ICorProfilerCallback::RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6ef5-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="e6ef5-103">Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e6ef5-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ef5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e6ef5-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ef5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6ef5-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="e6ef5-106">'ndaki Devam eden iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e6ef5-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ef5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6ef5-107">Requirements</span></span>  

 <span data-ttu-id="e6ef5-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6ef5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6ef5-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e6ef5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6ef5-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6ef5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6ef5-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6ef5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ef5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ef5-112">See also</span></span>

- [<span data-ttu-id="e6ef5-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6ef5-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e6ef5-114">RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6ef5-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
