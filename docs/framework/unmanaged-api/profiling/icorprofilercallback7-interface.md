---
title: ICorProfilerCallback7 arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f681001b610f42fef28181ffe3b47d702aabdf6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452699"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="08825-102">ICorProfilerCallback7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="08825-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="08825-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="08825-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="08825-104">Öğesinin bir alt [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) bir bellek içi modülü ile ilişkili simgesi akış güncelleştirilir profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08825-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08825-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08825-105">Methods</span></span>  
  
|<span data-ttu-id="08825-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08825-106">Method</span></span>|<span data-ttu-id="08825-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08825-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08825-108">ModuleInMemorySymbolsUpdated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08825-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="08825-109">Profil Oluşturucu bir bellek içi modülü ile ilişkili simgesi akış güncelleştirilir bildirir.</span><span class="sxs-lookup"><span data-stu-id="08825-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08825-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08825-110">Requirements</span></span>  
 <span data-ttu-id="08825-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08825-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08825-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08825-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08825-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08825-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08825-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08825-114">See Also</span></span>  
 [<span data-ttu-id="08825-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08825-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
