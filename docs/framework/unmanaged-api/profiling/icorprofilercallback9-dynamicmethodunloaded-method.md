---
title: ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498979"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="c29d9-102">ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="c29d9-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="c29d9-103">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c29d9-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="c29d9-104">Dinamik bir yöntem atık olarak toplandığında ve sonra kaldırıldığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="c29d9-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c29d9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c29d9-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c29d9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c29d9-106">Parameters</span></span>  
<span data-ttu-id="c29d9-107">'ndaki`functionId`</span><span class="sxs-lookup"><span data-stu-id="c29d9-107">[in] `functionId`</span></span>  
<span data-ttu-id="c29d9-108">Atık olarak toplanmış ve kaldırılmış olan bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c29d9-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="c29d9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c29d9-109">Requirements</span></span>  
 <span data-ttu-id="c29d9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c29d9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c29d9-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c29d9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c29d9-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c29d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c29d9-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c29d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c29d9-114">See also</span></span>

- [<span data-ttu-id="c29d9-115">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="c29d9-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="c29d9-116">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="c29d9-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="c29d9-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c29d9-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="c29d9-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="c29d9-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
