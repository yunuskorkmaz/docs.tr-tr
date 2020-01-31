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
ms.openlocfilehash: ed39411fa88c38da58e8a881c47d19b3b8c9ff8d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869285"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="eca4b-102">ICorProfilerInfo::SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eca4b-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="eca4b-103">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eca4b-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eca4b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eca4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eca4b-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="eca4b-106">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="eca4b-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="eca4b-107">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="eca4b-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="eca4b-108">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eca4b-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca4b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eca4b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eca4b-110">Bu yöntem yerine [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eca4b-110">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="eca4b-111">`SetEventMask` yöntemi desteklenmeye devam etse de, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="eca4b-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca4b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eca4b-112">Requirements</span></span>  
 <span data-ttu-id="eca4b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca4b-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eca4b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eca4b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eca4b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca4b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca4b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca4b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eca4b-117">See also</span></span>

- [<span data-ttu-id="eca4b-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eca4b-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="eca4b-119">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eca4b-119">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
