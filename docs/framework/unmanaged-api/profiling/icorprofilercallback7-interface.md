---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81477010b22edee71098edfc1b8557db08b6038f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049706"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="440ed-102">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="440ed-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="440ed-103">[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="440ed-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="440ed-104">Öğesinin [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) profil oluşturucu bir bellek içi modül ile ilişkili simge akışı güncelleştirilmiş olduğunu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="440ed-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="440ed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="440ed-105">Methods</span></span>  
  
|<span data-ttu-id="440ed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="440ed-106">Method</span></span>|<span data-ttu-id="440ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="440ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="440ed-108">ModuleInMemorySymbolsUpdated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="440ed-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="440ed-109">Profil Oluşturucu, bir bellek içi modül ile ilişkili simge akışı güncelleştirilmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="440ed-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="440ed-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="440ed-110">Requirements</span></span>  
 <span data-ttu-id="440ed-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="440ed-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="440ed-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="440ed-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="440ed-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="440ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="440ed-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="440ed-114">See also</span></span>

- [<span data-ttu-id="440ed-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="440ed-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
