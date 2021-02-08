---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback7 Interface'
title: ICorProfilerCallback7 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: 3db402db221fca4487939f9817b20ec0c5207fc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781746"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="c0664-103">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0664-103">ICorProfilerCallback7 Interface</span></span>

<span data-ttu-id="c0664-104">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c0664-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c0664-105">Ortak dil çalışma zamanının, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiği profil oluşturucuyu bilgilendirmek için kullandığı bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback6](icorprofilercallback6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c0664-105">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0664-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c0664-106">Methods</span></span>  
  
|<span data-ttu-id="c0664-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c0664-107">Method</span></span>|<span data-ttu-id="c0664-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0664-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0664-109">ModuleInMemorySymbolsUpdated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0664-109">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="c0664-110">Profil oluşturucuyu, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c0664-110">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0664-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0664-111">Requirements</span></span>  

 <span data-ttu-id="c0664-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0664-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0664-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0664-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0664-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0664-114">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0664-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0664-115">See also</span></span>

- [<span data-ttu-id="c0664-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c0664-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
