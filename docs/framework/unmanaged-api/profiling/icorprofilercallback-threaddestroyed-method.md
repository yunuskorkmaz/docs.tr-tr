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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041632"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="d59bc-102">ICorProfilerCallback::ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d59bc-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>
<span data-ttu-id="d59bc-103">Profil Oluşturucu, bir iş parçacığı yok edildi bildirir.</span><span class="sxs-lookup"><span data-stu-id="d59bc-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d59bc-104">Syntax</span></span>  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d59bc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d59bc-106">[in] Yok edilmiş iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="d59bc-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d59bc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d59bc-107">Remarks</span></span>  
 <span data-ttu-id="d59bc-108">`threadId` Değeri artık geçerli değil Bu çağrı anda.</span><span class="sxs-lookup"><span data-stu-id="d59bc-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59bc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d59bc-109">Requirements</span></span>  
 <span data-ttu-id="d59bc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59bc-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d59bc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d59bc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d59bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d59bc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59bc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d59bc-114">See also</span></span>

- [<span data-ttu-id="d59bc-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d59bc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d59bc-116">ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d59bc-116">ThreadCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
