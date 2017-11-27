---
title: "ICorProfilerInfo3::EnumJITedFunctions Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c367ae29cc0daa406356a245f3dc16a671d3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="e16b2-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e16b2-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="e16b2-103">Daha önce JIT derlenmiş tüm işlevleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e16b2-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e16b2-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e16b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e16b2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e16b2-106">[out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="e16b2-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e16b2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e16b2-107">Remarks</span></span>  
 <span data-ttu-id="e16b2-108">Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e16b2-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="e16b2-109">Bu yöntem tarafından döndürülen Numaralandırıcı Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="e16b2-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e16b2-110">Döndürülen numaralandırması yalnızca "0" değerini içeren `COR_PRF_FUNCTION::reJitId` alan.</span><span class="sxs-lookup"><span data-stu-id="e16b2-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="e16b2-111">Geçerli gerekiyorsa `COR_PRF_FUNCTION::reJitId` değerlerini kullanın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e16b2-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e16b2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e16b2-112">Requirements</span></span>  
 <span data-ttu-id="e16b2-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16b2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16b2-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e16b2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e16b2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e16b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e16b2-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16b2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e16b2-117">See Also</span></span>  
 [<span data-ttu-id="e16b2-118">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e16b2-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="e16b2-119">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e16b2-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e16b2-120">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="e16b2-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
