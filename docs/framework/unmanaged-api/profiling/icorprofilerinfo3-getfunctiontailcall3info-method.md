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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74f0e6e39f99c9e6981066e6a3171bb9508cf1a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782132"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="337a2-102">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="337a2-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="337a2-103">Profil Oluşturucu tarafından bildirilen işlev yığın çerçevesinde sağlar [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="337a2-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="337a2-104">Bu yöntem yalnızca sırasında çağrılabilir `FunctionTailcall3WithInfo` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="337a2-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="337a2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="337a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="337a2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="337a2-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="337a2-107">[in] `FunctionID` Döndüren işlev.</span><span class="sxs-lookup"><span data-stu-id="337a2-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="337a2-108">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="337a2-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="337a2-109">Profil Oluşturucu, aynı sağlamalıdır `eltInfo` değişken için Profil Oluşturucu tarafından `FunctionTailcall3WithInfo` işlevi.</span><span class="sxs-lookup"><span data-stu-id="337a2-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="337a2-110">[out] Genel türler belirtilen yığın çerçevesi bilgilerini temsil eden bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="337a2-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="337a2-111">Bu işleyici yalnızca sırasında geçerli `FunctionTailcall3WithInfo` profil oluşturucu çağrılır, geri çağırma `GetFunctionTailcall3Info` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="337a2-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="337a2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="337a2-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="337a2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="337a2-113">Requirements</span></span>  
 <span data-ttu-id="337a2-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="337a2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="337a2-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="337a2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="337a2-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="337a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="337a2-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="337a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337a2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="337a2-118">See also</span></span>

- [<span data-ttu-id="337a2-119">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="337a2-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="337a2-120">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="337a2-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="337a2-121">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="337a2-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="337a2-122">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="337a2-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="337a2-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="337a2-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="337a2-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="337a2-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
