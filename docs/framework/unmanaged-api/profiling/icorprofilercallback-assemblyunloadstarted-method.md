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
ms.openlocfilehash: bb7dade1ccd46cb9e13d45468c2ca2a8b451b70b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700307"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="2c8ff-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c8ff-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="2c8ff-103">Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c8ff-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c8ff-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2c8ff-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c8ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c8ff-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="2c8ff-106">\[' de], kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c8ff-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c8ff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c8ff-107">Remarks</span></span>  

 <span data-ttu-id="2c8ff-108">Değeri, `assemblyId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil — bu `AssemblyUnloadStarted` derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="2c8ff-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c8ff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c8ff-109">Requirements</span></span>  

 <span data-ttu-id="2c8ff-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c8ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c8ff-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c8ff-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c8ff-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c8ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c8ff-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c8ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8ff-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c8ff-114">See also</span></span>

- [<span data-ttu-id="2c8ff-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c8ff-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2c8ff-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c8ff-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
