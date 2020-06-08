---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 5e50255342abae43565fd3556964c24ba4385eb8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500136"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="26537-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26537-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="26537-103">Profil oluşturucuyu, özel durum işlemenin geri alma aşamasının bir işlevi geriye doğru bir şekilde geri yüklemeye başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="26537-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26537-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="26537-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26537-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26537-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="26537-106">\[içinde] bozuk işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="26537-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="26537-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26537-107">Remarks</span></span>  
 <span data-ttu-id="26537-108">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="26537-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="26537-109">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="26537-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="26537-110">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="26537-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26537-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26537-111">Requirements</span></span>  
 <span data-ttu-id="26537-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26537-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26537-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26537-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26537-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26537-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26537-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26537-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26537-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26537-116">See also</span></span>

- [<span data-ttu-id="26537-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26537-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="26537-118">ExceptionUnwindFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26537-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
