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
ms.openlocfilehash: 243660d3159e3c8c1d052c08e9c7499e7065d301
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753334"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="39bea-103">ICorProfilerCallback9::D ynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="39bea-103">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="39bea-104">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="39bea-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="39bea-105">Dinamik bir yöntem atık olarak toplandığında ve sonra kaldırıldığında profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="39bea-105">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bea-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39bea-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39bea-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39bea-107">Parameters</span></span>  

<span data-ttu-id="39bea-108">'ndaki `functionId`</span><span class="sxs-lookup"><span data-stu-id="39bea-108">[in] `functionId`</span></span>  
<span data-ttu-id="39bea-109">Atık olarak toplanmış ve kaldırılmış olan bellek içi işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="39bea-109">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="39bea-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39bea-110">Requirements</span></span>  

 <span data-ttu-id="39bea-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39bea-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bea-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="39bea-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39bea-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39bea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39bea-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="39bea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bea-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39bea-115">See also</span></span>

- [<span data-ttu-id="39bea-116">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="39bea-116">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="39bea-117">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="39bea-117">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="39bea-118">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39bea-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="39bea-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="39bea-119">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
