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
ms.openlocfilehash: 50fe7399896c35c1d6595b2d7214280e3009fab5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455807"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="a9a40-102">ICorProfilerCallback3::InitializeForAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9a40-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="a9a40-103">Ortak dil çalışma zamanı (CLR) profil oluşturucu ekleme işlemden sonra durumu başlatmak için fırsat verecek şekilde tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a9a40-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9a40-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9a40-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9a40-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="a9a40-106">[in] Arabirim işaretçisi için `ICorProfilerInfo*` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a9a40-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="a9a40-107">[in] Geçirilen veriler için bir işaretçi [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yönteminde kendi `pvClientData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a9a40-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="a9a40-108">Bu parametre null ise `cbClientData` 0 (sıfır) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a9a40-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="a9a40-109">Gelen geri döndüğünde CLR bu belleği serbest bırakma `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="a9a40-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="a9a40-110">[in] Bayt cinsinden veri boyutu, `pvClientData` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a9a40-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9a40-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9a40-111">Remarks</span></span>  
 <span data-ttu-id="a9a40-112">CLR çağrıları `InitializeForAttach` profil oluşturucu isteği geri aramalar için bir fırsat vermek için.</span><span class="sxs-lookup"><span data-stu-id="a9a40-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a40-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9a40-113">Requirements</span></span>  
 <span data-ttu-id="a9a40-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9a40-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a40-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9a40-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9a40-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9a40-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9a40-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a40-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a40-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9a40-118">See Also</span></span>  
 [<span data-ttu-id="a9a40-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9a40-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a9a40-120">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9a40-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="a9a40-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9a40-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a9a40-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9a40-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
