---
title: ICorProfilerCallback2::HandleCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 6cd931f6c680a07327915ab4680702af298ca1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717324"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="6d723-102">ICorProfilerCallback2::HandleCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d723-102">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="6d723-103">Kod Profilcisi bir çöp toplama tutamacının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d723-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d723-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d723-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d723-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d723-105">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="6d723-106">'ndaki Çöp toplama tanıtıcısının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6d723-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="6d723-107">'ndaki Çöp toplama tanıtıcısının oluşturulduğu nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6d723-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d723-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d723-108">Requirements</span></span>  

 <span data-ttu-id="6d723-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d723-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d723-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d723-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d723-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d723-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d723-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d723-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d723-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d723-113">See also</span></span>

- [<span data-ttu-id="6d723-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d723-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6d723-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d723-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
