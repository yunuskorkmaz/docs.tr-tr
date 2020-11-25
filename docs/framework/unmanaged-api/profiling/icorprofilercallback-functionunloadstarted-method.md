---
title: ICorProfilerCallback::FunctionUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: bab8d446347646081cee635035e954da58c3550c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733886"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="b695a-102">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695a-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>

<span data-ttu-id="b695a-103">Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b695a-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b695a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b695a-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="b695a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b695a-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b695a-106">\[' de] kaldırılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b695a-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="b695a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b695a-107">Remarks</span></span>  

 <span data-ttu-id="b695a-108">`functionId`Bu yöntem çağırana döndüğünde parametrenin değeri artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b695a-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b695a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b695a-109">Requirements</span></span>  

 <span data-ttu-id="b695a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b695a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b695a-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b695a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b695a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b695a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b695a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b695a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b695a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b695a-114">See also</span></span>

- [<span data-ttu-id="b695a-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b695a-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
