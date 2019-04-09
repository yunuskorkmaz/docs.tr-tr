---
title: ICorProfilerCallback3::InitializeForAttach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84d07fe975bab1b0af81299893b52142630b5bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079753"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="29c44-102">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29c44-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="29c44-103">Ortak dil çalışma zamanı (CLR) profil oluşturucu bir iliştirme işleminden sonra kendi durumunu başlatmak üzere bir fırsat vermek tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="29c44-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29c44-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29c44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29c44-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="29c44-106">[in] Bir arabirim işaretçisi için `ICorProfilerInfo*` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="29c44-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="29c44-107">[in] Geçirilen veriler için bir işaretçi [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yöntemi kendi `pvClientData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="29c44-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="29c44-108">Bu parametre null ise `cbClientData` 0 (sıfır) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="29c44-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="29c44-109">Gelen döndürdüğünde CLR bu belleği serbest bırakır `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="29c44-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="29c44-110">[in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="29c44-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c44-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29c44-111">Remarks</span></span>  
 <span data-ttu-id="29c44-112">CLR çağrıları `InitializeForAttach` profil oluşturucu, istek geri çağırmalar için bir fırsat vermek için.</span><span class="sxs-lookup"><span data-stu-id="29c44-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c44-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29c44-113">Requirements</span></span>  
 <span data-ttu-id="29c44-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c44-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c44-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29c44-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29c44-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29c44-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="29c44-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="29c44-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29c44-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29c44-118">See also</span></span>

- [<span data-ttu-id="29c44-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29c44-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="29c44-120">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29c44-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="29c44-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29c44-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="29c44-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29c44-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
