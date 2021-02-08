---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo5:: SetEventMask2 Yöntemi'
title: ICorProfilerInfo5::SetEventMask2 Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 2928ec408f2fdeb363164530258a3bf5c9719e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799011"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="b07d3-103">ICorProfilerInfo5::SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b07d3-103">ICorProfilerInfo5::SetEventMask2 Method</span></span>

<span data-ttu-id="b07d3-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="b07d3-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b07d3-105">Profil oluşturucunun, ortak dil çalışma zamanından (CLR) olay bildirimleri almak istediği olay türlerini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b07d3-105">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="b07d3-106">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yönteminden daha fazla işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b07d3-106">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07d3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b07d3-107">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b07d3-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b07d3-108">Parameters</span></span>  

 `dwEventsLow`  
 <span data-ttu-id="b07d3-109">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="b07d3-109">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="b07d3-110">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="b07d3-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b07d3-111">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b07d3-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="b07d3-112">'ndaki Olayların kategorilerini belirten 4 baytlık bir değer.</span><span class="sxs-lookup"><span data-stu-id="b07d3-112">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="b07d3-113">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="b07d3-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b07d3-114">Bitleri [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b07d3-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b07d3-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b07d3-115">Remarks</span></span>  

 <span data-ttu-id="b07d3-116">`SetEventMask2`Yöntemi, profil oluşturucunun abone olduğu geri çağırmaları ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b07d3-116">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="b07d3-117">Genellikle, hangi bitlerin ayarlandığını öğrenmek için [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) yöntemini çağırır, mantıksal veya `pdwEventsLow` değerlerini ve `pdwEventsHigh` ayarlamak istediğiniz yeni bitleri gerçekleştirin ve sonra `SetEventMask2` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b07d3-117">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="b07d3-118">Bu yöntem, [SetEventMask](icorprofilerinfo-seteventmask-method.md) yönteminin önerilen alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="b07d3-118">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b07d3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b07d3-119">Requirements</span></span>  

 <span data-ttu-id="b07d3-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b07d3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b07d3-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b07d3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b07d3-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b07d3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b07d3-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b07d3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07d3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b07d3-124">See also</span></span>

- [<span data-ttu-id="b07d3-125">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b07d3-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="b07d3-126">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b07d3-126">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
