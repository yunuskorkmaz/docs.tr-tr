---
description: ': ICorProfilerCallback:: AssemblyUnloadStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 91c0b6a600a1c7c12905a7a9817e6e7e9601c3c0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759475"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="92f83-103">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92f83-103">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="92f83-104">Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="92f83-104">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f83-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92f83-105">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92f83-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92f83-106">Parameters</span></span>

<span data-ttu-id="92f83-107">`assemblyId` 'ndaki Kaldırılmakta olan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92f83-107">`assemblyId` [in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="92f83-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92f83-108">Remarks</span></span>  

 <span data-ttu-id="92f83-109">Değeri, `assemblyId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil — bu `AssemblyUnloadStarted` derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="92f83-109">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f83-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92f83-110">Requirements</span></span>  

 <span data-ttu-id="92f83-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f83-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f83-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92f83-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92f83-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92f83-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f83-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f83-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92f83-115">See also</span></span>

- [<span data-ttu-id="92f83-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92f83-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="92f83-117">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92f83-117">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
