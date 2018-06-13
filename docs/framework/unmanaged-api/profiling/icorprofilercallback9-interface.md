---
title: ICorProfilerCallback9 arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452383"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="6df24-102">ICorProfilerCallback9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df24-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="6df24-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="6df24-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="6df24-104">Öğesinin bir alt [ICorProfilerCallback8](icorprofilercallback8-interface.md) profil oluşturucu dinamik yöntemi toplanır ve daha sonra kaldırıldığında çöp olduğunu bildirmek için ortak dil çalışma zamanı tarafından kullanılan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df24-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6df24-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6df24-105">Methods</span></span>  
  
|<span data-ttu-id="6df24-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6df24-106">Method</span></span>|<span data-ttu-id="6df24-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6df24-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6df24-108">DynamicMethodUnloaded yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df24-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="6df24-109">Profil Oluşturucu dinamik yöntemi toplanır ve daha sonra kaldırıldığında çöp olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6df24-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6df24-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df24-110">Requirements</span></span>  
 <span data-ttu-id="6df24-111">**Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df24-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df24-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6df24-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="6df24-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6df24-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6df24-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6df24-114">See Also</span></span>  
<span data-ttu-id="6df24-115">[Profil oluşturma arabirimleri](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="6df24-115">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
<span data-ttu-id="6df24-116">[ICorProfilerCallback8 arabirimi](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="6df24-116">[ICorProfilerCallback8 Interface](icorprofilercallback9-interface.md) </span></span>  
<span data-ttu-id="6df24-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span><span class="sxs-lookup"><span data-stu-id="6df24-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span></span>  
[<span data-ttu-id="6df24-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df24-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
