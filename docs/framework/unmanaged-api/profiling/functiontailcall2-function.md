---
title: FunctionTailcall2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175193"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="c3b9d-102">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3b9d-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="c3b9d-103">Profiloluşturucuya, şu anda yürütülen işlevin başka bir işleve kuyruk çağrısı yapmak üzere olduğunu ve yığın çerçevesi hakkında bilgi verdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3b9d-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3b9d-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="c3b9d-106">\[in] Kuyruk araması yapmak üzere olan şu anda çalıştırılabilen işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="c3b9d-107">\[in] Profiloluşturucudaha önce [FunctionIDMapper](functionidmapper-function.md)üzerinden belirtilen remapped fonksiyon tanımlayıcısı , bir kuyruk aramayapmak üzere olan şu anda çalıştırılan işlev.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="c3b9d-108">\[in] `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgilere işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="c3b9d-109">Profil oluşturucu [bunu, ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemindeki yürütme motoruna geri geçirilebilen opak bir kulp olarak ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3b9d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3b9d-110">Remarks</span></span>  
 <span data-ttu-id="c3b9d-111">Kuyruk çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk aramasını yapan işlevin arayana döner.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="c3b9d-112">Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](functionleave2-function.md) geri aramasının verilmeyeceğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="c3b9d-113">`func` Değer değişebileceği veya yok `FunctionTailcall2` olabileceğinden, parametrenin değeri işlev döndükten sonra geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="c3b9d-114">İşlev `FunctionTailcall2` bir geri aramadır; bunu uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="c3b9d-115">Uygulama `__declspec`, (`naked`) depolama sınıfı özniteliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c3b9d-116">Yürütme motoru, bu işlevi aramadan önce herhangi bir kayıt kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c3b9d-117">Girişte, kayan nokta birimindekiler (FPU) dahil olmak üzere kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c3b9d-118">Çıkışta, arayan tarafından itilen tüm parametreleri patlatarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c3b9d-119">Çöp toplamayı `FunctionTailcall2` geciktireceği için uygulanması engellememelidir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c3b9d-120">Yığın çöp toplama dostu bir durumda olmayabilir, çünkü uygulama bir çöp toplama girişimi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c3b9d-121">Bir çöp toplama denenir, çalışma süresi `FunctionTailcall2` döndürülene kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="c3b9d-122">Ayrıca, `FunctionTailcall2` işlev yönetilen koda çağrı yapmamalı veya herhangi bir şekilde yönetilen bir bellek ayırmasına neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b9d-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3b9d-123">Requirements</span></span>  
 <span data-ttu-id="c3b9d-124">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b9d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b9d-125">**Üstbilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c3b9d-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c3b9d-126">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3b9d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3b9d-127">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b9d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b9d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b9d-128">See also</span></span>

- [<span data-ttu-id="c3b9d-129">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3b9d-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="c3b9d-130">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3b9d-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="c3b9d-131">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3b9d-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c3b9d-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c3b9d-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
