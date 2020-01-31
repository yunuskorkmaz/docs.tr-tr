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
ms.openlocfilehash: add89fe81fccbd5e6f5ad5d27f0ab3ace489963e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868531"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="c8e9e-102">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8e9e-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="c8e9e-103">[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="c8e9e-104">Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8e9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8e9e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8e9e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c8e9e-107">'ndaki Döndürülen işlevin `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c8e9e-108">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c8e9e-109">Profil Oluşturucu, `FunctionTailcall3WithInfo` işlevi tarafından Profiler 'a verilen aynı `eltInfo` sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="c8e9e-110">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="c8e9e-111">Bu tanıtıcı yalnızca profil oluşturucunun `GetFunctionTailcall3Info` metodunu çağırdığı `FunctionTailcall3WithInfo` geri çağırma sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8e9e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8e9e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e9e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8e9e-113">Requirements</span></span>  
 <span data-ttu-id="c8e9e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e9e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e9e-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c8e9e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8e9e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c8e9e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8e9e-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8e9e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e9e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e9e-118">See also</span></span>

- [<span data-ttu-id="c8e9e-119">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="c8e9e-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="c8e9e-120">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="c8e9e-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="c8e9e-121">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="c8e9e-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c8e9e-122">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8e9e-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c8e9e-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c8e9e-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c8e9e-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8e9e-124">Profiling</span></span>](index.md)
