---
description: ': ICorDebugThread:: SetDebugState Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 40339cbce8d30617738151c0a32466c2361e3a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658808"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="a6553-103">ICorDebugThread::SetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6553-103">ICorDebugThread::SetDebugState Method</span></span>

<span data-ttu-id="a6553-104">Bu ICorDebugThread 'in hata ayıklama durumunu tanımlayan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6553-104">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6553-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6553-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6553-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6553-106">Parameters</span></span>  

 `state`  
 <span data-ttu-id="a6553-107">'ndaki Bu iş parçacığının hata ayıklama durumunu belirten, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a6553-107">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6553-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6553-108">Remarks</span></span>  

 <span data-ttu-id="a6553-109">`SetDebugState` iş parçacığının geçerli hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6553-109">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="a6553-110">("Geçerli hata ayıklama durumu" işlemi devam etseydi, gerçek geçerli durum değil, hata ayıklama durumunu temsil eder.) Bunun için normal değer THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="a6553-110">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="a6553-111">Yalnızca hata ayıklayıcı bir iş parçacığının hata ayıklama durumunu etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="a6553-111">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="a6553-112">Hata ayıklama durumları son boyunca devam eder, bu nedenle bir iş parçacığı THREAD_SUSPENDed birden çok kez devam etmek istiyorsanız, onu bir kez ayarlayabilir ve bundan sonra endişelenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="a6553-112">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="a6553-113">İş parçacıklarını askıya almak ve işlemi sürdürmek kilitlenmeye neden olabilir, ancak bu genellikle düşüktür.</span><span class="sxs-lookup"><span data-stu-id="a6553-113">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="a6553-114">Bu, iş parçacıklarının ve işlemlerin gerçek bir kalitesidir ve tasarıma göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="a6553-114">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="a6553-115">Hata ayıklayıcı kilitlenme kesmek için zaman uyumsuz olarak kesintiye uğratır ve iş parçacıklarını sürdürür.</span><span class="sxs-lookup"><span data-stu-id="a6553-115">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="a6553-116">İş parçacığının kullanıcı durumu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplamayı (GC) engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a6553-116">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="a6553-117">Bu, askıya alınan iş parçacığının kilitlenmeye neden olma olasılığını çok daha yüksek olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a6553-117">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="a6553-118">Bu, zaten kuyruğa alınmış olan hata ayıklama olaylarını etkilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a6553-118">This may not affect debug events already queued.</span></span> <span data-ttu-id="a6553-119">Bu nedenle, iş parçacıklarını askıya almadan veya devam ettirmeden önce hata ayıklayıcı tüm olay kuyruğunu ( [ICorDebugController:: HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)çağırarak) boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6553-119">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="a6553-120">Diğer bir deyişle, zaten askıya alınmış olduğunu düşündüğü bir iş parçacığında olayları alabilir.</span><span class="sxs-lookup"><span data-stu-id="a6553-120">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6553-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6553-121">Requirements</span></span>  

 <span data-ttu-id="a6553-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6553-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6553-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6553-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6553-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a6553-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6553-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6553-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
