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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4929d9aaf7de9af72ec5ba93f5d7e35c712ac6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451707"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="a0af0-102">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0af0-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="a0af0-103">Profil Oluşturucu, bir iş parçacığı yok olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a0af0-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0af0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0af0-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0af0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0af0-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a0af0-106">[in] Yok edildi iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="a0af0-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0af0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0af0-107">Remarks</span></span>  
 <span data-ttu-id="a0af0-108">`threadId` Değeri geçerli artık çağrısı zaman.</span><span class="sxs-lookup"><span data-stu-id="a0af0-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0af0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0af0-109">Requirements</span></span>  
 <span data-ttu-id="a0af0-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0af0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0af0-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0af0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0af0-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0af0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0af0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0af0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0af0-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0af0-114">See Also</span></span>  
 [<span data-ttu-id="a0af0-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0af0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a0af0-116">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0af0-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
