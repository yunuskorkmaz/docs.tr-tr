---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9cdbc2234519c0dba1a5004246492e7609ea2b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180498"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="4b84e-102">ICorProfilerCallback::ExceptionThrown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b84e-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="4b84e-103">Profil Oluşturucu, bir özel durum olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4b84e-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b84e-104">Yalnızca yönetilen kod özel durum erişirse, bu işlev çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b84e-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b84e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b84e-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b84e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b84e-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="4b84e-107">[in] Özel durum oluşturulmasına neden olan nesnenin kimliği.</span><span class="sxs-lookup"><span data-stu-id="4b84e-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b84e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b84e-108">Remarks</span></span>  
 <span data-ttu-id="4b84e-109">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4b84e-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4b84e-110">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="4b84e-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4b84e-111">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="4b84e-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b84e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b84e-112">Requirements</span></span>  
 <span data-ttu-id="4b84e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b84e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b84e-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b84e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b84e-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b84e-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4b84e-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4b84e-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b84e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b84e-117">See also</span></span>

- [<span data-ttu-id="4b84e-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b84e-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
