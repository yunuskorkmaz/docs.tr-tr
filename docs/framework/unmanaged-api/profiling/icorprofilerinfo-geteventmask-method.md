---
description: ': ICorProfilerInfo:: GetEventMask yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8ae02a0ef98330207fa7ce6366342d5e0bcb4f19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647654"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="08b4e-103">ICorProfilerInfo::GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08b4e-103">ICorProfilerInfo::GetEventMask Method</span></span>

<span data-ttu-id="08b4e-104">Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="08b4e-104">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b4e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08b4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08b4e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08b4e-106">Parameters</span></span>  

 `pdwEvents`  
 <span data-ttu-id="08b4e-107">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08b4e-107">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="08b4e-108">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="08b4e-108">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="08b4e-109">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08b4e-109">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b4e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08b4e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08b4e-111">Bu yöntem yerine [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08b4e-111">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="08b4e-112">`SetEventMask`Yöntemi desteklenmeye devam etse de, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ek işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="08b4e-112">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b4e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08b4e-113">Requirements</span></span>  

 <span data-ttu-id="08b4e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08b4e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b4e-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="08b4e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08b4e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08b4e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08b4e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b4e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b4e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08b4e-118">See also</span></span>

- [<span data-ttu-id="08b4e-119">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08b4e-119">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="08b4e-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08b4e-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
