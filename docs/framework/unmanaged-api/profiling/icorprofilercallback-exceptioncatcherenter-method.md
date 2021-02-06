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
ms.openlocfilehash: 3a813936a7d1f3a5041e192c85d02b37976e3388
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657638"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="76343-103">ICorProfilerCallback::ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76343-103">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="76343-104">Profil oluşturucuyu denetimin uygun bloğa geçtiğini bildirir `catch` .</span><span class="sxs-lookup"><span data-stu-id="76343-104">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76343-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76343-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76343-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76343-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="76343-107">\[içinde] bloğu içeren işlevin tanımlayıcısı `catch` .</span><span class="sxs-lookup"><span data-stu-id="76343-107">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="76343-108">\[' de] işlenmekte olan özel durumun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="76343-108">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="76343-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76343-109">Remarks</span></span>  

 <span data-ttu-id="76343-110">`ExceptionCatcherEnter`Yöntemi, yalnızca catch noktası tam zamanında (JIT) derleyici ile derlenmişse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="76343-110">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="76343-111">Yönetilmeyen kodda veya çalışma zamanının iç kodunda yakalanan bir özel durum, bu bildirimi çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="76343-111">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="76343-112">`objectId`Bir çöp toplama işlemi, bildirimden bu yana nesneyi taşıdığından, değer tekrar geçirilir `ExceptionThrown` .</span><span class="sxs-lookup"><span data-stu-id="76343-112">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="76343-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="76343-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="76343-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="76343-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="76343-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="76343-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76343-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76343-116">Requirements</span></span>  

 <span data-ttu-id="76343-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76343-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76343-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="76343-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76343-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76343-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76343-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76343-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76343-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76343-121">See also</span></span>

- [<span data-ttu-id="76343-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76343-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="76343-123">ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76343-123">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
