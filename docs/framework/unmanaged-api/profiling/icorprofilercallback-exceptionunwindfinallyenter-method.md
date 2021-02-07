---
description: ': ICorProfilerCallback:: Exceptionunwıniyenter yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
ms.openlocfilehash: e4a701597b318a387405a152f2c3b4758d616eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706090"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="795a9-103">ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="795a9-103">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>

<span data-ttu-id="795a9-104">Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının `finally` belirtilen işlevde içerilen bir yan tümce girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="795a9-104">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795a9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="795a9-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="795a9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="795a9-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="795a9-107">\[içinde] yan tümcesini içeren işlevin KIMLIĞI `finally` .</span><span class="sxs-lookup"><span data-stu-id="795a9-107">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="795a9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="795a9-108">Remarks</span></span>  

 <span data-ttu-id="795a9-109">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="795a9-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="795a9-110">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="795a9-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="795a9-111">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="795a9-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795a9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="795a9-112">Requirements</span></span>  

 <span data-ttu-id="795a9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="795a9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="795a9-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="795a9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="795a9-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="795a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="795a9-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="795a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795a9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="795a9-117">See also</span></span>

- [<span data-ttu-id="795a9-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="795a9-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="795a9-119">GetNotifiedExceptionClauseInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="795a9-119">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="795a9-120">ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="795a9-120">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
