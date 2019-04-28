---
title: ICorProfilerCallback::ExceptionCatcherEnter Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9b47e1d1bfa1d8f6c970e95fe25f62a690d3b91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598214"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="9ec1a-102">ICorProfilerCallback::ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec1a-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="9ec1a-103">Denetimi uygun geçirilen profil oluşturucu bildirir `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ec1a-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ec1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ec1a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9ec1a-106">[in] İşlevi içeren tanımlayıcısı `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="9ec1a-107">[in] İşlenen özel durum tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec1a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ec1a-108">Remarks</span></span>  
 <span data-ttu-id="9ec1a-109">`ExceptionCatcherEnter` Yöntemi, yalnızca catch noktası just-in-time (JIT) derleyici ile derlenmiş kod olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="9ec1a-110">Yönetilmeyen kod veya çalışma zamanı iç kod yakalanan bir özel durum, bu bildirim çağırmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="9ec1a-111">`objectId` Değeri bir çöp toplama bu yana nesne taşındı olduğundan yeniden geçirilir `ExceptionThrown` bildirim.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="9ec1a-112">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9ec1a-113">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9ec1a-114">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec1a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ec1a-115">Requirements</span></span>  
 <span data-ttu-id="9ec1a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec1a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec1a-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ec1a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ec1a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ec1a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec1a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec1a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec1a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec1a-120">See also</span></span>

- [<span data-ttu-id="9ec1a-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ec1a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9ec1a-122">ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec1a-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
