---
title: ICorProfilerInfo5 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo5
api_location: mscorwks.dll
api_type: COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75bbaf5fdf41a55719965203c50ddd0f5d48263a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="ecbcd-102">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecbcd-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="ecbcd-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="ecbcd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ecbcd-104">Öğesinin bir alt [Icorprofilerınfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) ortak dil çalışma olayı izleme denetlemek için (CLR) ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecbcd-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecbcd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ecbcd-105">Methods</span></span>  
  
|<span data-ttu-id="ecbcd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ecbcd-106">Method</span></span>|<span data-ttu-id="ecbcd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecbcd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecbcd-108">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecbcd-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="ecbcd-109">Profil Oluşturucu CLR bildirimlerini almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="ecbcd-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="ecbcd-110">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecbcd-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="ecbcd-111">Profil Oluşturucu CLR olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ecbcd-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecbcd-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecbcd-112">Remarks</span></span>  
 <span data-ttu-id="ecbcd-113">Bu arabirimde yöntemleri değiştirmek için tasarlanmıştır [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) ve [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ecbcd-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbcd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecbcd-114">Requirements</span></span>  
 <span data-ttu-id="ecbcd-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecbcd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecbcd-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ecbcd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ecbcd-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecbcd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbcd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecbcd-118">See Also</span></span>  
 [<span data-ttu-id="ecbcd-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ecbcd-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
