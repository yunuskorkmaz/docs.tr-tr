---
description: ': ICorProfilerCallback:: Exceptionatılan yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ExceptionThrown Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 77ebca8fbc52ed0c46a4f76fb5cdf6cb2923edaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706142"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="5ee55-103">ICorProfilerCallback::ExceptionThrown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ee55-103">ICorProfilerCallback::ExceptionThrown Method</span></span>

<span data-ttu-id="5ee55-104">Profiler öğesine bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="5ee55-104">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee55-105">Bu işlev yalnızca özel durum yönetilen koda ulaşırsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ee55-105">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee55-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ee55-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee55-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ee55-107">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="5ee55-108">\[' de] özel durumun oluşturulmasına neden olan nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5ee55-108">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5ee55-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ee55-109">Remarks</span></span>  

 <span data-ttu-id="5ee55-110">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5ee55-110">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5ee55-111">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="5ee55-111">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5ee55-112">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="5ee55-112">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee55-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ee55-113">Requirements</span></span>  

 <span data-ttu-id="5ee55-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee55-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee55-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5ee55-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ee55-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ee55-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee55-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee55-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee55-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee55-118">See also</span></span>

- [<span data-ttu-id="5ee55-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ee55-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
