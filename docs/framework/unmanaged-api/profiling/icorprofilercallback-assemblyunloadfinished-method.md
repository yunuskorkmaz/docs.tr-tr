---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866630"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="84451-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84451-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="84451-103">Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="84451-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84451-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84451-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84451-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84451-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="84451-106">\[içindeki], bellekten kaldırılan derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84451-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="84451-107">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="84451-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="84451-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84451-108">Remarks</span></span>  
 <span data-ttu-id="84451-109">`assemblyId` değeri, [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) yöntemi döndürüldüğünden bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="84451-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="84451-110">Derlemeyi kaldırma işleminin bazı bölümleri `AssemblyUnloadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="84451-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="84451-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="84451-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="84451-112">Ancak `hrStatus` başarılı bir HRESULT, yalnızca derlemeyi kaldırma ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84451-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84451-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84451-113">Requirements</span></span>  
 <span data-ttu-id="84451-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84451-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84451-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="84451-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84451-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84451-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84451-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84451-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84451-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84451-118">See also</span></span>

- [<span data-ttu-id="84451-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84451-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
