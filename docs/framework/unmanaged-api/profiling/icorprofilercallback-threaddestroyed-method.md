---
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
ms.openlocfilehash: 07041d06668d474a3d30968fb623854a24ebf0eb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865830"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="191c1-102">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="191c1-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="191c1-103">Profiler öğesine bir iş parçacığının yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="191c1-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="191c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="191c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="191c1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="191c1-106">'ndaki Yok edilmiş iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="191c1-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="191c1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="191c1-107">Remarks</span></span>  
 <span data-ttu-id="191c1-108">`threadId` değeri bu çağrı sırasında artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="191c1-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="191c1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="191c1-109">Requirements</span></span>  
 <span data-ttu-id="191c1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="191c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="191c1-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="191c1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="191c1-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="191c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="191c1-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="191c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191c1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191c1-114">See also</span></span>

- [<span data-ttu-id="191c1-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="191c1-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="191c1-116">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="191c1-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
