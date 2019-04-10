---
title: ICorProfilerCallback9 Arabirimi
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
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227762"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="d0c72-102">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0c72-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="d0c72-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="d0c72-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="d0c72-104">Öğesinin [Icorprofilercallback8](icorprofilercallback8-interface.md) profil oluşturucu dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirmek için ortak dil çalışma zamanı tarafından kullanılan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0c72-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0c72-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0c72-105">Methods</span></span>  
  
|<span data-ttu-id="d0c72-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d0c72-106">Method</span></span>|<span data-ttu-id="d0c72-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c72-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0c72-108">DynamicMethodUnloaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0c72-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="d0c72-109">Profil Oluşturucu, dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d0c72-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0c72-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0c72-110">Requirements</span></span>  
 <span data-ttu-id="d0c72-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0c72-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0c72-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0c72-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
**<span data-ttu-id="d0c72-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d0c72-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a><span data-ttu-id="d0c72-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c72-114">See also</span></span>

- [<span data-ttu-id="d0c72-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d0c72-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d0c72-116">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0c72-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="d0c72-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0c72-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="d0c72-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0c72-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
