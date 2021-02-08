---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback9 Interface'
title: ICorProfilerCallback9 Arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4bfcaf6f8985909ef9142ef4d08535a19facd7e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781655"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="87ed0-103">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ed0-103">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="87ed0-104">[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="87ed0-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="87ed0-105">Ortak dil çalışma zamanı tarafından, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılabileceğini bildirmek için kullanılan bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback8](icorprofilercallback8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87ed0-105">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87ed0-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="87ed0-106">Methods</span></span>  
  
|<span data-ttu-id="87ed0-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="87ed0-107">Method</span></span>|<span data-ttu-id="87ed0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87ed0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87ed0-109">DynamicMethodUnloaded Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ed0-109">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="87ed0-110">Profiler öğesine dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="87ed0-110">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87ed0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87ed0-111">Requirements</span></span>  

 <span data-ttu-id="87ed0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ed0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ed0-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87ed0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="87ed0-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87ed0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="87ed0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ed0-115">See also</span></span>

- [<span data-ttu-id="87ed0-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87ed0-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="87ed0-117">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ed0-117">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="87ed0-118">ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ed0-118">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="87ed0-119">ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ed0-119">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
