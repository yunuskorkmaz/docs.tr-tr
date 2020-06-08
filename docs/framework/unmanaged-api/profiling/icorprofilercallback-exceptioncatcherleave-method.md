---
title: ICorProfilerCallback::ExceptionCatcherLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: cff2dd9fdb05ea4dd160dfa57df6f047beb57f69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500305"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="1829e-102">ICorProfilerCallback::ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1829e-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="1829e-103">Profil oluşturucuyu denetimin uygun bloktan geçirilmekte olduğunu bildirir `catch` .</span><span class="sxs-lookup"><span data-stu-id="1829e-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1829e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1829e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1829e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1829e-105">Remarks</span></span>  
 <span data-ttu-id="1829e-106">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1829e-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1829e-107">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="1829e-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1829e-108">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="1829e-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1829e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1829e-109">Requirements</span></span>  
 <span data-ttu-id="1829e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1829e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1829e-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1829e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1829e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1829e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1829e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1829e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1829e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1829e-114">See also</span></span>

- [<span data-ttu-id="1829e-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1829e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1829e-116">ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1829e-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
