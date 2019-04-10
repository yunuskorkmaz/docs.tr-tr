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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 810875d1b91265fe886ce3cd11970cad7fee122d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228867"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="1bfb8-102">ICorProfilerCallback::RuntimeThreadResumed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bfb8-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="1bfb8-103">Profil Oluşturucu, belirtilen iş parçacığını askıya sonra ettirdi bildirir.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bfb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bfb8-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bfb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bfb8-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1bfb8-106">[in] Sürdürüldü iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bfb8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bfb8-107">Requirements</span></span>  
 <span data-ttu-id="1bfb8-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bfb8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bfb8-109">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bfb8-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bfb8-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bfb8-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1bfb8-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1bfb8-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1bfb8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-112">See also</span></span>

- [<span data-ttu-id="1bfb8-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bfb8-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1bfb8-114">RuntimeThreadSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bfb8-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
