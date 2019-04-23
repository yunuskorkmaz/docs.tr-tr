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
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107555"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="5150d-102">ICorDebugController Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5150d-102">ICorDebugController Interface</span></span>

<span data-ttu-id="5150d-103">Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.</span><span class="sxs-lookup"><span data-stu-id="5150d-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5150d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5150d-104">Methods</span></span>  
  
|<span data-ttu-id="5150d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5150d-105">Method</span></span>|<span data-ttu-id="5150d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5150d-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="5150d-107">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5150d-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="5150d-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5150d-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="5150d-109">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="5150d-110">Yönetilen iş parçacıklarının yürütülmesini çağrısı yapıldıktan sonra sürdürür [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="5150d-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="5150d-111">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="5150d-112">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="5150d-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="5150d-113">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="5150d-114">Bir numaralandırıcı işlemde etkin yönetilen iş parçacıkları için alır.</span><span class="sxs-lookup"><span data-stu-id="5150d-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="5150d-115">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="5150d-116">Tüm yönetilen geri çağırmaları belirtilen iş parçacığı için sıraya alınmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="5150d-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="5150d-117">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="5150d-118">İşlemdeki iş parçacıkları şu anda özgürce çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="5150d-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="5150d-119">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="5150d-120">İşlemdeki tüm yönetilen iş parçacığı hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5150d-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="5150d-121">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="5150d-122">Yönetilen kod işlemde çalışan tüm iş parçacıkları üzerinde işbirliği yapan Durma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5150d-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="5150d-123">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5150d-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="5150d-124">Belirtilen çıkış kodu ile işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="5150d-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5150d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5150d-125">Remarks</span></span>  
 <span data-ttu-id="5150d-126">Varsa `ICorDebugController` olduğundan bir işlem denetleme, kapsamı işlemin tüm iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5150d-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="5150d-127">Varsa `ICorDebugController` olan bir uygulama etki alanı denetleme, kapsamı yalnızca bu belirli uygulama etki alanının iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5150d-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5150d-128">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5150d-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5150d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5150d-129">Requirements</span></span>  
 <span data-ttu-id="5150d-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5150d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5150d-131">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5150d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5150d-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5150d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5150d-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5150d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5150d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5150d-134">See also</span></span>

- [<span data-ttu-id="5150d-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5150d-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
