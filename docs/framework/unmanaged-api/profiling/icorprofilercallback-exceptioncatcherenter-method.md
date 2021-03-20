---
description: ': ICorProfilerCallback:: ExceptionCatcherEnter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f9ea2b44e7a783f9b21f4aa385585dfebc48b1d4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760528"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="26f92-103">ICorProfilerCallback::ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26f92-103">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="26f92-104">Profil oluşturucuyu denetimin uygun bloğa geçtiğini bildirir `catch` .</span><span class="sxs-lookup"><span data-stu-id="26f92-104">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26f92-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26f92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26f92-106">Parameters</span></span>

<span data-ttu-id="26f92-107">`functionId` 'ndaki Bloğu içeren işlevin tanımlayıcısı `catch` .</span><span class="sxs-lookup"><span data-stu-id="26f92-107">`functionId` [in] The identifier of the function containing the `catch` block.</span></span>
  
<span data-ttu-id="26f92-108">`objectId` 'ndaki İşlenmekte olan özel durumun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="26f92-108">`objectId` [in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="26f92-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26f92-109">Remarks</span></span>  

 <span data-ttu-id="26f92-110">`ExceptionCatcherEnter`Yöntemi, yalnızca catch noktası tam zamanında (JIT) derleyici ile derlenmişse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26f92-110">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="26f92-111">Yönetilmeyen kodda veya çalışma zamanının iç kodunda yakalanan bir özel durum, bu bildirimi çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="26f92-111">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="26f92-112">`objectId`Bir çöp toplama işlemi, bildirimden bu yana nesneyi taşıdığından, değer tekrar geçirilir `ExceptionThrown` .</span><span class="sxs-lookup"><span data-stu-id="26f92-112">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="26f92-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="26f92-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="26f92-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="26f92-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="26f92-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="26f92-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f92-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26f92-116">Requirements</span></span>  

 <span data-ttu-id="26f92-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f92-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f92-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26f92-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26f92-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26f92-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26f92-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f92-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f92-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26f92-121">See also</span></span>

- [<span data-ttu-id="26f92-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26f92-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="26f92-123">ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26f92-123">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
