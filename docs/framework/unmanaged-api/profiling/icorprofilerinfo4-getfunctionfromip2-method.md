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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18099e6e658391d6dae7a666cd0cebefa5859b1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971554"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="01c88-102">ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01c88-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="01c88-103">Yönetilen kod yönerge işaretçisi bir işlevin JIT yeniden derlenen sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="01c88-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01c88-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01c88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01c88-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="01c88-106">[in] Yönetilen kodda yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="01c88-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="01c88-107">[out] İşlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="01c88-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="01c88-108">[out] İşlev JIT yeniden derlenen sürümü kimliği.</span><span class="sxs-lookup"><span data-stu-id="01c88-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01c88-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01c88-109">Remarks</span></span>  
 <span data-ttu-id="01c88-110">`GetFunctionFromIP2` benzer `GetFunctionFromIP`dışında belirtilen IP adresi içeren işlev işlevi kimliği yerine JIT yeniden derlenen Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="01c88-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01c88-111">`GetFunctionFromIP2` bir çöp toplama ise tetikleyebilirsiniz `GetFunctionFromIP` erişemez.</span><span class="sxs-lookup"><span data-stu-id="01c88-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="01c88-112">Daha fazla bilgi için [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="01c88-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01c88-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01c88-113">Requirements</span></span>  
 <span data-ttu-id="01c88-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01c88-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01c88-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01c88-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01c88-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01c88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01c88-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c88-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01c88-118">See also</span></span>

- [<span data-ttu-id="01c88-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01c88-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
