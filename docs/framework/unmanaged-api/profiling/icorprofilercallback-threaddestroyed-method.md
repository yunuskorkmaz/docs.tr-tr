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
ms.openlocfilehash: d4c45290b1ef4360e51b5ed8e1b0fac3dcdde727
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217347"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="61a6f-102">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61a6f-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="61a6f-103">Profil Oluşturucu, bir iş parçacığı yok edildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="61a6f-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61a6f-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61a6f-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="61a6f-106">[in] Yok edilmiş iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="61a6f-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61a6f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61a6f-107">Remarks</span></span>  
 <span data-ttu-id="61a6f-108">`threadId` Değeri artık geçerli değil Bu çağrı anda.</span><span class="sxs-lookup"><span data-stu-id="61a6f-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a6f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61a6f-109">Requirements</span></span>  
 <span data-ttu-id="61a6f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a6f-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61a6f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61a6f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a6f-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="61a6f-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="61a6f-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61a6f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61a6f-114">See also</span></span>

- [<span data-ttu-id="61a6f-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61a6f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="61a6f-116">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61a6f-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
