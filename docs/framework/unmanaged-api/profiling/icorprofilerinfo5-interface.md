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
ms.openlocfilehash: 84744474b9eca96cae5e96b8c4eadc4109f85f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="c781c-102">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c781c-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="c781c-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c781c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c781c-104">Öğesinin bir alt [Icorprofilerınfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) ortak dil çalışma olayı izleme denetlemek için (CLR) ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c781c-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c781c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c781c-105">Methods</span></span>  
  
|<span data-ttu-id="c781c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c781c-106">Method</span></span>|<span data-ttu-id="c781c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c781c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c781c-108">GetEventMask2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="c781c-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="c781c-109">Profil Oluşturucu CLR bildirimlerini almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="c781c-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="c781c-110">SetEventMask2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="c781c-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="c781c-111">Profil Oluşturucu CLR olay bildirimlerini almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c781c-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c781c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c781c-112">Remarks</span></span>  
 <span data-ttu-id="c781c-113">Bu arabirimde yöntemleri değiştirmek için tasarlanmıştır [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) ve [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c781c-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c781c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c781c-114">Requirements</span></span>  
 <span data-ttu-id="c781c-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c781c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c781c-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c781c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c781c-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c781c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c781c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c781c-118">See Also</span></span>  
 [<span data-ttu-id="c781c-119">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c781c-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
