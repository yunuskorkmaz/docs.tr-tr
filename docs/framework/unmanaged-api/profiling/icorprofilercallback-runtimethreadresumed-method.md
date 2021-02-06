---
description: ': ICorProfilerCallback:: Runtimethreadsürdürülme yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a01be057bb442c69890d3b1cb4ebe1f861d2518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657352"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="9d1de-103">ICorProfilerCallback::RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d1de-103">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="9d1de-104">Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d1de-104">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d1de-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d1de-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d1de-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d1de-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="9d1de-107">'ndaki Devam eden iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9d1de-107">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d1de-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d1de-108">Requirements</span></span>  

 <span data-ttu-id="9d1de-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d1de-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d1de-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d1de-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d1de-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d1de-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d1de-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d1de-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1de-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d1de-113">See also</span></span>

- [<span data-ttu-id="9d1de-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d1de-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9d1de-115">RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d1de-115">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
