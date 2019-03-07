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
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499699"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="6261e-102">ICorDebugThread::SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6261e-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="6261e-103">Bu Icordebugthread hata ayıklama durumunu açıklayan bir bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6261e-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6261e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6261e-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6261e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6261e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="6261e-106">[in] Bu iş parçacığı hata ayıklama durumunu belirten CorDebugThreadState sabit listesi değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6261e-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6261e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6261e-107">Remarks</span></span>  
 <span data-ttu-id="6261e-108">`SetDebugState` Geçerli iş parçacığı hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6261e-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="6261e-109">(İşlemi devam için gerçek geçerli durumunda olsaydı "Geçerli hata ayıklama durumunu" hata ayıklama durumunu gösterir.) Normal bu THREAD_RUNNING değerdir.</span><span class="sxs-lookup"><span data-stu-id="6261e-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="6261e-110">Yalnızca hata ayıklayıcı, bir iş parçacığı hata ayıklama durumunu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6261e-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="6261e-111">Hata ayıklama durumlarını son boyunca devam eder, bir iş parçacığı üzerinde birden çok THREAD_SUSPENDed devam tutmak istiyorsanız, bunu ayarlamalı ve bundan sonra endişelenmenize gerek yok.</span><span class="sxs-lookup"><span data-stu-id="6261e-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="6261e-112">İş parçacıklarını askıya alma ve sürdürme işlemi kilitlenmeler, genellikle olsa da neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6261e-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="6261e-113">Bu bir iç kalitesi iş parçacıklarında ve işlemlerde ve tasarım.</span><span class="sxs-lookup"><span data-stu-id="6261e-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="6261e-114">Zaman uyumsuz olarak bir hata ayıklayıcı kesme ve kilitlenme ayırmak için iş parçacığı sürdürme.</span><span class="sxs-lookup"><span data-stu-id="6261e-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="6261e-115">Kullanıcı durumu iş parçacığının USER_UNSAFE_POINT içeriyorsa, iş parçacığı bir çöp toplama (GC) engelliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6261e-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="6261e-116">Bu, askıya alınan iş parçacığı bir kilitlenmeye neden olan bir çok daha yüksek şansı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6261e-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="6261e-117">Bu, hata ayıklama olaylarını zaten kuyruğa alınmış etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="6261e-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="6261e-118">Bu nedenle bir hata ayıklayıcı tüm olay sırasındaki boşaltma (çağırarak [Icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) askıya alma ya da iş parçacıklarını önce.</span><span class="sxs-lookup"><span data-stu-id="6261e-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="6261e-119">Aksi takdirde, zaten askıya aldı düşündüğü bir iş parçacığı üzerinde olayları alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6261e-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6261e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6261e-120">Requirements</span></span>  
 <span data-ttu-id="6261e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6261e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6261e-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6261e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6261e-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6261e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6261e-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6261e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
