---
title: "ICorProfilerInfo::SetEventMask Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c6fe763103e7b8aaf6d501c653342a21bd513b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="337c0-102">ICorProfilerInfo::SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="337c0-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="337c0-103">Profil Oluşturucu ortak dil çalışma (CLR) bildirim almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="337c0-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="337c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="337c0-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="337c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="337c0-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="337c0-106">[in] Olayların kategorilerini belirler 4-bayt değeri.</span><span class="sxs-lookup"><span data-stu-id="337c0-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="337c0-107">Her bitin farklı yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="337c0-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="337c0-108">BITS açıklanan [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="337c0-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="337c0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="337c0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="337c0-110">Çağırmalısınız [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metodu yerine bu yöntem.</span><span class="sxs-lookup"><span data-stu-id="337c0-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="337c0-111">Ancak `SetEventMask` yöntemi sürdürür desteklenmesi, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="337c0-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="337c0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="337c0-112">Requirements</span></span>  
 <span data-ttu-id="337c0-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="337c0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="337c0-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="337c0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="337c0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="337c0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="337c0-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="337c0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337c0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="337c0-117">See Also</span></span>  
 [<span data-ttu-id="337c0-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="337c0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="337c0-119">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="337c0-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
