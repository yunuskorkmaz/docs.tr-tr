---
title: ICorProfilerCallback::ThreadCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 1d8aa231f65bad88806ee9b1d3c5df978c9740a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446931"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="6de97-102">ICorProfilerCallback::ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de97-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="6de97-103">Profil oluşturucuyu bir iş parçacığının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6de97-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6de97-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="6de97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6de97-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="6de97-106">'ndaki Oluşturulan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6de97-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de97-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6de97-107">Remarks</span></span>  
 <span data-ttu-id="6de97-108">`threadId` değeri hemen geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6de97-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de97-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6de97-109">Requirements</span></span>  
 <span data-ttu-id="6de97-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de97-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de97-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6de97-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6de97-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6de97-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6de97-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de97-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de97-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6de97-114">See also</span></span>

- [<span data-ttu-id="6de97-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6de97-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6de97-116">ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6de97-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
