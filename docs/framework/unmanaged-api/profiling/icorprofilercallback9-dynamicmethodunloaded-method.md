---
title: ICorProfilerCallback9::DynamicMethodUnloaded yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 680bd351a64632e67432ee03352ee7caa8f4b2d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780381"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="ba77d-102">ICorProfilerCallback9::DynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba77d-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="ba77d-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="ba77d-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="ba77d-104">Profil Oluşturucu, dinamik bir yöntem atık toplanan ve daha sonra kaldırıldığında olduğunda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="ba77d-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba77d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba77d-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba77d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba77d-106">Parameters</span></span>  
<span data-ttu-id="ba77d-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="ba77d-107">[in] `functionId`</span></span>  
<span data-ttu-id="ba77d-108">Atık toplanan ve yüklenmemiş olan bellek içi işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ba77d-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="ba77d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba77d-109">Requirements</span></span>  
 <span data-ttu-id="ba77d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba77d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba77d-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ba77d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba77d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba77d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba77d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba77d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba77d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba77d-114">See also</span></span>

- [<span data-ttu-id="ba77d-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba77d-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="ba77d-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba77d-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="ba77d-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba77d-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="ba77d-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="ba77d-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
