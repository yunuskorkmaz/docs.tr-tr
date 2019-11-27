---
title: ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: 5153a25ef87d9c06bb46b74945c8eb68eb041682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443150"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="f2010-102">ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2010-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="f2010-103">Yönetilen bir kod yönerge işaretçisini bir işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="f2010-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2010-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2010-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2010-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2010-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="f2010-106">'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f2010-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="f2010-107">dışı İşlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f2010-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="f2010-108">dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="f2010-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2010-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2010-109">Remarks</span></span>  
 <span data-ttu-id="f2010-110">`GetFunctionFromIP2`, belirtilen IP adresini içeren işlevin işlev KIMLIĞI yerine JıT-yeniden derlenmesi KIMLIĞINI aldığından, `GetFunctionFromIP`benzer.</span><span class="sxs-lookup"><span data-stu-id="f2010-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2010-111">`GetFunctionFromIP2` bir çöp toplamayı tetikleyebilir, ancak `GetFunctionFromIP` olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f2010-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="f2010-112">Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="f2010-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2010-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2010-113">Requirements</span></span>  
 <span data-ttu-id="f2010-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2010-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2010-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2010-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2010-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2010-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2010-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2010-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2010-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2010-118">See also</span></span>

- [<span data-ttu-id="f2010-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2010-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
