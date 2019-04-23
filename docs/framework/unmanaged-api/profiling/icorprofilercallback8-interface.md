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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125573"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="7c11d-102">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c11d-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="7c11d-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="7c11d-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="7c11d-104">Öğesinin [Icorprofilercallback7](icorprofilercallback7-interface.md) dinamik bir yöntem JIT derlemesi başladı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c11d-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="7c11d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7c11d-105">Methods</span></span>  
  
|<span data-ttu-id="7c11d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7c11d-106">Method</span></span>|<span data-ttu-id="7c11d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c11d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c11d-108">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="7c11d-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="7c11d-109">Profil Oluşturucu, dinamik bir yöntem JIT derlemesi başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7c11d-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="7c11d-110">DynamicMethodJITCompilationFinished Metodu</span><span class="sxs-lookup"><span data-stu-id="7c11d-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="7c11d-111">Profil oluşturucunun JIT derlemesi dinamik yöntemi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7c11d-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c11d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c11d-112">Requirements</span></span>  
 <span data-ttu-id="7c11d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c11d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c11d-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c11d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="7c11d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c11d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7c11d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c11d-116">See also</span></span>

- [<span data-ttu-id="7c11d-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c11d-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7c11d-118">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c11d-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
