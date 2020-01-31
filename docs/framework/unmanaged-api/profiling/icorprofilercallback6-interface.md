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
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864875"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="edcef-102">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edcef-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="edcef-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="edcef-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="edcef-104">Ortak dil çalışma zamanının bir derlemenin yüklendiği profil oluşturucuyu bilgilendirmek için kullandığı bir geri çağırma yöntemi sağlayan [ICorProfilerCallback5](icorprofilercallback5-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edcef-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="edcef-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="edcef-105">Methods</span></span>  
  
|<span data-ttu-id="edcef-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="edcef-106">Method</span></span>|<span data-ttu-id="edcef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edcef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="edcef-108">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="edcef-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="edcef-109">Profil oluşturucuyu bir derlemenin çok erken yükleme aşamasında olduğunu, ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="edcef-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edcef-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edcef-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edcef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edcef-111">Requirements</span></span>  
 <span data-ttu-id="edcef-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edcef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edcef-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="edcef-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edcef-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edcef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edcef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edcef-115">See also</span></span>

- [<span data-ttu-id="edcef-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="edcef-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
