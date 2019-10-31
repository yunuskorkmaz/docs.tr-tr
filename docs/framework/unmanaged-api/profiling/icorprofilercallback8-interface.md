---
title: ICorProfilerCallback8 Arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136448"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="7f014-102">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f014-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="7f014-103">[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="7f014-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="7f014-104">Ortak dil çalışma zamanı tarafından, bir dinamik yöntemin JıT derlemesinin başlatıldığını ve tamamlandığını bildiren profil oluşturucu bildirmek için kullanılan geri çağırma yöntemleri sağlayan bir [ICorProfilerCallback7](icorprofilercallback7-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f014-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="7f014-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7f014-105">Methods</span></span>  
  
|<span data-ttu-id="7f014-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7f014-106">Method</span></span>|<span data-ttu-id="7f014-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f014-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f014-108">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="7f014-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="7f014-109">Profiler öğesine dinamik bir yöntemin JıT derlemesinin başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7f014-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="7f014-110">DynamicMethodJITCompilationFinished Metodu</span><span class="sxs-lookup"><span data-stu-id="7f014-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="7f014-111">Profiler öğesine dinamik bir yöntemin JıT derlemesinin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7f014-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f014-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f014-112">Requirements</span></span>  
 <span data-ttu-id="7f014-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f014-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f014-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7f014-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="7f014-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7f014-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7f014-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f014-116">See also</span></span>

- [<span data-ttu-id="7f014-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7f014-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7f014-118">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f014-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
