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
ms.openlocfilehash: f8c2fb544cf9fd6642bd0581211e0e4e49633221
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139764"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="ceeb6-102">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ceeb6-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="ceeb6-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="ceeb6-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ceeb6-104">Ortak dil çalışma zamanının, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiği profil oluşturucuyu bilgilendirmek için kullandığı bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ceeb6-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ceeb6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ceeb6-105">Methods</span></span>  
  
|<span data-ttu-id="ceeb6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ceeb6-106">Method</span></span>|<span data-ttu-id="ceeb6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ceeb6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ceeb6-108">ModuleInMemorySymbolsUpdated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ceeb6-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="ceeb6-109">Profil oluşturucuyu, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ceeb6-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceeb6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ceeb6-110">Requirements</span></span>  
 <span data-ttu-id="ceeb6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceeb6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceeb6-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ceeb6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ceeb6-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceeb6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceeb6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceeb6-114">See also</span></span>

- [<span data-ttu-id="ceeb6-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ceeb6-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
