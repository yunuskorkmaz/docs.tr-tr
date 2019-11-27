---
title: ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e7a25fce945504cff0d07f499ae4bb79378e9f3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449695"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="d3c5a-102">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3c5a-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="d3c5a-103">[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="d3c5a-104">Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c5a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3c5a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3c5a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3c5a-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d3c5a-107">'ndaki Döndürülen işlevin `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="d3c5a-108">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="d3c5a-109">Profil Oluşturucu, `FunctionTailcall3WithInfo` işlevi tarafından Profiler 'a verilen aynı `eltInfo` sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="d3c5a-110">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="d3c5a-111">Bu tanıtıcı yalnızca profil oluşturucunun `GetFunctionTailcall3Info` metodunu çağırdığı `FunctionTailcall3WithInfo` geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3c5a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3c5a-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3c5a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3c5a-113">Requirements</span></span>  
 <span data-ttu-id="d3c5a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3c5a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3c5a-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d3c5a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3c5a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3c5a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3c5a-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3c5a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c5a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3c5a-118">See also</span></span>

- [<span data-ttu-id="d3c5a-119">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="d3c5a-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="d3c5a-120">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="d3c5a-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="d3c5a-121">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="d3c5a-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="d3c5a-122">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3c5a-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d3c5a-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3c5a-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d3c5a-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3c5a-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
