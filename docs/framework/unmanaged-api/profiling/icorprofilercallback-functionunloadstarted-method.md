---
description: ': ICorProfilerCallback:: FunctionUnloadStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ce3cf406b8d2f91613bce878db8a4f9e0838c052
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760437"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="e5895-103">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5895-103">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>

<span data-ttu-id="e5895-104">Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5895-104">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5895-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5895-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="e5895-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5895-106">Parameters</span></span>

<span data-ttu-id="e5895-107">`functionId` 'ndaki Kaldırılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e5895-107">`functionId` [in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5895-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5895-108">Remarks</span></span>  

 <span data-ttu-id="e5895-109">`functionId`Bu yöntem çağırana döndüğünde parametrenin değeri artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e5895-109">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5895-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5895-110">Requirements</span></span>  

 <span data-ttu-id="e5895-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5895-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5895-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e5895-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5895-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5895-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5895-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5895-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5895-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5895-115">See also</span></span>

- [<span data-ttu-id="e5895-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5895-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
