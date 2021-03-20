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
ms.openlocfilehash: aed3d6c4c3c45b546fa8af1db918a6f68eda9bde
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760411"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="643c0-103">ICorProfilerCallback::ExceptionThrown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="643c0-103">ICorProfilerCallback::ExceptionThrown Method</span></span>

<span data-ttu-id="643c0-104">Profiler öğesine bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="643c0-104">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="643c0-105">Bu işlev yalnızca özel durum yönetilen koda ulaşırsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="643c0-105">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="643c0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="643c0-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="643c0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="643c0-107">Parameters</span></span>

<span data-ttu-id="643c0-108">`thrownObjectId` 'ndaki Özel duruma neden olan nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="643c0-108">`thrownObjectId` [in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="643c0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="643c0-109">Remarks</span></span>  

 <span data-ttu-id="643c0-110">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="643c0-110">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="643c0-111">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="643c0-111">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="643c0-112">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="643c0-112">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="643c0-113">Requirements</span></span>  

 <span data-ttu-id="643c0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643c0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643c0-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="643c0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="643c0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="643c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="643c0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="643c0-118">See also</span></span>

- [<span data-ttu-id="643c0-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="643c0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
