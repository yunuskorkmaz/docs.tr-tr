---
title: ICorDebugThread::SetDebugState Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ada120b9cb4100bfadff83d96e0226f911958bf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420771"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="00592-102">ICorDebugThread::SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00592-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="00592-103">Bu Icordebugthread hata ayıklama durumunu açıklayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00592-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00592-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00592-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00592-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00592-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="00592-106">[in] Bu iş parçacığı hata ayıklama durumunu belirtin CorDebugThreadState numaralandırma değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="00592-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00592-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00592-107">Remarks</span></span>  
 <span data-ttu-id="00592-108">`SetDebugState` iş parçacığı geçerli hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00592-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="00592-109">(İşlemi devam için gerçek geçerli durumunda olsaydı "Geçerli hata ayıklama durumu" hata ayıklama durumu gösterir.) Normal bu THREAD_RUNNING değerdir.</span><span class="sxs-lookup"><span data-stu-id="00592-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="00592-110">Hata ayıklayıcı yalnızca bir iş parçacığı hata ayıklama durumunu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="00592-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="00592-111">Durumları hata ayıklama son çapraz devam eder, böylece THREAD_SUSPENDed birden çok üzerinden devam bir iş parçacığı tutmak istiyorsanız, bir kez ayarlamak ve bundan sonra hakkında endişelenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="00592-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="00592-112">İş parçacıklarını askıya alma ve sürdürme işlemi kilitlenmeler, genellikle olsa da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="00592-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="00592-113">Bu bir iç iş parçacıklarında ve işlemlerde kalitesi ve tasarım gereği.</span><span class="sxs-lookup"><span data-stu-id="00592-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="00592-114">Zaman uyumsuz olarak bir hata ayıklayıcısı bölün ve kilitlenme ayırmak için iş parçacığı sürdürün.</span><span class="sxs-lookup"><span data-stu-id="00592-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="00592-115">İş parçacığının kullanıcı durumunu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplama (GC) engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="00592-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="00592-116">Başka bir deyişle, askıya alınmış iş parçacığı bir kilitlenmeye neden bir çok daha yüksek olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="00592-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="00592-117">Bu olaylar zaten kuyruğa alınmış hata ayıklama etkileyebilir değil.</span><span class="sxs-lookup"><span data-stu-id="00592-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="00592-118">Bir hata ayıklayıcısı tüm olay sırası böylece boşaltma (çağırarak [Icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) askıya alma veya iş parçacıklarını sürdürme önce.</span><span class="sxs-lookup"><span data-stu-id="00592-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="00592-119">Else olayları askıya aldı bulunduğu bir iş parçacığında alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00592-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00592-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00592-120">Requirements</span></span>  
 <span data-ttu-id="00592-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00592-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00592-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00592-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00592-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00592-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00592-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00592-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
