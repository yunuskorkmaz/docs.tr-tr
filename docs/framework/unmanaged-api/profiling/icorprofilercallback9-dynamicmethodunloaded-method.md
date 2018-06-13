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
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452409"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="f2ae3-102">ICorProfilerCallback9::DynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2ae3-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="f2ae3-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="f2ae3-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="f2ae3-104">Profil Oluşturucu dinamik yöntemi toplanır ve daha sonra kaldırıldığında çöp olduğunda uyarır.</span><span class="sxs-lookup"><span data-stu-id="f2ae3-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ae3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2ae3-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2ae3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2ae3-106">Parameters</span></span>  
<span data-ttu-id="f2ae3-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="f2ae3-107">[in] `functionId`</span></span>  
<span data-ttu-id="f2ae3-108">Çöp bırakıldı bellek içi işlevi tanıtıcısı toplanır ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f2ae3-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="f2ae3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2ae3-109">Requirements</span></span>  
 <span data-ttu-id="f2ae3-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ae3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ae3-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2ae3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2ae3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2ae3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2ae3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ae3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ae3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2ae3-114">See Also</span></span>  
[<span data-ttu-id="f2ae3-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2ae3-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[<span data-ttu-id="f2ae3-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2ae3-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
<span data-ttu-id="f2ae3-117">[ICorProfilerCallback9 arabirimi](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="f2ae3-117">[ICorProfilerCallback9 Interface](icorprofilercallback9-interface.md) </span></span>  
[<span data-ttu-id="f2ae3-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="f2ae3-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
