---
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
ms.openlocfilehash: f3943eef969f777b40dc51c4900b190561f14887
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868401"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="ba467-102">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="ba467-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="ba467-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="ba467-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ba467-104">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ba467-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="ba467-105">[ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) yöntemi tarafından sağlanmayan işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba467-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba467-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba467-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba467-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba467-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="ba467-108">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba467-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="ba467-109">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="ba467-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ba467-110">Bitleri [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba467-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="ba467-111">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba467-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="ba467-112">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="ba467-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ba467-113">Bitleri [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) numaralandırmasında açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba467-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba467-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba467-114">Remarks</span></span>  
 <span data-ttu-id="ba467-115">`GetEventMask2` yöntemi, profil oluşturucunun abone olduğu geri çağırmaları tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba467-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="ba467-116">Genellikle, `pdwEventsLow` ve `pdwEventsHigh` değerlerini ve ayarlamak istediğiniz tüm yeni bitleri gerçekleştirin ve ardından [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ba467-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="ba467-117">Bu yöntem, [GetEventMask](icorprofilerinfo-geteventmask-method.md) yönteminin önerilen alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="ba467-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba467-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba467-118">Requirements</span></span>  
 <span data-ttu-id="ba467-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba467-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba467-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ba467-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba467-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba467-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba467-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba467-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba467-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba467-123">See also</span></span>

- [<span data-ttu-id="ba467-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba467-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="ba467-125">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba467-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
