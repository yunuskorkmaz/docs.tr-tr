---
title: Icordebugcontroller Interface1
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
ms.openlocfilehash: 230488201b637c5a53f41dd4c3f204b37e8984fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411476"
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="26be9-102">Icordebugcontroller Interface1</span><span class="sxs-lookup"><span data-stu-id="26be9-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="26be9-103">Bir kapsamı ya da temsil eden bir <xref:System.Diagnostics.Process> veya bir <xref:System.AppDomain>, hangi kod yürütme bağlamı denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="26be9-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26be9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="26be9-104">Methods</span></span>  
  
|<span data-ttu-id="26be9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="26be9-105">Method</span></span>|<span data-ttu-id="26be9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26be9-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="26be9-107">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="26be9-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="26be9-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="26be9-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="26be9-109">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="26be9-110">Yönetilen iş parçacığı yürütülmesi için bir çağrı sonra sürdürür [Icordebugcontroller::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="26be9-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="26be9-111">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="26be9-112">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="26be9-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="26be9-113">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="26be9-114">Bir numaralandırıcı etkin yönetilen iş parçacığı için işlem sırasında alır.</span><span class="sxs-lookup"><span data-stu-id="26be9-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="26be9-115">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="26be9-116">Tüm yönetilen geri aramalar için belirtilen iş parçacığı sıraya alınmış olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="26be9-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="26be9-117">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="26be9-118">İşlemdeki iş parçacıklarının ücretsiz olarak çalışmakta olan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="26be9-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="26be9-119">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="26be9-120">Tüm yönetilen iş parçacığı hata ayıklama durumunu işleminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="26be9-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="26be9-121">Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="26be9-122">Yönetilen kod işlemde çalışan tüm iş parçacıklarının işbirlikçi Dur gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="26be9-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="26be9-123">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26be9-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="26be9-124">Belirtilen çıkış kodu ile işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="26be9-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26be9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26be9-125">Remarks</span></span>  
 <span data-ttu-id="26be9-126">Varsa `ICorDebugController` olduğundan bir işlem denetleme, kapsam işlemin tüm iş parçacıklarının içerir.</span><span class="sxs-lookup"><span data-stu-id="26be9-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="26be9-127">Varsa `ICorDebugController` olan uygulama etki alanı denetleme, kapsamı yalnızca bu belirli uygulama etki alanı iş parçacıklarının içerir.</span><span class="sxs-lookup"><span data-stu-id="26be9-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26be9-128">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="26be9-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26be9-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26be9-129">Requirements</span></span>  
 <span data-ttu-id="26be9-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26be9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26be9-131">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26be9-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26be9-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26be9-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26be9-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26be9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26be9-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26be9-134">See Also</span></span>  
 [<span data-ttu-id="26be9-135">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26be9-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
