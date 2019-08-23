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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2a083f46f24d6f3f24c63dd2415b85f975cfa29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912859"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="df049-102">ICorDebugController Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df049-102">ICorDebugController Interface</span></span>

<span data-ttu-id="df049-103">Kod yürütme bağlamının denetlenebileceği bir <xref:System.Diagnostics.Process> ya da <xref:System.AppDomain>olan bir kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="df049-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df049-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df049-104">Methods</span></span>  
  
|<span data-ttu-id="df049-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df049-105">Method</span></span>|<span data-ttu-id="df049-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df049-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="df049-107">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="df049-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="df049-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="df049-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="df049-109">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="df049-110">[ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)çağrısından sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="df049-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="df049-111">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="df049-112">Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="df049-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="df049-113">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="df049-114">İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="df049-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="df049-115">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="df049-116">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="df049-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="df049-117">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="df049-118">İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="df049-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="df049-119">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="df049-120">İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="df049-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="df049-121">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="df049-122">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="df049-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="df049-123">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df049-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="df049-124">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="df049-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df049-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df049-125">Remarks</span></span>  
 <span data-ttu-id="df049-126">`ICorDebugController` Bir işlemi denetleriyorda kapsam, işlemin tüm iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="df049-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="df049-127">`ICorDebugController` Bir uygulama etki alanını denetleriyorde kapsam, yalnızca söz konusu uygulama etki alanının iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="df049-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df049-128">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="df049-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df049-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df049-129">Requirements</span></span>  
 <span data-ttu-id="df049-130">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df049-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df049-131">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df049-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df049-132">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df049-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df049-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df049-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df049-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df049-134">See also</span></span>

- [<span data-ttu-id="df049-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df049-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
