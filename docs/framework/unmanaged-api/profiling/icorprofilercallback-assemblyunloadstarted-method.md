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
ms.openlocfilehash: 80054a8292c69b957664cb3573b0a8694c7f9fd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500409"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="878fd-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="878fd-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="878fd-103">Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="878fd-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="878fd-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="878fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="878fd-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="878fd-106">\[' de], kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="878fd-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="878fd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="878fd-107">Remarks</span></span>  
 <span data-ttu-id="878fd-108">Değeri, `assemblyId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil — bu `AssemblyUnloadStarted` derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="878fd-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878fd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="878fd-109">Requirements</span></span>  
 <span data-ttu-id="878fd-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="878fd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="878fd-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="878fd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="878fd-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="878fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="878fd-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="878fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878fd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="878fd-114">See also</span></span>

- [<span data-ttu-id="878fd-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="878fd-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="878fd-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="878fd-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
