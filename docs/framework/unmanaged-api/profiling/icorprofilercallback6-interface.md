---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback6 Interface'
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
ms.openlocfilehash: 12eaafff8bd9ab8d4d58eac8f2d62415531bc898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781759"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="48c12-103">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48c12-103">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="48c12-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="48c12-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="48c12-105">Ortak dil çalışma zamanının bir derlemenin yüklendiği profil oluşturucuyu bilgilendirmek için kullandığı bir geri çağırma yöntemi sağlayan [ICorProfilerCallback5](icorprofilercallback5-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48c12-105">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48c12-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="48c12-106">Methods</span></span>  
  
|<span data-ttu-id="48c12-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="48c12-107">Method</span></span>|<span data-ttu-id="48c12-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48c12-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48c12-109">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48c12-109">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="48c12-110">Profil oluşturucuyu bir derlemenin çok erken yükleme aşamasında olduğunu, ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="48c12-110">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48c12-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48c12-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48c12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48c12-112">Requirements</span></span>  

 <span data-ttu-id="48c12-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48c12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48c12-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48c12-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48c12-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48c12-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c12-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48c12-116">See also</span></span>

- [<span data-ttu-id="48c12-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48c12-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
