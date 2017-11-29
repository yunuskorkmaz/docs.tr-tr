---
title: "ICorProfilerCallback::ExceptionCatcherLeave Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 328bc3960a7c456b454ee35ff5ca467f02ef2303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="253ec-102">ICorProfilerCallback::ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="253ec-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="253ec-103">Denetim uygun dışında geçirilmiş profil oluşturucu bildirir `catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="253ec-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="253ec-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="253ec-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="253ec-105">Remarks</span></span>  
 <span data-ttu-id="253ec-106">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="253ec-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="253ec-107">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="253ec-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="253ec-108">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="253ec-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="253ec-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="253ec-109">Requirements</span></span>  
 <span data-ttu-id="253ec-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="253ec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="253ec-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="253ec-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="253ec-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="253ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="253ec-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="253ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253ec-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="253ec-114">See Also</span></span>  
 [<span data-ttu-id="253ec-115">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="253ec-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="253ec-116">ExceptionCatcherEnter yöntemi</span><span class="sxs-lookup"><span data-stu-id="253ec-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
