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
ms.openlocfilehash: e11628f9c20160899f37e62472547eaa98ea60b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962646"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="a3a29-102">ICorProfilerInfo::SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3a29-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="a3a29-103">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a3a29-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3a29-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3a29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3a29-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="a3a29-106">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="a3a29-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a3a29-107">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="a3a29-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a3a29-108">Bitleri [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3a29-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3a29-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3a29-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3a29-110">Bu yöntem yerine [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3a29-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="a3a29-111">Yöntemi desteklenmeye devam etse de, SetEventMask2 ek işlevsellik sağlar. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) `SetEventMask`</span><span class="sxs-lookup"><span data-stu-id="a3a29-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a29-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3a29-112">Requirements</span></span>  
 <span data-ttu-id="a3a29-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a29-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a29-114">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3a29-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3a29-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3a29-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3a29-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a29-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a29-117">See also</span></span>

- [<span data-ttu-id="a3a29-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3a29-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a3a29-119">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3a29-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
