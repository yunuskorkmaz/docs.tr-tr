---
title: ICorProfilerInfo4::GetFunctionFromIP2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2173326c5c67d1f4d3a8e28f84508fd6affb8299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="bf5f0-102">ICorProfilerInfo4::GetFunctionFromIP2 Metodu</span><span class="sxs-lookup"><span data-stu-id="bf5f0-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="bf5f0-103">Yönetilen kod yönerge işaretçisi bir işlev JIT yeniden derlenmesi sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf5f0-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf5f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf5f0-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="bf5f0-106">[in] Yönetilen kod yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="bf5f0-107">[out] İşlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="bf5f0-108">[out] İşlevin JIT yeniden derlenmesi sürüm kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5f0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf5f0-109">Remarks</span></span>  
 <span data-ttu-id="bf5f0-110">`GetFunctionFromIP2`benzer `GetFunctionFromIP`dışında belirtilen IP adresi içeren işlevinin işlev kimliği yerine JIT yeniden derlenmesi Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf5f0-111">`GetFunctionFromIP2`Çöp toplama, ancak tetikleyebilir `GetFunctionFromIP` almayacak.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="bf5f0-112">Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="bf5f0-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5f0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf5f0-113">Requirements</span></span>  
 <span data-ttu-id="bf5f0-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5f0-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf5f0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf5f0-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf5f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf5f0-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5f0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5f0-118">See Also</span></span>  
 [<span data-ttu-id="bf5f0-119">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf5f0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
