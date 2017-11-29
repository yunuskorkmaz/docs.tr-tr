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
ms.openlocfilehash: dca83aca3aee4a072e90793e1bb33526b6e5ebd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="fb335-102">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb335-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="fb335-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="fb335-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fb335-104">Öğesinin bir alt [Icorprofilercallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) bir derlemesi yüklenirken bir profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb335-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb335-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb335-105">Methods</span></span>  
  
|<span data-ttu-id="fb335-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fb335-106">Method</span></span>|<span data-ttu-id="fb335-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb335-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb335-108">GetAssemblyReferences yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb335-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="fb335-109">Profil Oluşturucu ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bütünleştirilmiş bir çok erkenden aşama, yüklüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb335-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb335-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb335-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb335-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb335-111">Requirements</span></span>  
 <span data-ttu-id="fb335-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb335-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb335-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb335-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb335-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb335-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb335-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb335-115">See Also</span></span>  
 [<span data-ttu-id="fb335-116">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb335-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
