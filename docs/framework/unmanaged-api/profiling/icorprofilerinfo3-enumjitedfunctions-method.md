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
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862431"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="0e668-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e668-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="0e668-103">Daha önce JıT olarak derlenen tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e668-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e668-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e668-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e668-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e668-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="0e668-106">dışı [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e668-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e668-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e668-107">Remarks</span></span>  
 <span data-ttu-id="0e668-108">Bu yöntem [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi `JITCompilation` geri çağırmaları ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="0e668-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="0e668-109">Bu yöntemin döndürdüğü Numaralandırıcı, Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="0e668-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e668-110">Döndürülen numaralandırma, `COR_PRF_FUNCTION::reJitId` alanının değeri için yalnızca "0" içerir.</span><span class="sxs-lookup"><span data-stu-id="0e668-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="0e668-111">Geçerli `COR_PRF_FUNCTION::reJitId` değerlere ihtiyacınız varsa, [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e668-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e668-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e668-112">Requirements</span></span>  
 <span data-ttu-id="0e668-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e668-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e668-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0e668-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e668-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0e668-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e668-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e668-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e668-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e668-117">See also</span></span>

- [<span data-ttu-id="0e668-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e668-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0e668-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0e668-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0e668-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e668-120">Profiling</span></span>](index.md)
