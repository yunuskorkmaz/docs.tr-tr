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
ms.openlocfilehash: 0a677e33950f178b916a5e9e9cbb7bd918c1349b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866617"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="0b5d3-102">ICorProfilerCallback::AssemblyUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b5d3-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="0b5d3-103">Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b5d3-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b5d3-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b5d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b5d3-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="0b5d3-106">\[içindeki], bellekten kaldırılan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b5d3-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b5d3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b5d3-107">Remarks</span></span>  
 <span data-ttu-id="0b5d3-108">`assemblyId` değeri `AssemblyUnloadStarted` yöntemi çağrıldıktan sonra bir bilgi isteği için geçerli değil — bu derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="0b5d3-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b5d3-109">Requirements</span></span>  
 <span data-ttu-id="0b5d3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5d3-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0b5d3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b5d3-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b5d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b5d3-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5d3-114">See also</span></span>

- [<span data-ttu-id="0b5d3-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b5d3-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0b5d3-116">AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b5d3-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
