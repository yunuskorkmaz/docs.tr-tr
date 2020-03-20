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
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175128"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="93ed8-102">ICorProfilerCallback::ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93ed8-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="93ed8-103">Profil oluşturucuya bir iş parçacığı oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="93ed8-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ed8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93ed8-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="93ed8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93ed8-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="93ed8-106">[içinde] Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="93ed8-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93ed8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93ed8-107">Remarks</span></span>  
 <span data-ttu-id="93ed8-108">Değer `threadId` hemen geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="93ed8-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ed8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93ed8-109">Requirements</span></span>  
 <span data-ttu-id="93ed8-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93ed8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ed8-111">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93ed8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93ed8-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93ed8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93ed8-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ed8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ed8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93ed8-114">See also</span></span>

- [<span data-ttu-id="93ed8-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93ed8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="93ed8-116">ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93ed8-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
