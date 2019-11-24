---
title: ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 7e93b92b0b0b4c44955ebc7dfb9d1eb875713c27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449718"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="7d636-102">ICorProfilerInfo3::GetFunctionEnter3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d636-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="7d636-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="7d636-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="7d636-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span><span class="sxs-lookup"><span data-stu-id="7d636-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d636-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d636-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d636-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d636-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7d636-107">[in] The `FunctionID` of the function that is being entered.</span><span class="sxs-lookup"><span data-stu-id="7d636-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7d636-108">[in] An opaque handle that represents information about a given stack frame.</span><span class="sxs-lookup"><span data-stu-id="7d636-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7d636-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="7d636-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="7d636-110">[out] An opaque handle that represents generics information about a given stack frame.</span><span class="sxs-lookup"><span data-stu-id="7d636-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="7d636-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span><span class="sxs-lookup"><span data-stu-id="7d636-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="7d636-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="7d636-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="7d636-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="7d636-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="7d636-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span><span class="sxs-lookup"><span data-stu-id="7d636-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="7d636-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span><span class="sxs-lookup"><span data-stu-id="7d636-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d636-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d636-116">Remarks</span></span>  
 <span data-ttu-id="7d636-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span><span class="sxs-lookup"><span data-stu-id="7d636-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d636-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d636-118">Requirements</span></span>  
 <span data-ttu-id="7d636-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d636-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d636-120">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7d636-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d636-121">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d636-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d636-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d636-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d636-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d636-123">See also</span></span>

- [<span data-ttu-id="7d636-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7d636-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="7d636-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7d636-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="7d636-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7d636-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7d636-127">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d636-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7d636-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d636-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7d636-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d636-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
