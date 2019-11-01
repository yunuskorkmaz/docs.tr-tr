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
ms.openlocfilehash: 05a788179ff40a6889ed613b5f8659dd3f8e066f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196328"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="23f68-102">ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="23f68-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="23f68-103">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="23f68-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="23f68-104">Dinamik bir yöntem atık olarak toplandığında ve sonra kaldırıldığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="23f68-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23f68-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23f68-106">Parameters</span></span>  
<span data-ttu-id="23f68-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="23f68-107">[in] `functionId`</span></span>  
<span data-ttu-id="23f68-108">Atık olarak toplanmış ve kaldırılmış olan bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="23f68-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="23f68-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23f68-109">Requirements</span></span>  
 <span data-ttu-id="23f68-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f68-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f68-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="23f68-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23f68-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="23f68-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f68-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23f68-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f68-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23f68-114">See also</span></span>

- [<span data-ttu-id="23f68-115">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="23f68-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="23f68-116">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="23f68-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="23f68-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23f68-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="23f68-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="23f68-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
