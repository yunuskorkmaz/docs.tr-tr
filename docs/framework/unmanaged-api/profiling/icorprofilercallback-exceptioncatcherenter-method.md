---
title: "ICorProfilerCallback::ExceptionCatcherEnter Yöntemi"
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
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a72b2e75ee622bab357046ff29fac4aa9223d7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="b3b31-102">ICorProfilerCallback::ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3b31-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="b3b31-103">Denetim uygun geçirilmiş profil oluşturucu bildirir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="b3b31-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3b31-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3b31-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3b31-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b3b31-106">[in] İşlevi içeren tanımlayıcı `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="b3b31-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="b3b31-107">[in] İşlenen özel tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="b3b31-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3b31-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3b31-108">Remarks</span></span>  
 <span data-ttu-id="b3b31-109">`ExceptionCatcherEnter` Yalnızca yakalama noktası tam zamanında (JIT) derleyicisi ile derlenmiş kod ise yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b3b31-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b3b31-110">Yönetilmeyen kod veya iç kod çalışma zamanının görevinde bir özel durum, bu bildirim çağırmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b3b31-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="b3b31-111">`objectId` Değeri çöp toplama bu yana nesne taşınmış olması beri yeniden geçirilir `ExceptionThrown` bildirim.</span><span class="sxs-lookup"><span data-stu-id="b3b31-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="b3b31-112">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b3b31-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b3b31-113">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="b3b31-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b3b31-114">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="b3b31-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b31-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3b31-115">Requirements</span></span>  
 <span data-ttu-id="b3b31-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b31-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b31-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3b31-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3b31-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3b31-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3b31-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b31-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b31-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3b31-120">See Also</span></span>  
 [<span data-ttu-id="b3b31-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3b31-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b3b31-122">ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3b31-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
