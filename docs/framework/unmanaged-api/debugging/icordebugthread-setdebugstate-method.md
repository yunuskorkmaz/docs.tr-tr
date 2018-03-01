---
title: "ICorDebugThread::SetDebugState Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2754caf11f89358b3e81e6324835d5b2e12f17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="12bd1-102">ICorDebugThread::SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12bd1-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="12bd1-103">Bu Icordebugthread hata ayıklama durumunu açıklayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12bd1-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bd1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12bd1-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12bd1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12bd1-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="12bd1-106">[in] Bu iş parçacığı hata ayıklama durumunu belirtin CorDebugThreadState numaralandırma değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="12bd1-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12bd1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12bd1-107">Remarks</span></span>  
 <span data-ttu-id="12bd1-108">`SetDebugState`iş parçacığı geçerli hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12bd1-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="12bd1-109">(İşlemi devam için gerçek geçerli durumunda olsaydı "Geçerli hata ayıklama durumu" hata ayıklama durumu gösterir.) Normal bu THREAD_RUNNING değerdir.</span><span class="sxs-lookup"><span data-stu-id="12bd1-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="12bd1-110">Hata ayıklayıcı yalnızca bir iş parçacığı hata ayıklama durumunu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="12bd1-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="12bd1-111">Durumları hata ayıklama son çapraz devam eder, böylece THREAD_SUSPENDed birden çok üzerinden devam bir iş parçacığı tutmak istiyorsanız, bir kez ayarlamak ve bundan sonra hakkında endişelenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="12bd1-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="12bd1-112">İş parçacıklarını askıya alma ve sürdürme işlemi kilitlenmeler, genellikle olsa da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="12bd1-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="12bd1-113">Bu bir iç iş parçacıklarında ve işlemlerde kalitesi ve tasarım gereği.</span><span class="sxs-lookup"><span data-stu-id="12bd1-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="12bd1-114">Zaman uyumsuz olarak bir hata ayıklayıcısı bölün ve kilitlenme ayırmak için iş parçacığı sürdürün.</span><span class="sxs-lookup"><span data-stu-id="12bd1-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="12bd1-115">İş parçacığının kullanıcı durumunu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplama (GC) engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="12bd1-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="12bd1-116">Başka bir deyişle, askıya alınmış iş parçacığı bir kilitlenmeye neden bir çok daha yüksek olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="12bd1-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="12bd1-117">Bu olaylar zaten kuyruğa alınmış hata ayıklama etkileyebilir değil.</span><span class="sxs-lookup"><span data-stu-id="12bd1-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="12bd1-118">Bir hata ayıklayıcısı tüm olay sırası böylece boşaltma (çağırarak [Icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) askıya alma veya iş parçacıklarını sürdürme önce.</span><span class="sxs-lookup"><span data-stu-id="12bd1-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="12bd1-119">Else olayları askıya aldı bulunduğu bir iş parçacığında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12bd1-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bd1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12bd1-120">Requirements</span></span>  
 <span data-ttu-id="12bd1-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12bd1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bd1-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12bd1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12bd1-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12bd1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12bd1-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bd1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
