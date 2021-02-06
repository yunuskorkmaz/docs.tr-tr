---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo5:: GetEventMask2 yöntemi'
title: ICorProfilerInfo5::GetEventMask2 Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: c6652ffe1b8fd0d99ce5493c8ba27a971363c423
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646666"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="97370-103">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="97370-103">ICorProfilerInfo5::GetEventMask2 Method</span></span>

<span data-ttu-id="97370-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="97370-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="97370-105">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="97370-105">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="97370-106">[ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) yöntemi tarafından sağlanmayan işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="97370-106">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97370-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97370-107">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97370-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97370-108">Parameters</span></span>  

 `pdwEventsLow`  
 <span data-ttu-id="97370-109">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97370-109">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="97370-110">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="97370-110">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="97370-111">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97370-111">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="97370-112">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97370-112">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="97370-113">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="97370-113">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="97370-114">Bitleri [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97370-114">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97370-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97370-115">Remarks</span></span>  

 <span data-ttu-id="97370-116">`GetEventMask2`Yöntemi, profil oluşturucunun abone olduğu geri çağırmaları tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97370-116">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="97370-117">Genellikle, bir mantıksal veya değerlerini ve ayarlamak istediğiniz `pdwEventsLow` `pdwEventsHigh` Yeni bitleri gerçekleştirirsiniz ve ardından [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97370-117">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="97370-118">Bu yöntem, [GetEventMask](icorprofilerinfo-geteventmask-method.md) yönteminin önerilen alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="97370-118">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97370-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97370-119">Requirements</span></span>  

 <span data-ttu-id="97370-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97370-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97370-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="97370-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97370-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97370-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97370-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97370-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97370-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97370-124">See also</span></span>

- [<span data-ttu-id="97370-125">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97370-125">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="97370-126">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97370-126">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
