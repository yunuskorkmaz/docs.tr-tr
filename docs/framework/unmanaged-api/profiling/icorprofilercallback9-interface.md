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
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136572"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="c2d14-102">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2d14-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="c2d14-103">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c2d14-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="c2d14-104">Ortak dil çalışma zamanı tarafından, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılabileceğini bildirmek için kullanılan bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback8](icorprofilercallback8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2d14-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2d14-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c2d14-105">Methods</span></span>  
  
|<span data-ttu-id="c2d14-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c2d14-106">Method</span></span>|<span data-ttu-id="c2d14-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2d14-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2d14-108">DynamicMethodUnloaded Metodu</span><span class="sxs-lookup"><span data-stu-id="c2d14-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="c2d14-109">Profiler öğesine dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2d14-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2d14-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2d14-110">Requirements</span></span>  
 <span data-ttu-id="c2d14-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d14-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d14-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2d14-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="c2d14-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d14-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c2d14-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d14-114">See also</span></span>

- [<span data-ttu-id="c2d14-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2d14-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c2d14-116">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2d14-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="c2d14-117">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2d14-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="c2d14-118">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2d14-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
