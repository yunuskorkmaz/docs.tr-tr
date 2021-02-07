---
description: ': ICorProfilerCallback:: ManagedToUnmanagedTransition yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: bf7f45ae576f9812dee24cd3799a3a87678f7c61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705609"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="08123-103">ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08123-103">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="08123-104">Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="08123-104">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08123-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08123-105">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08123-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08123-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="08123-107">'ndaki Çağrılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="08123-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="08123-108">'ndaki Yönetilen koddan yönetilmeyen koda yapılan bir çağrı nedeniyle veya yönetilmeyen bir işlevden gelen bir dönüş nedeniyle geçiş yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="08123-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08123-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08123-109">Remarks</span></span>  

 <span data-ttu-id="08123-110">Değeri `reason` COR_PRF_TRANSITION_CALL ise, Işlev kimliği yönetilmeyen işlevin değildir ve bu, hiçbir zaman tam zamanında derleyici kullanılarak derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="08123-110">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="08123-111">Yönetilmeyen işlevlerde, bir ad ve bazı meta veriler gibi kendileriyle ilişkili temel bilgiler vardır.</span><span class="sxs-lookup"><span data-stu-id="08123-111">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="08123-112">Yönetilmeyen işlev örtük platform çağırma (PInvoke) kullanılarak çağrılırsa, çalışma zamanı çağrının hedefini belirleyemez ve değeri `functionId` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="08123-112">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="08123-113">Örtük PInvoke hakkında daha fazla bilgi için bkz. [C++ birlikte çalışabilirliği kullanma (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="08123-113">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08123-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08123-114">Requirements</span></span>  

 <span data-ttu-id="08123-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08123-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08123-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="08123-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08123-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08123-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08123-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08123-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08123-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08123-119">See also</span></span>

- [<span data-ttu-id="08123-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08123-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="08123-121">UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08123-121">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="08123-122">C++ ' ta açık PInvoke kullanma (DllImport özniteliği)</span><span class="sxs-lookup"><span data-stu-id="08123-122">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
