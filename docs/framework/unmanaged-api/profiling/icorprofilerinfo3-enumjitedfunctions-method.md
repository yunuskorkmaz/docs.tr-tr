---
title: "ICorProfilerInfo3::EnumJITedFunctions Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11a6b34be4f9bf046749941ac12895bf7040e331
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="50cb0-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50cb0-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="50cb0-103">Daha önce JIT derlenmiş tüm işlevleri için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="50cb0-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50cb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50cb0-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50cb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50cb0-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="50cb0-106">[out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="50cb0-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50cb0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50cb0-107">Remarks</span></span>  
 <span data-ttu-id="50cb0-108">Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50cb0-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="50cb0-109">Bu yöntem tarafından döndürülen Numaralandırıcı Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="50cb0-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50cb0-110">Döndürülen numaralandırması yalnızca "0" değerini içeren `COR_PRF_FUNCTION::reJitId` alan.</span><span class="sxs-lookup"><span data-stu-id="50cb0-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="50cb0-111">Geçerli gerekiyorsa `COR_PRF_FUNCTION::reJitId` değerlerini kullanın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50cb0-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50cb0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50cb0-112">Requirements</span></span>  
 <span data-ttu-id="50cb0-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50cb0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50cb0-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50cb0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50cb0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50cb0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50cb0-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50cb0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cb0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50cb0-117">See Also</span></span>  
 [<span data-ttu-id="50cb0-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50cb0-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="50cb0-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50cb0-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="50cb0-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="50cb0-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
