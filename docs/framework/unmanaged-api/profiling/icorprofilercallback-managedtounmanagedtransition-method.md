---
title: "ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59e36f9285f57b54935e40243e87d44b687686da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="38449-102">ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38449-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="38449-103">Profil Oluşturucu yönetilen koddan yönetilmeyen koda geçiş oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="38449-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38449-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38449-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38449-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38449-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="38449-106">[in] Çağrıldığından işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="38449-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="38449-107">[in] Değerini [cor_prf_transıtıon_reason](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) numaralandırması geçişi yönetilen koddan yönetilmeyen koda bir çağrı nedeniyle veya yönetilmeyen bir tarafından adında bir yönetilen işlevi bir dönüş nedeniyle oluşup oluşmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38449-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38449-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38449-108">Remarks</span></span>  
 <span data-ttu-id="38449-109">Varsa değerini `reason` COR_PRF_TRANSITION_CALL, kimliği: Yönetilmeyen işlevinin hangi asla tam zamanı derleyici kullanarak derlenmiştir, işlevi değil.</span><span class="sxs-lookup"><span data-stu-id="38449-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="38449-110">Yönetilmeyen işlevleri, bir ad ve bazı meta verileri gibi ilişkili temel bilgilere sahip.</span><span class="sxs-lookup"><span data-stu-id="38449-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="38449-111">Yönetilmeyen işlev örtük platform kullanarak çağrıldıklarında (PInvoke) çağırma, çalışma zamanının çağrı hedef ve değerini belirleyemiyor `functionId` null olur.</span><span class="sxs-lookup"><span data-stu-id="38449-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="38449-112">Örtük PInvoke hakkında daha fazla bilgi için bkz: [C++ Çalışabilirliği kullanarak (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="38449-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38449-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38449-113">Requirements</span></span>  
 <span data-ttu-id="38449-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38449-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38449-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38449-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38449-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38449-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38449-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38449-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38449-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38449-118">See Also</span></span>  
 [<span data-ttu-id="38449-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38449-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="38449-120">UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38449-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [<span data-ttu-id="38449-121">C++'ta Açık PInvoke Kullanma (DllImport Özniteliği)</span><span class="sxs-lookup"><span data-stu-id="38449-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
