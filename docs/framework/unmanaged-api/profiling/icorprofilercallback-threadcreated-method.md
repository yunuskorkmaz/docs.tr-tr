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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107776"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="cfb53-102">ICorProfilerCallback::ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfb53-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="cfb53-103">Profil Oluşturucu, bir iş parçacığı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="cfb53-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfb53-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="cfb53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfb53-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cfb53-106">[in] Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="cfb53-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb53-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfb53-107">Remarks</span></span>  
 <span data-ttu-id="cfb53-108">`threadId` Değeri hemen geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfb53-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb53-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfb53-109">Requirements</span></span>  
 <span data-ttu-id="cfb53-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb53-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfb53-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfb53-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb53-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cfb53-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cfb53-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb53-114">See also</span></span>

- [<span data-ttu-id="cfb53-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfb53-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cfb53-116">ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfb53-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
