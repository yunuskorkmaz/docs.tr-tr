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
ms.openlocfilehash: e61f6a104b8b9613db32ed6912395fd07c18dcff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864823"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="82fa2-102">ICorProfilerCallback7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82fa2-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="82fa2-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="82fa2-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="82fa2-104">Ortak dil çalışma zamanının, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiği profil oluşturucuyu bilgilendirmek için kullandığı bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback6](icorprofilercallback6-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="82fa2-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82fa2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="82fa2-105">Methods</span></span>  
  
|<span data-ttu-id="82fa2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="82fa2-106">Method</span></span>|<span data-ttu-id="82fa2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82fa2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82fa2-108">ModuleInMemorySymbolsUpdated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82fa2-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="82fa2-109">Profil oluşturucuyu, bellek içi modülle ilişkilendirilen sembol akışının güncelleştirildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="82fa2-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82fa2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82fa2-110">Requirements</span></span>  
 <span data-ttu-id="82fa2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82fa2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82fa2-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="82fa2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82fa2-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82fa2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82fa2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82fa2-114">See also</span></span>

- [<span data-ttu-id="82fa2-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82fa2-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
