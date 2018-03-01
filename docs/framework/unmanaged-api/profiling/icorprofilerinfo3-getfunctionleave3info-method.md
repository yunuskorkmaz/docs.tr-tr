---
title: ICorProfilerInfo3::GetFunctionLeave3Info Metodu
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
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5cbd73b6bfe89bec50eff0e09ec078db912adf25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="ef766-102">ICorProfilerInfo3::GetFunctionLeave3Info Metodu</span><span class="sxs-lookup"><span data-stu-id="ef766-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="ef766-103">Yığın çerçevesi ve için Profil Oluşturucu tarafından bildirilen işlevin dönüş değeri sağlar [Functionleave3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="ef766-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="ef766-104">Bu yöntem yalnızca sırasında çağrılabilir `FunctionLeave3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ef766-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef766-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef766-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef766-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef766-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ef766-107">[in] `FunctionID` İşlevinin döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="ef766-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="ef766-108">[in] Verilen yığın çerçevesi ilgili bilgileri temsil eder donuk işleci.</span><span class="sxs-lookup"><span data-stu-id="ef766-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="ef766-109">Profil Oluşturucu aynı sağlamalıdır `eltInfo` , verilen için Profil Oluşturucu tarafından [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="ef766-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="ef766-110">[out] Verilen yığın çerçevesi genel türler bilgilerini temsil eden bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="ef766-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="ef766-111">Bu işleme yalnızca sırasında geçerli `FunctionLeave3WithInfo` profil oluşturucu çağırıldığı geri çağırma `GetFunctionLeave3Info` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef766-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="ef766-112">[out] Bir işaretçi bir [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) işlevinden döndürülen değeri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="ef766-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="ef766-113">Dönüş değeri bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağı ayarlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef766-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="ef766-114">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayrakları ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="ef766-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef766-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef766-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef766-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef766-116">Requirements</span></span>  
 <span data-ttu-id="ef766-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef766-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef766-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef766-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef766-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef766-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef766-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef766-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef766-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef766-121">See Also</span></span>  
 [<span data-ttu-id="ef766-122">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="ef766-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="ef766-123">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="ef766-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="ef766-124">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="ef766-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="ef766-125">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef766-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="ef766-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ef766-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ef766-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef766-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
