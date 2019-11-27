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
ms.openlocfilehash: d21a793a88cd7561da9acb7daab2dc3bfecf0fc7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449765"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="bd59c-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd59c-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="bd59c-103">Daha önce JıT olarak derlenen tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd59c-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd59c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd59c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd59c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd59c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="bd59c-106">dışı [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd59c-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd59c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd59c-107">Remarks</span></span>  
 <span data-ttu-id="bd59c-108">Bu yöntem [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi `JITCompilation` geri çağırmaları ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="bd59c-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="bd59c-109">Bu yöntemin döndürdüğü Numaralandırıcı, Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="bd59c-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd59c-110">Döndürülen numaralandırma, `COR_PRF_FUNCTION::reJitId` alanının değeri için yalnızca "0" içerir.</span><span class="sxs-lookup"><span data-stu-id="bd59c-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="bd59c-111">Geçerli `COR_PRF_FUNCTION::reJitId` değerlere ihtiyacınız varsa, [ICorProfilerInfo4:: EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd59c-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd59c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd59c-112">Requirements</span></span>  
 <span data-ttu-id="bd59c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd59c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd59c-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd59c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd59c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bd59c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd59c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd59c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd59c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd59c-117">See also</span></span>

- [<span data-ttu-id="bd59c-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd59c-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bd59c-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bd59c-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bd59c-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd59c-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
