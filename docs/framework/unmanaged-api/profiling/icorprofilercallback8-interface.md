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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175102"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="772e5-102">ICorProfilerCallback8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="772e5-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="772e5-103">[.NET Framework 4.7 ve sonraki sürümlerde desteklendi]</span><span class="sxs-lookup"><span data-stu-id="772e5-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="772e5-104">Profilciye dinamik bir yöntemin JIT derlemesinin başladığını ve bittiğini bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri arama yöntemlerini sağlayan [ICorProfilerCallback7'nin](icorprofilercallback7-interface.md) bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="772e5-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="772e5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="772e5-105">Methods</span></span>  
  
|<span data-ttu-id="772e5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="772e5-106">Method</span></span>|<span data-ttu-id="772e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="772e5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="772e5-108">DynamicMethodJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772e5-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="772e5-109">Profiloluşturucuya dinamik bir yöntemin JIT derlemesinin başladığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="772e5-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="772e5-110">DynamicMethodJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="772e5-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="772e5-111">Profiloluşturucuya dinamik bir yöntemin JIT derlemesinin tamamladığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="772e5-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="772e5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="772e5-112">Requirements</span></span>  
 <span data-ttu-id="772e5-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772e5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772e5-114">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="772e5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="772e5-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="772e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="772e5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="772e5-116">See also</span></span>

- [<span data-ttu-id="772e5-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="772e5-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="772e5-118">ICorProfilerCallback9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="772e5-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
