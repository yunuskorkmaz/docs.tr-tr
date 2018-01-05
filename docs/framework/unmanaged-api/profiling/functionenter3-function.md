---
title: "FunctionEnter3 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter3
helpviewer_keywords: FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bbdfa608f1ea60462dc432a7c2b98cafe66d7be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="532a9-102">FunctionEnter3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="532a9-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="532a9-103">Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="532a9-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="532a9-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="532a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="532a9-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="532a9-106">[in] Denetim geçirilen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="532a9-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="532a9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="532a9-107">Remarks</span></span>  
 <span data-ttu-id="532a9-108">`FunctionEnter3` Geri çağırma işlevi işlevleri adı verilir, ancak mu destek bağımsız değişkeni denetleme profil oluşturucu bildirir.</span><span class="sxs-lookup"><span data-stu-id="532a9-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="532a9-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlevin kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="532a9-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="532a9-110">`FunctionEnter3` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="532a9-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="532a9-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="532a9-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="532a9-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="532a9-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="532a9-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="532a9-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="532a9-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="532a9-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="532a9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="532a9-115">Requirements</span></span>  
 <span data-ttu-id="532a9-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="532a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="532a9-117">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="532a9-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="532a9-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="532a9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="532a9-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="532a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532a9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="532a9-120">See Also</span></span>  
 [<span data-ttu-id="532a9-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="532a9-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="532a9-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="532a9-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="532a9-123">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="532a9-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="532a9-124">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="532a9-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="532a9-125">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="532a9-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="532a9-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="532a9-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="532a9-127">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="532a9-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="532a9-128">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="532a9-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="532a9-129">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="532a9-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="532a9-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="532a9-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
