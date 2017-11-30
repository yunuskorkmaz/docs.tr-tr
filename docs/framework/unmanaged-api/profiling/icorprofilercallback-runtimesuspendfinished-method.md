---
title: "ICorProfilerCallback::RuntimeSuspendFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c922ee4f986df22f213820b8aed60ea28a76377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="b04f2-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b04f2-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="b04f2-103">Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını askıya tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b04f2-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b04f2-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b04f2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b04f2-105">Remarks</span></span>  
 <span data-ttu-id="b04f2-106">Yönetilmeyen kod içinde tüm çalışma zamanı iş parçacıklarının bunlar çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmek için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b04f2-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="b04f2-107">Çalışma zamanı yeniden devam edene dek bu noktada bunlar da askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="b04f2-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="b04f2-108">Bu durum, çalışma zamanı girin yeni iş parçacığı için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b04f2-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="b04f2-109">Tüm iş parçacıklarının çalışma zamanında ya da kesilebilir kodda zaten oldukları veya kesilebilir kod ulaştığında askıya almak için sorulan hemen askıya ' dir.</span><span class="sxs-lookup"><span data-stu-id="b04f2-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="b04f2-110">`RuntimeSuspendFinished` Geri çağırma aynı iş parçacığı üzerinde gerçekleşmesi için garanti [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b04f2-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04f2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b04f2-111">Requirements</span></span>  
 <span data-ttu-id="b04f2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b04f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04f2-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b04f2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b04f2-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b04f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b04f2-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04f2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b04f2-116">See Also</span></span>  
 [<span data-ttu-id="b04f2-117">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="b04f2-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b04f2-118">RuntimeSuspendAborted yöntemi</span><span class="sxs-lookup"><span data-stu-id="b04f2-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
