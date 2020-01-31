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
ms.openlocfilehash: 2b228337a55d50b94da966b45877e2000b3c03e4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866334"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="746b7-102">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="746b7-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="746b7-103">Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="746b7-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="746b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="746b7-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="746b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="746b7-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="746b7-106">\[içinde] bellekten kaldırılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="746b7-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="746b7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="746b7-107">Remarks</span></span>  
 <span data-ttu-id="746b7-108">`functionId` parametresinin değeri, bu yöntem çağırana geri döndüğünde artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="746b7-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="746b7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="746b7-109">Requirements</span></span>  
 <span data-ttu-id="746b7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="746b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="746b7-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="746b7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="746b7-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="746b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="746b7-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="746b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746b7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="746b7-114">See also</span></span>

- [<span data-ttu-id="746b7-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="746b7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
