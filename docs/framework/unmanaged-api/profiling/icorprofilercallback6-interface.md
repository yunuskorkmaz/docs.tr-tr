---
title: ICorProfilerCallback6 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fda98c20b42355b9f52595929bbf5b980b5b857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077244"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="a7a00-102">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7a00-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="a7a00-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="a7a00-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a7a00-104">Öğesinin [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) bir derleme yüklenen bir profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7a00-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7a00-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7a00-105">Methods</span></span>  
  
|<span data-ttu-id="a7a00-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7a00-106">Method</span></span>|<span data-ttu-id="a7a00-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a00-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7a00-108">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7a00-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="a7a00-109">Profil Oluşturucu, ortak dil çalışma zamanı bir bütünleştirilmiş kod başvurusu kapanış Yürüme gerçekleştirirken bir derleme bir çok erken aşama, yükleniyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a7a00-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7a00-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7a00-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a00-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7a00-111">Requirements</span></span>  
 <span data-ttu-id="a7a00-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a00-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a00-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a7a00-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7a00-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a00-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a00-115">See also</span></span>

- [<span data-ttu-id="a7a00-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7a00-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
