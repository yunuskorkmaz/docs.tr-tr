---
title: FunctionEnter3 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a731df84af0991f80c560db417df0ffe053a5e2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598941"
---
# <a name="functionenter3-function"></a><span data-ttu-id="a7a92-102">FunctionEnter3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a7a92-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="a7a92-103">Profil Oluşturucu, denetim bir işleve geçirilen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a7a92-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7a92-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7a92-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="a7a92-106">[in] Denetimin geçtiğini işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a7a92-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a92-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7a92-107">Remarks</span></span>  
 <span data-ttu-id="a7a92-108">`FunctionEnter3` Geri çağırma işlevini bildirir profil oluşturucu işlevleri adı verilir, ancak destek bağımsız değişken incelemesini yapar.</span><span class="sxs-lookup"><span data-stu-id="a7a92-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="a7a92-109">Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlev, kaydedilecek.</span><span class="sxs-lookup"><span data-stu-id="a7a92-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a7a92-110">`FunctionEnter3` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7a92-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a7a92-111">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a7a92-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a7a92-112">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="a7a92-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a7a92-113">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7a92-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a7a92-114">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a7a92-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a92-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7a92-115">Requirements</span></span>  
 <span data-ttu-id="a7a92-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a92-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a92-117">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a7a92-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a7a92-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7a92-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7a92-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a92-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a92-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a92-120">See also</span></span>

- [<span data-ttu-id="a7a92-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a7a92-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="a7a92-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a7a92-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="a7a92-123">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="a7a92-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="a7a92-124">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="a7a92-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="a7a92-125">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="a7a92-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a7a92-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a7a92-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a7a92-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a7a92-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a7a92-128">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="a7a92-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a7a92-129">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="a7a92-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a7a92-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a7a92-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
