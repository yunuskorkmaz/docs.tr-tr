---
title: FunctionEnter2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177065"
---
# <a name="functionenter2-function"></a><span data-ttu-id="8ea3e-102">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="8ea3e-103">Profiloluşturucuya denetimin bir işleve geçirildiğini belirtir ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="8ea3e-104">Bu işlev [FunctionEnter](functionenter-function.md) işlevinin yerini alar.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea3e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ea3e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ea3e-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="8ea3e-107">\[in] Denetimin geçtiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="8ea3e-108">\[in] Profiloluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevini kullanarak belirttiği remapped işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="8ea3e-109">\[in] `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgilere işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="8ea3e-110">Profil oluşturucu [bunu, ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemindeki yürütme motoruna geri geçirilebilen opak bir kulp olarak ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="8ea3e-111">\[in] İşlevin bağımsız değişkenlerinin belleğindeki konumları belirten [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) bir yapıya işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="8ea3e-112">Bağımsız değişken bilgilerine erişmek `COR_PRF_ENABLE_FUNCTION_ARGS` için bayrak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="8ea3e-113">Profil oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ea3e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ea3e-114">Remarks</span></span>  
 <span data-ttu-id="8ea3e-115">Değerler değişebileceği `func` `argumentInfo` veya yok `FunctionEnter2` olabileceğinden, işlev döndükten sonra parametrelerin değerleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="8ea3e-116">İşlev `FunctionEnter2` bir geri aramadır; bunu uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="8ea3e-117">Uygulama `__declspec`, (`naked`) depolama sınıfı özniteliği kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8ea3e-118">Yürütme motoru, bu işlevi aramadan önce herhangi bir kayıt kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="8ea3e-119">Girişte, kayan nokta birimindekiler (FPU) dahil olmak üzere kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="8ea3e-120">Çıkışta, arayan tarafından itilen tüm parametreleri patlatarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8ea3e-121">Çöp toplamayı `FunctionEnter2` geciktireceği için uygulanması engellememelidir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8ea3e-122">Yığın çöp toplama dostu bir durumda olmayabilir, çünkü uygulama bir çöp toplama girişimi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8ea3e-123">Bir çöp toplama denenir, çalışma süresi `FunctionEnter2` döndürülene kadar engellenir.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="8ea3e-124">Ayrıca, `FunctionEnter2` işlev yönetilen koda çağrı yapmamalı veya herhangi bir şekilde yönetilen bir bellek ayırmasına neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea3e-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ea3e-125">Requirements</span></span>  
 <span data-ttu-id="8ea3e-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ea3e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ea3e-127">**Üstbilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="8ea3e-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8ea3e-128">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ea3e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ea3e-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ea3e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea3e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea3e-130">See also</span></span>

- [<span data-ttu-id="8ea3e-131">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="8ea3e-132">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="8ea3e-133">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ea3e-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="8ea3e-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8ea3e-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
