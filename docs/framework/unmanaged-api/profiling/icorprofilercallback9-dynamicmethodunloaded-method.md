---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi'
title: ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: bc7f95b5101658c93eeb9fcef51e9c0f1bd2f2bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760203"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="a18a1-103">ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="a18a1-103">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="a18a1-104">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="a18a1-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="a18a1-105">Dinamik bir yöntem atık olarak toplandığında ve sonra kaldırıldığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="a18a1-105">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18a1-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a18a1-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a18a1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a18a1-107">Parameters</span></span>  

<span data-ttu-id="a18a1-108">`functionId` 'ndaki Atık olarak toplanmış ve kaldırılmış olan bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a18a1-108">`functionId` [in] The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="a18a1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a18a1-109">Requirements</span></span>  

 <span data-ttu-id="a18a1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a18a1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a18a1-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a18a1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a18a1-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a18a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a18a1-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a18a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18a1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a18a1-114">See also</span></span>

- [<span data-ttu-id="a18a1-115">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="a18a1-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a18a1-116">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="a18a1-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a18a1-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a18a1-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="a18a1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="a18a1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
