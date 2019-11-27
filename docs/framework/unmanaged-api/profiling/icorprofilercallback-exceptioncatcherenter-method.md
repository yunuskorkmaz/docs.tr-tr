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
ms.openlocfilehash: 9c9cd0b042dc22f35c38e349ab8881dafc602731
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445020"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="7902e-102">ICorProfilerCallback::ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7902e-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="7902e-103">Profil oluşturucuyu denetimin uygun `catch` bloğuna geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="7902e-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7902e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7902e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7902e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7902e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7902e-106">'ndaki `catch` bloğunu içeren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7902e-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="7902e-107">'ndaki İşlenmekte olan özel durumun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7902e-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7902e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7902e-108">Remarks</span></span>  
 <span data-ttu-id="7902e-109">`ExceptionCatcherEnter` yöntemi, yalnızca catch noktası tam zamanında (JıT) derleyici ile derlenmişse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7902e-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="7902e-110">Yönetilmeyen kodda veya çalışma zamanının iç kodunda yakalanan bir özel durum, bu bildirimi çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="7902e-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="7902e-111">Bir çöp toplama işlemi `ExceptionThrown` bildiriminden bu yana nesneyi taşıdığından `objectId` değer tekrar geçirilir.</span><span class="sxs-lookup"><span data-stu-id="7902e-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="7902e-112">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7902e-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="7902e-113">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="7902e-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="7902e-114">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="7902e-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7902e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7902e-115">Requirements</span></span>  
 <span data-ttu-id="7902e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7902e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7902e-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7902e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7902e-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7902e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7902e-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7902e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7902e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7902e-120">See also</span></span>

- [<span data-ttu-id="7902e-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7902e-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7902e-122">ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7902e-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
