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
ms.openlocfilehash: 16bd8b09d5118171e669e9c428fb444384b5867d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722576"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="d4f83-102">ICorProfilerInfo::GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4f83-102">ICorProfilerInfo::GetEventMask Method</span></span>

<span data-ttu-id="d4f83-103">Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d4f83-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f83-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d4f83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4f83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4f83-105">Parameters</span></span>  

 `pdwEvents`  
 <span data-ttu-id="d4f83-106">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4f83-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="d4f83-107">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="d4f83-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="d4f83-108">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4f83-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f83-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4f83-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4f83-110">Bu yöntem yerine [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4f83-110">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="d4f83-111">`SetEventMask`Yöntemi desteklenmeye devam etse de, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4f83-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f83-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4f83-112">Requirements</span></span>  

 <span data-ttu-id="d4f83-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4f83-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f83-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d4f83-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4f83-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d4f83-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4f83-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f83-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f83-117">See also</span></span>

- [<span data-ttu-id="d4f83-118">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4f83-118">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="d4f83-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4f83-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
