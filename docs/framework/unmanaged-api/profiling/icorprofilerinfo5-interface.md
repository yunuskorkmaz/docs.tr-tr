---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo5 Interface'
title: ICorProfilerInfo5 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: c89faf3db08adeee3ffcfbb755a5da5ae44b3c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737278"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="fcb55-103">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcb55-103">ICorProfilerInfo5 Interface</span></span>

<span data-ttu-id="fcb55-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="fcb55-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fcb55-105">Kod profil oluşturucular tarafından, olay izlemeyi denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak için kullanılacak yöntemler sağlayan bir [ICorProfilerInfo4](icorprofilerinfo4-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fcb55-105">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcb55-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fcb55-106">Methods</span></span>  
  
|<span data-ttu-id="fcb55-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fcb55-107">Method</span></span>|<span data-ttu-id="fcb55-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcb55-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcb55-109">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcb55-109">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="fcb55-110">Profil oluşturucunun CLR 'den bildirim almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="fcb55-110">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="fcb55-111">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcb55-111">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="fcb55-112">Profil oluşturucunun, CLR 'den olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fcb55-112">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcb55-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcb55-113">Remarks</span></span>  

 <span data-ttu-id="fcb55-114">Bu arabirimdeki kullanılabilir yöntemler [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemlerinin yerini alacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fcb55-114">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb55-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcb55-115">Requirements</span></span>  

 <span data-ttu-id="fcb55-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb55-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcb55-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fcb55-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcb55-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb55-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcb55-119">See also</span></span>

- [<span data-ttu-id="fcb55-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fcb55-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
