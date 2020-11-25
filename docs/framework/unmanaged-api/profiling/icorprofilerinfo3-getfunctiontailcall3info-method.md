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
ms.openlocfilehash: 27bbb1aac376866be7458a3737af9d89bf761411
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721623"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="622d6-102">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="622d6-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>

<span data-ttu-id="622d6-103">[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="622d6-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="622d6-104">Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri çağırma sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="622d6-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="622d6-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="622d6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="622d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="622d6-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="622d6-107">'ndaki `FunctionID` Döndüren işlevin.</span><span class="sxs-lookup"><span data-stu-id="622d6-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="622d6-108">'ndaki Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="622d6-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="622d6-109">Profil Oluşturucu, `eltInfo` işlev tarafından Profiler 'a verilen aynısını sağlamalıdır `FunctionTailcall3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="622d6-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="622d6-110">dışı Belirli bir yığın çerçevesiyle ilgili genel türler bilgilerini temsil eden donuk bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="622d6-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="622d6-111">Bu tanıtıcı yalnızca `FunctionTailcall3WithInfo` profil oluşturucunun yöntemi olarak çağrıldığı geri çağırma sırasında geçerlidir `GetFunctionTailcall3Info` .</span><span class="sxs-lookup"><span data-stu-id="622d6-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="622d6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="622d6-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="622d6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="622d6-113">Requirements</span></span>  

 <span data-ttu-id="622d6-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="622d6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622d6-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="622d6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="622d6-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="622d6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="622d6-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="622d6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622d6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="622d6-118">See also</span></span>

- [<span data-ttu-id="622d6-119">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="622d6-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="622d6-120">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="622d6-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="622d6-121">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="622d6-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="622d6-122">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="622d6-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="622d6-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="622d6-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="622d6-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="622d6-124">Profiling</span></span>](index.md)
