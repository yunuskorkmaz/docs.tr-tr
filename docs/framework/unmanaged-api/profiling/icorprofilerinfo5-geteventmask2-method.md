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
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114742"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="56300-102">ICorProfilerInfo5::GetEventMask2 Metodu</span><span class="sxs-lookup"><span data-stu-id="56300-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="56300-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="56300-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="56300-104">Profil oluşturucunun ortak dil çalışma zamanından (CLR) bildirim almak istediği geçerli olay kategorilerini alır.</span><span class="sxs-lookup"><span data-stu-id="56300-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="56300-105">[ICorProfilerInfo:: GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yöntemi tarafından sağlanmayan işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="56300-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56300-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56300-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56300-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56300-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="56300-108">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56300-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="56300-109">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="56300-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="56300-110">Bitleri [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56300-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="56300-111">dışı Olayların kategorilerini belirten 4 baytlık bir değere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56300-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="56300-112">Her bit, farklı bir yetenek, davranış veya olay türünü denetler.</span><span class="sxs-lookup"><span data-stu-id="56300-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="56300-113">Bitleri [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) numaralandırması içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56300-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56300-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56300-114">Remarks</span></span>  
 <span data-ttu-id="56300-115">`GetEventMask2` yöntemi, profil oluşturucunun abone olduğu geri çağırmaları tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56300-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="56300-116">Genellikle, `pdwEventsLow` ve `pdwEventsHigh` değerlerini ve ayarlamak istediğiniz tüm yeni bitleri gerçekleştirin ve ardından [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="56300-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="56300-117">Bu yöntem, [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) yönteminin önerilen alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="56300-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56300-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56300-118">Requirements</span></span>  
 <span data-ttu-id="56300-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56300-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56300-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="56300-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56300-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="56300-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56300-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56300-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56300-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56300-123">See also</span></span>

- [<span data-ttu-id="56300-124">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56300-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="56300-125">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56300-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
