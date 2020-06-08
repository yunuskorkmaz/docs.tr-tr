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
ms.openlocfilehash: c63b91c39ded58ed208f6920c2bfaeba410c093c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499863"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="040b5-102">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="040b5-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="040b5-103">Profiler öğesine bir iş parçacığının yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="040b5-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="040b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="040b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="040b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="040b5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="040b5-106">'ndaki Yok edilmiş iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="040b5-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="040b5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="040b5-107">Remarks</span></span>  
 <span data-ttu-id="040b5-108">`threadId`Bu çağrı sırasında değer artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="040b5-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="040b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="040b5-109">Requirements</span></span>  
 <span data-ttu-id="040b5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="040b5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="040b5-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="040b5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="040b5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="040b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="040b5-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="040b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040b5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="040b5-114">See also</span></span>

- [<span data-ttu-id="040b5-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="040b5-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="040b5-116">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="040b5-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
