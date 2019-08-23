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
ms.openlocfilehash: 8c133338ec0edac19f49d435df41e3081c486f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948458"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="1651c-102">ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1651c-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="1651c-103">Yönetilen bir kod yönerge işaretçisini bir işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="1651c-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1651c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1651c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1651c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1651c-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="1651c-106">'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1651c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="1651c-107">dışı İşlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1651c-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="1651c-108">dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="1651c-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1651c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1651c-109">Remarks</span></span>  
 <span data-ttu-id="1651c-110">`GetFunctionFromIP2`, öğesine `GetFunctionFromIP`benzerdir, ancak belirtilen IP adresini içeren işlevin işlev kimliği yerine JIT-yeniden derlenmesi kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1651c-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1651c-111">`GetFunctionFromIP2`bir çöp toplama tetiklenebilir, ancak `GetFunctionFromIP` olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1651c-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="1651c-112">Daha fazla bilgi için bkz. [corprof_e_unsupported_call_sequence hresult](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="1651c-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1651c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1651c-113">Requirements</span></span>  
 <span data-ttu-id="1651c-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1651c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1651c-115">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1651c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1651c-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1651c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1651c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1651c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1651c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1651c-118">See also</span></span>

- [<span data-ttu-id="1651c-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1651c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
