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
ms.openlocfilehash: d3949189a72583ebb50b67a270694a31f1eb23dc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503217"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="65496-102">ICorProfilerCallback::RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65496-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="65496-103">Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="65496-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65496-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="65496-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65496-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65496-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="65496-106">'ndaki Devam eden iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="65496-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65496-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65496-107">Requirements</span></span>  
 <span data-ttu-id="65496-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65496-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65496-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65496-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65496-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65496-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65496-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65496-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65496-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65496-112">See also</span></span>

- [<span data-ttu-id="65496-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65496-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="65496-114">RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65496-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
