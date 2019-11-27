---
title: ICorProfilerCallback::AssemblyUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 3abf944df3619256791882bf61dfc4072b642c54
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445134"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="b226a-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b226a-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="b226a-103">Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b226a-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b226a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b226a-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b226a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b226a-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="b226a-106">'ndaki Kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b226a-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b226a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b226a-107">Remarks</span></span>  
 <span data-ttu-id="b226a-108">`assemblyId` değeri `AssemblyUnloadStarted` yöntemi çağrıldıktan sonra bir bilgi isteği için geçerli değil — bu derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="b226a-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b226a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b226a-109">Requirements</span></span>  
 <span data-ttu-id="b226a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b226a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b226a-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b226a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b226a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b226a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b226a-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b226a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b226a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b226a-114">See also</span></span>

- [<span data-ttu-id="b226a-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b226a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b226a-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b226a-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
