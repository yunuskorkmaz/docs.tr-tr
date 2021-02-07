---
description: ': ICorProfilerInfo:: SetEventMask yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e389d25abfecfc9a5dec8834e412fe618324e311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687200"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="3fc19-103">ICorProfilerInfo::SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fc19-103">ICorProfilerInfo::SetEventMask Method</span></span>

<span data-ttu-id="3fc19-104">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3fc19-104">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc19-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fc19-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc19-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fc19-106">Parameters</span></span>  

 `dwEvents`  
 <span data-ttu-id="3fc19-107">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="3fc19-107">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="3fc19-108">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="3fc19-108">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="3fc19-109">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fc19-109">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc19-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fc19-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fc19-111">Bu yöntem yerine [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc19-111">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="3fc19-112">`SetEventMask`Yöntemi desteklenmeye devam etse de, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fc19-112">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc19-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fc19-113">Requirements</span></span>  

 <span data-ttu-id="3fc19-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc19-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc19-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3fc19-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fc19-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3fc19-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc19-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc19-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc19-118">See also</span></span>

- [<span data-ttu-id="3fc19-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fc19-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3fc19-120">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fc19-120">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
