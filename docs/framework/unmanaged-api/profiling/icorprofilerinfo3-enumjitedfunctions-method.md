---
title: ICorProfilerInfo3::EnumJITedFunctions Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7525d107fec7229d9b86eee63bde2aaf2d701b1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190307"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="f13d2-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f13d2-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="f13d2-103">Daha önce JIT olarak derlenmiş tüm işlevler için bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f13d2-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f13d2-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f13d2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f13d2-106">[out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="f13d2-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f13d2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f13d2-107">Remarks</span></span>  
 <span data-ttu-id="f13d2-108">Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f13d2-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="f13d2-109">Bu yöntem tarafından döndürülen Numaralandırıcı, Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="f13d2-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f13d2-110">Döndürülen sabit listesi yalnızca "0" değerini içeren `COR_PRF_FUNCTION::reJitId` alan.</span><span class="sxs-lookup"><span data-stu-id="f13d2-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="f13d2-111">Geçerli gerekiyorsa `COR_PRF_FUNCTION::reJitId` değerlerini kullanın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f13d2-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13d2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f13d2-112">Requirements</span></span>  
 <span data-ttu-id="f13d2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13d2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13d2-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f13d2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f13d2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f13d2-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f13d2-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f13d2-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f13d2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f13d2-117">See also</span></span>

- [<span data-ttu-id="f13d2-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f13d2-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f13d2-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f13d2-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f13d2-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f13d2-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
