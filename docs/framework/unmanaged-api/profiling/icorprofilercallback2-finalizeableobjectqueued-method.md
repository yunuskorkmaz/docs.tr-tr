---
title: ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4d10b313adc60e2b851d32aeea70e2993480b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451814"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="efc07-102">ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi</span><span class="sxs-lookup"><span data-stu-id="efc07-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="efc07-103">Kod profil oluşturucu bir sonlandırıcı sahip bir nesne yürütülmesi için sonlandırıcıyı iş parçacığı için sıraya bildirir, `Finalize` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efc07-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efc07-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efc07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efc07-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="efc07-106">[in] Değerini [cor_prf_fınalızer_flags](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) sonlandırıcıyı yönlerini açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="efc07-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="efc07-107">[in] Kuyruğa alındı nesnesinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="efc07-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc07-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efc07-108">Requirements</span></span>  
 <span data-ttu-id="efc07-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc07-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efc07-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efc07-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efc07-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc07-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc07-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efc07-113">See Also</span></span>  
 [<span data-ttu-id="efc07-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efc07-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="efc07-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efc07-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
