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
ms.openlocfilehash: f81b671721e1416ab9717442d4d7fc727b938ee2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980496"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="f747b-102">ICorDebugController Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f747b-102">ICorDebugController Interface</span></span>

<span data-ttu-id="f747b-103">Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.</span><span class="sxs-lookup"><span data-stu-id="f747b-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f747b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f747b-104">Methods</span></span>  
  
|<span data-ttu-id="f747b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f747b-105">Method</span></span>|<span data-ttu-id="f747b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f747b-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="f747b-107">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f747b-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="f747b-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f747b-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="f747b-109">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="f747b-110">Yönetilen iş parçacıklarının yürütülmesini çağrısı yapıldıktan sonra sürdürür [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="f747b-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="f747b-111">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="f747b-112">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="f747b-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="f747b-113">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="f747b-114">Bir numaralandırıcı işlemde etkin yönetilen iş parçacıkları için alır.</span><span class="sxs-lookup"><span data-stu-id="f747b-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="f747b-115">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="f747b-116">Tüm yönetilen geri çağırmaları belirtilen iş parçacığı için sıraya alınmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f747b-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="f747b-117">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="f747b-118">İşlemdeki iş parçacıkları şu anda özgürce çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f747b-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="f747b-119">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="f747b-120">İşlemdeki tüm yönetilen iş parçacığı hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f747b-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="f747b-121">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="f747b-122">Yönetilen kod işlemde çalışan tüm iş parçacıkları üzerinde işbirliği yapan Durma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f747b-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="f747b-123">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f747b-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="f747b-124">Belirtilen çıkış kodu ile işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="f747b-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f747b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f747b-125">Remarks</span></span>  
 <span data-ttu-id="f747b-126">Varsa `ICorDebugController` olduğundan bir işlem denetleme, kapsamı işlemin tüm iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f747b-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="f747b-127">Varsa `ICorDebugController` olan bir uygulama etki alanı denetleme, kapsamı yalnızca bu belirli uygulama etki alanının iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f747b-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f747b-128">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f747b-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f747b-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f747b-129">Requirements</span></span>  
 <span data-ttu-id="f747b-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f747b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f747b-131">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f747b-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f747b-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f747b-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f747b-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f747b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f747b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f747b-134">See also</span></span>
- [<span data-ttu-id="f747b-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f747b-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
