---
description: ': ICorProfilerCallback:: UnmanagedToManagedTransition yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2b2bd86798df8b8c46506c924ee201c191e6cb82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657157"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="566ce-103">ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="566ce-103">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>

<span data-ttu-id="566ce-104">Profil oluşturucuyu yönetilmeyen koddan yönetilen koda geçiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="566ce-104">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="566ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="566ce-105">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="566ce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="566ce-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="566ce-107">'ndaki Çağrılmakta olan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="566ce-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="566ce-108">'ndaki Yönetilmeyen koddan yönetilen koda yapılan bir çağrı nedeniyle veya yönetilen bir işlev tarafından çağrılan yönetilmeyen bir işlevden dönüş nedeniyle geçişin yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="566ce-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="566ce-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="566ce-109">Remarks</span></span>  

 <span data-ttu-id="566ce-110">Değeri `reason` COR_PRF_TRANSITION_RETURN ise ve `functionId` null değilse, işlev kimliği yönetilmeyen işlevin değeridir ve hiçbir zaman tam ZAMANıNDA (JIT) derleyici kullanılarak derlenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="566ce-110">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="566ce-111">Yönetilmeyen işlevlerde, bunlarla ilişkili bazı temel bilgiler (örneğin, bir ad ve bazı meta veriler) vardır.</span><span class="sxs-lookup"><span data-stu-id="566ce-111">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="566ce-112">Değeri `reason` COR_PRF_TRANSITION_CALL ise, çağrılan işlevin (yani, yönetilen işlev) henüz JIT derlenmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="566ce-112">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="566ce-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="566ce-113">Requirements</span></span>  

 <span data-ttu-id="566ce-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="566ce-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="566ce-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="566ce-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="566ce-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="566ce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="566ce-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="566ce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566ce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="566ce-118">See also</span></span>

- [<span data-ttu-id="566ce-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="566ce-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="566ce-120">ManagedToUnmanagedTransition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="566ce-120">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="566ce-121">C++ ' ta açık PInvoke kullanma (DllImport özniteliği)</span><span class="sxs-lookup"><span data-stu-id="566ce-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="566ce-122">C++ birlikte çalışabilirliği kullanma (örtük PInvoke)</span><span class="sxs-lookup"><span data-stu-id="566ce-122">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
