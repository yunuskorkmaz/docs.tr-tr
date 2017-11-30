---
title: "ICorProfilerCallback3::InitializeForAttach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.InitializeForAttach Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 323f163774407ff2ddfd261ff6d6584a07ed7d8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="f0bbd-102">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0bbd-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="f0bbd-103">Ortak dil çalışma zamanı (CLR) profil oluşturucu ekleme işlemden sonra durumu başlatmak için fırsat verecek şekilde tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0bbd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0bbd-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0bbd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0bbd-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="f0bbd-106">[in] Arabirim işaretçisi için `ICorProfilerInfo*` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="f0bbd-107">[in] Geçirilen veriler için bir işaretçi [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yönteminde kendi `pvClientData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="f0bbd-108">Bu parametre null ise `cbClientData` 0 (sıfır) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="f0bbd-109">Gelen geri döndüğünde CLR bu belleği serbest bırakma `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="f0bbd-110">[in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0bbd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0bbd-111">Remarks</span></span>  
 <span data-ttu-id="f0bbd-112">CLR çağrıları `InitializeForAttach` profil oluşturucu isteği geri aramalar için bir fırsat vermek için.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0bbd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0bbd-113">Requirements</span></span>  
 <span data-ttu-id="f0bbd-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0bbd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0bbd-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0bbd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0bbd-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0bbd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0bbd-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0bbd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bbd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0bbd-118">See Also</span></span>  
 [<span data-ttu-id="f0bbd-119">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0bbd-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f0bbd-120">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0bbd-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f0bbd-121">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0bbd-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f0bbd-122">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bbd-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
