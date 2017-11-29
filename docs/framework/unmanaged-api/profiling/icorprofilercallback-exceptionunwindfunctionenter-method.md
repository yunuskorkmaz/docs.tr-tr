---
title: "ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc41dc95776ca31178153402d2e145a3d2c13bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="4412f-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4412f-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="4412f-103">Profil oluşturucu işlevi bırakma özel durum işleme bırakma aşaması başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="4412f-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4412f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4412f-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4412f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4412f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4412f-106">[in] Sapmasına işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="4412f-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4412f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4412f-107">Remarks</span></span>  
 <span data-ttu-id="4412f-108">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4412f-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4412f-109">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="4412f-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4412f-110">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="4412f-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4412f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4412f-111">Requirements</span></span>  
 <span data-ttu-id="4412f-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4412f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4412f-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4412f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4412f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4412f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4412f-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4412f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4412f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4412f-116">See Also</span></span>  
 [<span data-ttu-id="4412f-117">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="4412f-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4412f-118">ExceptionUnwindFunctionLeave yöntemi</span><span class="sxs-lookup"><span data-stu-id="4412f-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
