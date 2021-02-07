---
description: ': ICorDebugController arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 588c41b5b8d87589facd6085655ed0ad415ec3aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710757"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="bbfc8-103">ICorDebugController Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-103">ICorDebugController Interface</span></span>

<span data-ttu-id="bbfc8-104"><xref:System.Diagnostics.Process> <xref:System.AppDomain> Kod yürütme bağlamının denetlenebileceği bir ya da olan bir kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-104">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbfc8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bbfc8-105">Methods</span></span>  
  
|<span data-ttu-id="bbfc8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bbfc8-106">Method</span></span>|<span data-ttu-id="bbfc8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbfc8-107">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="bbfc8-108">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-108">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="bbfc8-109">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-109">This method is obsolete.</span></span>|  
|[<span data-ttu-id="bbfc8-110">Continue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-110">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="bbfc8-111">[ICorDebugController:: stop](icordebugcontroller-stop-method.md)çağrısından sonra yönetilen iş parçacıklarının yürütülmesini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-111">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="bbfc8-112">Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-112">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="bbfc8-113">Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-113">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="bbfc8-114">EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-114">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="bbfc8-115">İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-115">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="bbfc8-116">HasQueuedCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-116">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="bbfc8-117">Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-117">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="bbfc8-118">IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-118">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="bbfc8-119">İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-119">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="bbfc8-120">SetAllThreadsDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-120">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="bbfc8-121">İşlemdeki tüm yönetilen iş parçacıklarının hata ayıklama durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-121">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="bbfc8-122">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-122">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="bbfc8-123">İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-123">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="bbfc8-124">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbfc8-124">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="bbfc8-125">Belirtilen çıkış koduyla işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-125">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbfc8-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbfc8-126">Remarks</span></span>  

 <span data-ttu-id="bbfc8-127">`ICorDebugController`Bir işlemi denetleriyorda kapsam, işlemin tüm iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-127">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="bbfc8-128">`ICorDebugController`Bir uygulama etki alanını denetleriyorde kapsam, yalnızca söz konusu uygulama etki alanının iş parçacıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-128">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbfc8-129">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfc8-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbfc8-130">Requirements</span></span>  

 <span data-ttu-id="bbfc8-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbfc8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfc8-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bbfc8-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfc8-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bbfc8-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfc8-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfc8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfc8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbfc8-135">See also</span></span>

- [<span data-ttu-id="bbfc8-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bbfc8-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
