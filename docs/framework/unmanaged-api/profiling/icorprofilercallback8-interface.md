---
title: ICorProfilerCallback8 arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455289"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="bd79d-102">ICorProfilerCallback8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd79d-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="bd79d-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="bd79d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="bd79d-104">Öğesinin bir alt [ICorProfilerCallback7](icorprofilercallback7-interface.md) JIT derleme dinamik yönteminin başlatıldı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd79d-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="bd79d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bd79d-105">Methods</span></span>  
  
|<span data-ttu-id="bd79d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bd79d-106">Method</span></span>|<span data-ttu-id="bd79d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd79d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd79d-108">DynamicMethodJITCompilationStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd79d-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="bd79d-109">Profil Oluşturucu JIT derleme dinamik yönteminin başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd79d-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="bd79d-110">DynamicMethodJITCompilationFinished yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd79d-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="bd79d-111">Profil Oluşturucu JIT derleme dinamik yönteminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd79d-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd79d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd79d-112">Requirements</span></span>  
 <span data-ttu-id="bd79d-113">**Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd79d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd79d-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd79d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="bd79d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bd79d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bd79d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd79d-116">See Also</span></span>  
<span data-ttu-id="bd79d-117">[Profil oluşturma arabirimleri](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="bd79d-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="bd79d-118">ICorProfilerCallback9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd79d-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
