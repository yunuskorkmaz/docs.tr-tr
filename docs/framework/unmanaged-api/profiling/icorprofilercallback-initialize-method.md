---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ecea5911771d12df74b260845523dd2b7a012aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494525"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="a4e9f-102">ICorProfilerCallback::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4e9f-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="a4e9f-103">Yeni bir ortak dil çalışma zamanı (CLR) uygulama başlatıldığında, kod profil oluşturucuyu başlatmak üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a4e9f-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4e9f-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4e9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4e9f-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="a4e9f-106">[içinde](/cpp/atl/iunknown) profil oluşturucu için faydalanacaksa arabirimi bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a4e9f-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4e9f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4e9f-107">Remarks</span></span>  
 <span data-ttu-id="a4e9f-108">`Initialize` Sabittir geri çağırmaları etkinleştirmek (veya devre dışı bırakmak) yalnızca fırsat çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="a4e9f-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="a4e9f-109">Bir geri çağırma tarafından etkinleştirildikten sonra `Initialize` çağrısı, bunu daha sonra kullanarak devre dışı bırakılamaz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="a4e9f-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="a4e9f-110">COR_PRF_MONITOR_IMMUTABLE değerini [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırma belirten olayları sabittir.</span><span class="sxs-lookup"><span data-stu-id="a4e9f-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e9f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4e9f-111">Requirements</span></span>  
 <span data-ttu-id="a4e9f-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e9f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e9f-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4e9f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4e9f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4e9f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4e9f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e9f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e9f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4e9f-116">See also</span></span>
- [<span data-ttu-id="a4e9f-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4e9f-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a4e9f-118">Shutdown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4e9f-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
