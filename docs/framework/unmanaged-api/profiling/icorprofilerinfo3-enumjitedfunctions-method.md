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
ms.openlocfilehash: 3ebf4a7706b3d3495e4a617b4f86a50281115436
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496561"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="f9b75-102">ICorProfilerInfo3::EnumJITedFunctions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b75-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="f9b75-103">Daha önce JıT olarak derlenen tüm işlevler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9b75-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b75-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9b75-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9b75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9b75-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f9b75-106">dışı [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9b75-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9b75-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9b75-107">Remarks</span></span>  
 <span data-ttu-id="f9b75-108">Bu yöntem `JITCompilation` [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi geri çağırmalar ile çakışabilir.</span><span class="sxs-lookup"><span data-stu-id="f9b75-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="f9b75-109">Bu yöntemin döndürdüğü Numaralandırıcı, Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.</span><span class="sxs-lookup"><span data-stu-id="f9b75-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9b75-110">Döndürülen numaralandırma alanın değeri için yalnızca "0" içerir `COR_PRF_FUNCTION::reJitId` .</span><span class="sxs-lookup"><span data-stu-id="f9b75-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="f9b75-111">Geçerli değerlere ihtiyacınız varsa `COR_PRF_FUNCTION::reJitId` , [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9b75-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b75-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9b75-112">Requirements</span></span>  
 <span data-ttu-id="f9b75-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b75-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b75-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f9b75-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9b75-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9b75-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9b75-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b75-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b75-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9b75-117">See also</span></span>

- [<span data-ttu-id="f9b75-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9b75-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f9b75-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9b75-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f9b75-120">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9b75-120">Profiling</span></span>](index.md)
