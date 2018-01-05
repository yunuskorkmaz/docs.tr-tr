---
title: ICorProfilerCallback6 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 733ca2f03e73852f2fef1e42fb9ec961ade2975d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="95811-102">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95811-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="95811-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="95811-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="95811-104">Öğesinin bir alt [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) bir derlemesi yüklenirken bir profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95811-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95811-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95811-105">Methods</span></span>  
  
|<span data-ttu-id="95811-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95811-106">Method</span></span>|<span data-ttu-id="95811-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95811-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95811-108">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95811-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="95811-109">Profil Oluşturucu ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bütünleştirilmiş bir çok erkenden aşama, yüklüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="95811-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95811-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95811-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95811-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95811-111">Requirements</span></span>  
 <span data-ttu-id="95811-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95811-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95811-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95811-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95811-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95811-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95811-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95811-115">See Also</span></span>  
 [<span data-ttu-id="95811-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95811-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
