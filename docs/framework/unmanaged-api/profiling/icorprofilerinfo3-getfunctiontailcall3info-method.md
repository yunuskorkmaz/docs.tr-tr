---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo3:: Getfunctiontailcall3ınfo yöntemi'
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
ms.openlocfilehash: a8976a11cf7a2c556afa62a559e3a294d81b9a1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646809"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="b0332-103">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0332-103">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>

<span data-ttu-id="b0332-104">[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0332-104">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="b0332-105">Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0332-105">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0332-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0332-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0332-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0332-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="b0332-108">'ndaki `FunctionID` Döndüren işlevin.</span><span class="sxs-lookup"><span data-stu-id="b0332-108">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b0332-109">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="b0332-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b0332-110">Profil Oluşturucu, `eltInfo` işlev tarafından Profiler 'a verilen aynısını sağlamalıdır `FunctionTailcall3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="b0332-110">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b0332-111">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="b0332-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b0332-112">Bu tanıtıcı yalnızca `FunctionTailcall3WithInfo` profil oluşturucunun yöntemi olarak çağrıldığı geri çağırma sırasında geçerlidir `GetFunctionTailcall3Info` .</span><span class="sxs-lookup"><span data-stu-id="b0332-112">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0332-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0332-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0332-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0332-114">Requirements</span></span>  

 <span data-ttu-id="b0332-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0332-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0332-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0332-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0332-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0332-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0332-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0332-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0332-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0332-119">See also</span></span>

- [<span data-ttu-id="b0332-120">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="b0332-120">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="b0332-121">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="b0332-121">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="b0332-122">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="b0332-122">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b0332-123">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0332-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b0332-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0332-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b0332-125">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0332-125">Profiling</span></span>](index.md)
