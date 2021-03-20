---
description: ': ICorProfilerCallback:: Initialize yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: c7138a1a39a1d32c751c205a86c00e6070a236b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760424"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="04c49-103">ICorProfilerCallback::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04c49-103">ICorProfilerCallback::Initialize Method</span></span>

<span data-ttu-id="04c49-104">Her yeni ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucuyu başlatmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="04c49-104">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c49-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04c49-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04c49-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04c49-106">Parameters</span></span>

<span data-ttu-id="04c49-107">`pICorProfilerInfoUnk`'ndaki Profil oluşturucunun bir [ICorProfilerInfo](icorprofilerinfo-interface.md) arabirim işaretçisi için sorgulaması gereken bir [IUnknown](/cpp/atl/iunknown) arabirimine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04c49-107">`pICorProfilerInfoUnk` [in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="04c49-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04c49-108">Remarks</span></span>  

 <span data-ttu-id="04c49-109">`Initialize`Çağrı, sabit olan geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) için tek fırsattır.</span><span class="sxs-lookup"><span data-stu-id="04c49-109">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="04c49-110">Çağrı tarafından bir geri çağırma etkinleştirildikten sonra `Initialize` [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)kullanılarak daha sonra devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="04c49-110">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="04c49-111">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) sabit listesinin COR_PRF_MONITOR_IMMUTABLE değeri, hangi olayların sabit olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="04c49-111">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04c49-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04c49-112">Requirements</span></span>  

 <span data-ttu-id="04c49-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04c49-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04c49-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="04c49-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04c49-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="04c49-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04c49-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04c49-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c49-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c49-117">See also</span></span>

- [<span data-ttu-id="04c49-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04c49-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="04c49-119">Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04c49-119">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
