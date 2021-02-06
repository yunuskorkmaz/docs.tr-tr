---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo3:: Getfunctionleave3ınfo yöntemi'
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
ms.openlocfilehash: 3031190a3603bedb3f58e7a86747542831c72291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646804"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="9ed09-103">ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ed09-103">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>

<span data-ttu-id="9ed09-104">[FunctionLeave3WithInfo işlev](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve dönüş değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ed09-104">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="9ed09-105">Bu yöntem yalnızca `FunctionLeave3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed09-105">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed09-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ed09-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ed09-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ed09-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="9ed09-108">'ndaki `FunctionID` Döndüren işlevin.</span><span class="sxs-lookup"><span data-stu-id="9ed09-108">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="9ed09-109">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9ed09-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9ed09-110">Profil Oluşturucu, `eltInfo` [FunctionLeave3WithInfo](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a verilen aynısını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ed09-110">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="9ed09-111">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9ed09-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="9ed09-112">Bu tanıtıcı yalnızca `FunctionLeave3WithInfo` profil oluşturucunun yöntemi olarak çağrıldığı geri çağırma sırasında geçerlidir `GetFunctionLeave3Info` .</span><span class="sxs-lookup"><span data-stu-id="9ed09-112">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="9ed09-113">dışı İşlevden döndürülen değeri içeren [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9ed09-113">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="9ed09-114">Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ed09-114">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="9ed09-115">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed09-115">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed09-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ed09-116">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed09-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ed09-117">Requirements</span></span>  

 <span data-ttu-id="9ed09-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed09-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed09-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ed09-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ed09-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9ed09-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed09-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed09-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed09-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed09-122">See also</span></span>

- [<span data-ttu-id="9ed09-123">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ed09-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="9ed09-124">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ed09-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="9ed09-125">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="9ed09-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="9ed09-126">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ed09-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9ed09-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9ed09-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9ed09-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ed09-128">Profiling</span></span>](index.md)
