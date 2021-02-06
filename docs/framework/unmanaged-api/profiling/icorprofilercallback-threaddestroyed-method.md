---
description: ': ICorProfilerCallback:: Threadyok etme yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ThreadDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 63c8c4c523cb398bd7c766fc41bc669a2d74045e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657199"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="dcdb9-103">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcdb9-103">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="dcdb9-104">Profiler öğesine bir iş parçacığının yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="dcdb9-104">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdb9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcdb9-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcdb9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcdb9-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="dcdb9-107">'ndaki Yok edilmiş iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dcdb9-107">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcdb9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcdb9-108">Remarks</span></span>  

 <span data-ttu-id="dcdb9-109">`threadId`Bu çağrı sırasında değer artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="dcdb9-109">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdb9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcdb9-110">Requirements</span></span>  

 <span data-ttu-id="dcdb9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdb9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdb9-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dcdb9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dcdb9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dcdb9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcdb9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdb9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdb9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcdb9-115">See also</span></span>

- [<span data-ttu-id="dcdb9-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcdb9-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="dcdb9-117">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcdb9-117">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
