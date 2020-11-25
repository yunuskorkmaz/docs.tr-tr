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
ms.openlocfilehash: 23b91a2a58c6e76b31b94e0fa3661dfbc8e18e33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712774"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="37a8b-102">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37a8b-102">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="37a8b-103">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="37a8b-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="37a8b-104">Ortak dil çalışma zamanı tarafından, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılabileceğini bildirmek için kullanılan bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback8](icorprofilercallback8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37a8b-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37a8b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="37a8b-105">Methods</span></span>  
  
|<span data-ttu-id="37a8b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="37a8b-106">Method</span></span>|<span data-ttu-id="37a8b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37a8b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37a8b-108">DynamicMethodUnloaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37a8b-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="37a8b-109">Profiler öğesine dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="37a8b-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37a8b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37a8b-110">Requirements</span></span>  

 <span data-ttu-id="37a8b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37a8b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37a8b-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="37a8b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="37a8b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37a8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="37a8b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37a8b-114">See also</span></span>

- [<span data-ttu-id="37a8b-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37a8b-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="37a8b-116">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37a8b-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="37a8b-117">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="37a8b-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="37a8b-118">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="37a8b-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
