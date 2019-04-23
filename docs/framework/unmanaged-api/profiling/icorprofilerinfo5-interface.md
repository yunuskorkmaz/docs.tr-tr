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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094261"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="cc42a-102">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc42a-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="cc42a-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="cc42a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cc42a-104">Öğesinin [Icorprofilerınfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) olayı izlemeyi denetlemek için (CLR) ortak dil çalışma zamanıyla iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc42a-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc42a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cc42a-105">Methods</span></span>  
  
|<span data-ttu-id="cc42a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cc42a-106">Method</span></span>|<span data-ttu-id="cc42a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc42a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc42a-108">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc42a-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="cc42a-109">Profil Oluşturucu CLR'den bildirim almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="cc42a-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="cc42a-110">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc42a-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="cc42a-111">Profil Oluşturucu CLR'den olay bildirimlerini almak istediği olaylara türlerini belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc42a-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc42a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc42a-112">Remarks</span></span>  
 <span data-ttu-id="cc42a-113">Bu arabirimdeki yöntemleri değiştirmek için hedeflenen [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) ve [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="cc42a-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc42a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc42a-114">Requirements</span></span>  
 <span data-ttu-id="cc42a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc42a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc42a-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc42a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc42a-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc42a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc42a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc42a-118">See also</span></span>

- [<span data-ttu-id="cc42a-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc42a-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
