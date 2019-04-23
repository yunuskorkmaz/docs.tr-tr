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
ms.openlocfilehash: 96cdfb79c1573648173305d6ee789aa8db030ff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211016"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="e02b1-102">ICorProfilerCallback9::DynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02b1-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="e02b1-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="e02b1-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="e02b1-104">Profil Oluşturucu, dinamik bir yöntem atık toplanan ve daha sonra kaldırıldığında olduğunda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="e02b1-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e02b1-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e02b1-106">Parameters</span></span>  
<span data-ttu-id="e02b1-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="e02b1-107">[in] `functionId`</span></span>  
<span data-ttu-id="e02b1-108">Atık toplanan ve yüklenmemiş olan bellek içi işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e02b1-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="e02b1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e02b1-109">Requirements</span></span>  
 <span data-ttu-id="e02b1-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02b1-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e02b1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e02b1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e02b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e02b1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e02b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02b1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e02b1-114">See also</span></span>

- [<span data-ttu-id="e02b1-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02b1-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="e02b1-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02b1-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="e02b1-117">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02b1-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="e02b1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="e02b1-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
