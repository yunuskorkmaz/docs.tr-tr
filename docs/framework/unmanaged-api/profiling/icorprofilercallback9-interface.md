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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991997"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="0f1a9-102">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f1a9-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="0f1a9-103">[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="0f1a9-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="0f1a9-104">Öğesinin [Icorprofilercallback8](icorprofilercallback8-interface.md) profil oluşturucu dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirmek için ortak dil çalışma zamanı tarafından kullanılan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f1a9-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f1a9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f1a9-105">Methods</span></span>  
  
|<span data-ttu-id="0f1a9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f1a9-106">Method</span></span>|<span data-ttu-id="0f1a9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f1a9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f1a9-108">DynamicMethodUnloaded Metodu</span><span class="sxs-lookup"><span data-stu-id="0f1a9-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="0f1a9-109">Profil Oluşturucu, dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0f1a9-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f1a9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f1a9-110">Requirements</span></span>  
 <span data-ttu-id="0f1a9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f1a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f1a9-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f1a9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="0f1a9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f1a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0f1a9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1a9-114">See also</span></span>

- [<span data-ttu-id="0f1a9-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f1a9-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0f1a9-116">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f1a9-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="0f1a9-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f1a9-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="0f1a9-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f1a9-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
