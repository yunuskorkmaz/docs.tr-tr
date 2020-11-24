---
title: ICorDebugController Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 1ca9e55a2183ca4293d30607496b588cbf21d6dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679955"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="46562-102">ICorDebugController Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46562-102">ICorDebugController Interface</span></span>

<span data-ttu-id="46562-103"><xref:System.Diagnostics.Process> <xref:System.AppDomain> Kod yürütme bağlamının denetlenebileceği bir ya da olan bir kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46562-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46562-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="46562-104">Methods</span></span>  
  
|<span data-ttu-id="46562-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="46562-105">Method</span></span>|<span data-ttu-id="46562-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46562-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="46562-107">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="46562-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="46562-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="46562-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="46562-109">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="46562-110">[ICorDebugController:: stop](icordebugcontroller-stop-method.md)çağrısından sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="46562-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="46562-111">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="46562-112">Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="46562-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="46562-113">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="46562-114">İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="46562-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="46562-115">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="46562-116">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="46562-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="46562-117">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="46562-118">İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="46562-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="46562-119">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="46562-120">İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46562-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="46562-121">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="46562-122">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="46562-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="46562-123">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46562-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="46562-124">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="46562-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46562-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46562-125">Remarks</span></span>  

 <span data-ttu-id="46562-126">`ICorDebugController`Bir işlemi denetleriyorda kapsam, işlemin tüm iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="46562-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="46562-127">`ICorDebugController`Bir uygulama etki alanını denetleriyorde kapsam, yalnızca söz konusu uygulama etki alanının iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="46562-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46562-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="46562-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46562-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46562-129">Requirements</span></span>  

 <span data-ttu-id="46562-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46562-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46562-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="46562-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46562-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46562-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46562-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46562-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46562-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46562-134">See also</span></span>

- [<span data-ttu-id="46562-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="46562-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
