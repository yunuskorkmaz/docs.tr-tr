---
description: ': ICorProfilerCallback:: ThreadCreated yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8b6208856b78298f643161cd6bb78773ac86bc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657209"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="66101-103">ICorProfilerCallback::ThreadCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66101-103">ICorProfilerCallback::ThreadCreated Method</span></span>

<span data-ttu-id="66101-104">Profil oluşturucuyu bir iş parçacığının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="66101-104">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66101-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66101-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="66101-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66101-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="66101-107">'ndaki Oluşturulan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="66101-107">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66101-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66101-108">Remarks</span></span>  

 <span data-ttu-id="66101-109">`threadId`Değer hemen geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="66101-109">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66101-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66101-110">Requirements</span></span>  

 <span data-ttu-id="66101-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66101-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66101-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="66101-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66101-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66101-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66101-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66101-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66101-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66101-115">See also</span></span>

- [<span data-ttu-id="66101-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66101-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="66101-117">ThreadDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66101-117">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
