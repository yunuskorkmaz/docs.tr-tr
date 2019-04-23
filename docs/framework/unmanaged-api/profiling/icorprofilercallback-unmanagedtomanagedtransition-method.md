---
title: ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 312f133c263becfd815f1b4ad48dff4892963aaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227859"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="480bc-102">ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="480bc-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="480bc-103">Profil Oluşturucu, yönetilmeyen koddan yönetilen koda geçiş oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="480bc-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="480bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="480bc-104">Syntax</span></span>  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="480bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="480bc-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="480bc-106">[in] Aranan işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="480bc-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="480bc-107">[in] Değerini [cor_prf_transıtıon_reason](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) geçişi, yönetilmeyen koddan yönetilen koda bir çağrı nedeniyle veya yönetilmeyen bir işlev tarafından yönetilen bir adlı geri döndürme nedeniyle oluşup oluşmadığını belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="480bc-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="480bc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="480bc-108">Remarks</span></span>  
 <span data-ttu-id="480bc-109">Varsa değerini `reason` COR_PRF_TRANSITION_RETURN olduğu ve `functionId` null olmayan işlev kimliği yönetilmeyen işleve olan ve hiçbir zaman just-in-time (JIT) derleyici kullanarak derlenen olan.</span><span class="sxs-lookup"><span data-stu-id="480bc-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="480bc-110">Yönetilmeyen işlevleri kendileriyle ilişkili bir ad ve bazı meta verileri gibi bazı temel bilgileri var.</span><span class="sxs-lookup"><span data-stu-id="480bc-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="480bc-111">Varsa değerini `reason` COR_PRF_TRANSITION_CALL, olan (diğer bir deyişle, yönetilen işlevi) çağrılan işlev henüz JIT olarak derlenmiş ayarlanmamış olduğunu mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="480bc-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="480bc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="480bc-112">Requirements</span></span>  
 <span data-ttu-id="480bc-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="480bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="480bc-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="480bc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="480bc-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="480bc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="480bc-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="480bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480bc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="480bc-117">See also</span></span>

- [<span data-ttu-id="480bc-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="480bc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="480bc-119">ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="480bc-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="480bc-120">C++'ta Açık PInvoke Kullanma (DllImport Özniteliği)</span><span class="sxs-lookup"><span data-stu-id="480bc-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="480bc-121">C++ Birlikte Çalışabilirliği Kullanma (Örtük PInvoke)</span><span class="sxs-lookup"><span data-stu-id="480bc-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
