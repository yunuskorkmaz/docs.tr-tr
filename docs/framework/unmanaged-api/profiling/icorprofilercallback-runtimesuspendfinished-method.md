---
title: ICorProfilerCallback::RuntimeSuspendFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f69c39938384c7feca28ae40aba3e80a0ba28ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706660"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="ad03a-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad03a-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="ad03a-103">Profil Oluşturucu çalışma zamanı, tüm çalışma zamanı iş parçacıkları askıya alınması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ad03a-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad03a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad03a-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad03a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad03a-105">Remarks</span></span>  
 <span data-ttu-id="ad03a-106">Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ad03a-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="ad03a-107">Çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="ad03a-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="ad03a-108">Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ad03a-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="ad03a-109">Tüm çalışma zamanında ya da hemen kesilebilir kodda zaten olduğu ya da bunlar kesilebilir kod ulaştığınızda askıya almak için sorulan askıya akışlardır.</span><span class="sxs-lookup"><span data-stu-id="ad03a-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="ad03a-110">`RuntimeSuspendFinished` Aynı iş parçacığı üzerinde gerçekleşmesi için geri çağırma garantisi [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ad03a-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad03a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad03a-111">Requirements</span></span>  
 <span data-ttu-id="ad03a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad03a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad03a-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad03a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad03a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad03a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad03a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad03a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad03a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad03a-116">See also</span></span>
- [<span data-ttu-id="ad03a-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad03a-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ad03a-118">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad03a-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
