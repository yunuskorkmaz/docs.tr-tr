---
title: Icorprofilercallback8 arabirimi
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
ms.openlocfilehash: a3bdf79582619777a22c80caac5b4e90d603f3a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675021"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="7fd86-102">Icorprofilercallback8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7fd86-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="7fd86-103">[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="7fd86-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="7fd86-104">Öğesinin [Icorprofilercallback7](icorprofilercallback7-interface.md) dinamik bir yöntem JIT derlemesi başladı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri çağırma yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fd86-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="7fd86-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7fd86-105">Methods</span></span>  
  
|<span data-ttu-id="7fd86-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7fd86-106">Method</span></span>|<span data-ttu-id="7fd86-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fd86-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fd86-108">DynamicMethodJITCompilationStarted Metodu</span><span class="sxs-lookup"><span data-stu-id="7fd86-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="7fd86-109">Profil Oluşturucu, dinamik bir yöntem JIT derlemesi başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7fd86-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="7fd86-110">DynamicMethodJITCompilationFinished Metodu</span><span class="sxs-lookup"><span data-stu-id="7fd86-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="7fd86-111">Profil oluşturucunun JIT derlemesi dinamik yöntemi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="7fd86-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fd86-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7fd86-112">Requirements</span></span>  
 <span data-ttu-id="7fd86-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd86-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd86-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7fd86-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="7fd86-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd86-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7fd86-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fd86-116">See also</span></span>
- [<span data-ttu-id="7fd86-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7fd86-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7fd86-118">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7fd86-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
