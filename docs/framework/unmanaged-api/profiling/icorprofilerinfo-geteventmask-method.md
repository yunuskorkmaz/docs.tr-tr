---
title: ICorProfilerInfo::GetEventMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2881dbe83b0d9f6e2ae3c4f478bbecdca444b78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991880"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="20e03-102">ICorProfilerInfo::GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20e03-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="20e03-103">Profil Oluşturucu ortak dil çalışma zamanından (CLR) olay bildirimlerini almak istediği geçerli olay kategorileri alır.</span><span class="sxs-lookup"><span data-stu-id="20e03-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20e03-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20e03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20e03-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="20e03-106">[out] Olayların kategorilerini belirten bir 4 baytlık değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20e03-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="20e03-107">Farklı yetenek, davranış veya olay türü her bit denetler.</span><span class="sxs-lookup"><span data-stu-id="20e03-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="20e03-108">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="20e03-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20e03-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20e03-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20e03-110">Çağırmalısınız [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) yöntemi bu yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="20e03-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="20e03-111">Ancak `SetEventMask` yöntemi devam desteklenmesi [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="20e03-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e03-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20e03-112">Requirements</span></span>  
 <span data-ttu-id="20e03-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e03-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e03-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20e03-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20e03-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20e03-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20e03-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e03-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e03-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20e03-117">See also</span></span>

- [<span data-ttu-id="20e03-118">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20e03-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="20e03-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20e03-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
