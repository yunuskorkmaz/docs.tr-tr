---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: Getfunctionfromıp2 yöntemi'
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
ms.openlocfilehash: f6abda7c9e7d4abcc0f0b256d6a7785cea205d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686810"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="e8b9e-103">ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8b9e-103">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>

<span data-ttu-id="e8b9e-104">Yönetilen bir kod yönerge işaretçisini bir işlevin JıT yeniden derlenmiş sürümüne eşler.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-104">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8b9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8b9e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8b9e-106">Parameters</span></span>  

 `ip`  
 <span data-ttu-id="e8b9e-107">'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-107">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="e8b9e-108">dışı İşlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-108">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="e8b9e-109">dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-109">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8b9e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8b9e-110">Remarks</span></span>  

 <span data-ttu-id="e8b9e-111">`GetFunctionFromIP2` , öğesine benzerdir `GetFunctionFromIP` , ancak BELIRTILEN IP adresini içeren işlevin Işlev kimliği yerıne JIT-yeniden DERLENMESI kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-111">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b9e-112">`GetFunctionFromIP2` bir çöp toplama tetiklenebilir, ancak `GetFunctionFromIP` olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-112">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="e8b9e-113">Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="e8b9e-113">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8b9e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8b9e-114">Requirements</span></span>  

 <span data-ttu-id="e8b9e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8b9e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b9e-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e8b9e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8b9e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e8b9e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8b9e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b9e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b9e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b9e-119">See also</span></span>

- [<span data-ttu-id="e8b9e-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8b9e-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
