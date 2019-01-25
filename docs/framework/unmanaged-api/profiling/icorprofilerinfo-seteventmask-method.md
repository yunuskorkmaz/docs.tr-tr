---
title: ICorProfilerInfo::SetEventMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34aba20704ff8dc0d699ebee9440745d19c697b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566014"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="34dcc-102">ICorProfilerInfo::SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34dcc-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="34dcc-103">Profil Oluşturucu ortak dil çalışma zamanından (CLR) bildirim almak istediği olaylara türlerini belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34dcc-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34dcc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34dcc-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34dcc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34dcc-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="34dcc-106">[in] Olayların kategorilerini belirten bir 4 baytlık değeri.</span><span class="sxs-lookup"><span data-stu-id="34dcc-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="34dcc-107">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="34dcc-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="34dcc-108">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="34dcc-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34dcc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34dcc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34dcc-110">Çağırmalısınız [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi bu yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="34dcc-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="34dcc-111">Ancak `SetEventMask` yöntemi devam desteklenmesi [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="34dcc-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34dcc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34dcc-112">Requirements</span></span>  
 <span data-ttu-id="34dcc-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34dcc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34dcc-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34dcc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34dcc-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34dcc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34dcc-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34dcc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34dcc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34dcc-117">See also</span></span>
- [<span data-ttu-id="34dcc-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34dcc-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="34dcc-119">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34dcc-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
