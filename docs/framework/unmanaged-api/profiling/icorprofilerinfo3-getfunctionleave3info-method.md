---
title: ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000629"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="aec65-102">ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec65-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="aec65-103">Yığın çerçevesi ve Profil Oluşturucu tarafından bildirilen işlevin dönüş değeri sağlar [Functionleave3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="aec65-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="aec65-104">Bu yöntem yalnızca sırasında çağrılabilir `FunctionLeave3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="aec65-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aec65-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aec65-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aec65-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aec65-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="aec65-107">[in] `FunctionID` Döndüren işlev.</span><span class="sxs-lookup"><span data-stu-id="aec65-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="aec65-108">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="aec65-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="aec65-109">Profil Oluşturucu, aynı sağlamalıdır `eltInfo` değişken için Profil Oluşturucu tarafından [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="aec65-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="aec65-110">[out] Genel türler belirtilen yığın çerçevesi bilgilerini temsil eden bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="aec65-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="aec65-111">Bu işleyici yalnızca sırasında geçerli `FunctionLeave3WithInfo` profil oluşturucu çağrılır, geri çağırma `GetFunctionLeave3Info` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aec65-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="aec65-112">[out] Bir işaretçi bir [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) işlevden döndürülen değer içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="aec65-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="aec65-113">Dönüş değeri bilgilerini erişmeye `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağı ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aec65-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="aec65-114">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayrakları ayarlamanızı.</span><span class="sxs-lookup"><span data-stu-id="aec65-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aec65-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aec65-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aec65-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aec65-116">Requirements</span></span>  
 <span data-ttu-id="aec65-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aec65-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aec65-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aec65-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aec65-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aec65-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aec65-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aec65-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec65-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec65-121">See also</span></span>

- [<span data-ttu-id="aec65-122">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="aec65-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="aec65-123">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="aec65-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="aec65-124">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="aec65-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="aec65-125">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec65-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="aec65-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aec65-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="aec65-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aec65-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
