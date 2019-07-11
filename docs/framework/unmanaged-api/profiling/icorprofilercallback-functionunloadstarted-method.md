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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6dd7792fe298aa1950b23053a7c5cd576b62e7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755887"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="71fd7-102">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71fd7-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="71fd7-103">Profil Oluşturucu bir işlev kaldırmak çalışma zamanı başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="71fd7-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71fd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71fd7-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="71fd7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71fd7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="71fd7-106">[in] Boşaltılıyor işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="71fd7-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71fd7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71fd7-107">Remarks</span></span>  
 <span data-ttu-id="71fd7-108">Değerini `functionId` parametresi artık geçerli değil sonra bu yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="71fd7-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71fd7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71fd7-109">Requirements</span></span>  
 <span data-ttu-id="71fd7-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71fd7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71fd7-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71fd7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71fd7-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71fd7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71fd7-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71fd7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fd7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71fd7-114">See also</span></span>

- [<span data-ttu-id="71fd7-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71fd7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
