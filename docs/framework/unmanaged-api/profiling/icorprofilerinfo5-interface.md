---
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
ms.openlocfilehash: a6206e35280e073df2abfb7ae46aa84d34b30208
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733808"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="6ceec-102">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ceec-102">ICorProfilerInfo5 Interface</span></span>

<span data-ttu-id="6ceec-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6ceec-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6ceec-104">Kod profil oluşturucular tarafından, olay izlemeyi denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak için kullanılacak yöntemler sağlayan bir [ICorProfilerInfo4](icorprofilerinfo4-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6ceec-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ceec-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ceec-105">Methods</span></span>  
  
|<span data-ttu-id="6ceec-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6ceec-106">Method</span></span>|<span data-ttu-id="6ceec-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ceec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ceec-108">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ceec-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="6ceec-109">Profil oluşturucunun CLR 'den bildirim almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6ceec-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="6ceec-110">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ceec-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="6ceec-111">Profil oluşturucunun, CLR 'den olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ceec-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ceec-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ceec-112">Remarks</span></span>  

 <span data-ttu-id="6ceec-113">Bu arabirimdeki kullanılabilir yöntemler [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemlerinin yerini alacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ceec-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ceec-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ceec-114">Requirements</span></span>  

 <span data-ttu-id="6ceec-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ceec-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ceec-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6ceec-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ceec-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ceec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceec-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ceec-118">See also</span></span>

- [<span data-ttu-id="6ceec-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ceec-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
