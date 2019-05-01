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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f8eca3e8eb755e31e704e557ae614a6e5c1f534
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915280"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="b0fdc-102">ICorProfilerCallback::ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0fdc-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="b0fdc-103">Profil Oluşturucu, bir iş parçacığı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="b0fdc-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0fdc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0fdc-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b0fdc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0fdc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b0fdc-106">[in] Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="b0fdc-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0fdc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0fdc-107">Remarks</span></span>  
 <span data-ttu-id="b0fdc-108">`threadId` Değeri hemen geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b0fdc-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0fdc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0fdc-109">Requirements</span></span>  
 <span data-ttu-id="b0fdc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0fdc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0fdc-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0fdc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0fdc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0fdc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0fdc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0fdc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fdc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0fdc-114">See also</span></span>

- [<span data-ttu-id="b0fdc-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0fdc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b0fdc-116">ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0fdc-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
