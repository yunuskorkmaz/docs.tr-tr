---
title: "ICorProfilerCallback::ExceptionThrown Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionThrown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3986ca8205297a36bb54825a7af72aeb9821f75b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="d004f-102">ICorProfilerCallback::ExceptionThrown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d004f-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="d004f-103">Profil Oluşturucu bir özel durum bildirir.</span><span class="sxs-lookup"><span data-stu-id="d004f-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d004f-104">Bu işlev yalnızca özel durum yönetilen kod ulaşırsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d004f-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d004f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d004f-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d004f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d004f-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="d004f-107">[in] Özel durum nedeniyle nesne kimliği.</span><span class="sxs-lookup"><span data-stu-id="d004f-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d004f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d004f-108">Remarks</span></span>  
 <span data-ttu-id="d004f-109">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d004f-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="d004f-110">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="d004f-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="d004f-111">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="d004f-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d004f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d004f-112">Requirements</span></span>  
 <span data-ttu-id="d004f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d004f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d004f-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d004f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d004f-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d004f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d004f-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d004f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d004f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d004f-117">See Also</span></span>  
 [<span data-ttu-id="d004f-118">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="d004f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
