---
title: "ICorProfilerCallback::Initialize Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2eebe596b3459d51afe66df4bb81f74e93f3526e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="62f4b-102">ICorProfilerCallback::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62f4b-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="62f4b-103">Yeni bir ortak dil çalışma zamanı (CLR) uygulaması başlatıldığında kod profil oluşturucu başlatmak üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="62f4b-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f4b-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62f4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62f4b-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="62f4b-106">[içinde](/cpp/atl/iunknown) profil oluşturucu için sorgu gerekir arabirimi bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="62f4b-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f4b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62f4b-107">Remarks</span></span>  
 <span data-ttu-id="62f4b-108">`Initialize` Etkinleştirin (veya devre dışı bırak) değişmez geri aramalar yalnızca fırsatı çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="62f4b-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="62f4b-109">Bir geri çağırma tarafından etkinleştirildikten sonra `Initialize` çağrısı, bunu daha sonra kullanılarak devre dışı bırakılamaz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="62f4b-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="62f4b-110">COR_PRF_MONITOR_IMMUTABLE değeri [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırma gösterir hangi olayların değişmez.</span><span class="sxs-lookup"><span data-stu-id="62f4b-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f4b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62f4b-111">Requirements</span></span>  
 <span data-ttu-id="62f4b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f4b-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62f4b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62f4b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f4b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f4b-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f4b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62f4b-116">See Also</span></span>  
 [<span data-ttu-id="62f4b-117">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="62f4b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="62f4b-118">Shutdown yöntemi</span><span class="sxs-lookup"><span data-stu-id="62f4b-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
