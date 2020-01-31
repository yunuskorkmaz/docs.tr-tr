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
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862411"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="7cf3c-102">ICorProfilerInfo3::GetFunctionLeave3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cf3c-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="7cf3c-103">[FunctionLeave3WithInfo işlev](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve dönüş değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="7cf3c-104">Bu yöntem yalnızca `FunctionLeave3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf3c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cf3c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf3c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cf3c-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7cf3c-107">'ndaki Döndürülen işlevin `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="7cf3c-108">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7cf3c-109">Profil Oluşturucu, [FunctionLeave3WithInfo](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a verilen aynı `eltInfo` sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="7cf3c-110">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="7cf3c-111">Bu tanıtıcı yalnızca profil oluşturucunun `GetFunctionLeave3Info` metodunu çağırdığı `FunctionLeave3WithInfo` geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="7cf3c-112">dışı İşlevden döndürülen değeri içeren [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="7cf3c-113">Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="7cf3c-114">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf3c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cf3c-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf3c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cf3c-116">Requirements</span></span>  
 <span data-ttu-id="7cf3c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf3c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf3c-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7cf3c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cf3c-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7cf3c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf3c-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf3c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf3c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cf3c-121">See also</span></span>

- [<span data-ttu-id="7cf3c-122">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="7cf3c-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="7cf3c-123">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="7cf3c-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="7cf3c-124">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="7cf3c-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7cf3c-125">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7cf3c-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7cf3c-126">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7cf3c-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7cf3c-127">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7cf3c-127">Profiling</span></span>](index.md)
