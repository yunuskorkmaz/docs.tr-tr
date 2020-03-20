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
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177000"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="afe41-102">ICorProfilerInfo3::GetFunctionTailcall3Info Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afe41-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="afe41-103">[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından profilciye bildirilen işlevin yığın çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="afe41-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="afe41-104">Bu yöntem yalnızca `FunctionTailcall3WithInfo` geri arama sırasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="afe41-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe41-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afe41-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe41-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afe41-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="afe41-107">[içinde] Geri `FunctionID` dönen işlevin.</span><span class="sxs-lookup"><span data-stu-id="afe41-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="afe41-108">[içinde] Belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden opak bir tutamaç.</span><span class="sxs-lookup"><span data-stu-id="afe41-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="afe41-109">Profil oluşturucu, `eltInfo` `FunctionTailcall3WithInfo` işlev tarafından profilciye verilenin aynısını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="afe41-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="afe41-110">[çıkış] Belirli bir yığın çerçevesi hakkında genel bilgileri temsil eden opak bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="afe41-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="afe41-111">Bu tanıtıcı yalnızca `FunctionTailcall3WithInfo` profilleyicinin `GetFunctionTailcall3Info` yöntemi çağırdığı geri arama sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="afe41-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afe41-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afe41-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe41-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afe41-113">Requirements</span></span>  
 <span data-ttu-id="afe41-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe41-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe41-115">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="afe41-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afe41-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afe41-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afe41-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe41-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe41-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afe41-118">See also</span></span>

- [<span data-ttu-id="afe41-119">FonksiyonEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="afe41-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="afe41-120">FonksiyonLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="afe41-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="afe41-121">FonksiyonTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="afe41-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="afe41-122">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afe41-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="afe41-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="afe41-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="afe41-124">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="afe41-124">Profiling</span></span>](index.md)
