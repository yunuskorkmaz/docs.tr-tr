---
title: ICorDebugController::EnumerateThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4bb4072c574edeac1c531978fac75595c252e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481605"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="8245a-102">ICorDebugController::EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8245a-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="8245a-103">Bir numaralandırıcı işlemde etkin yönetilen iş parçacıkları için alır.</span><span class="sxs-lookup"><span data-stu-id="8245a-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8245a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8245a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8245a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8245a-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="8245a-106">[out] İşlem sırasında etkin olan tüm yönetilen iş parçacıkları için bir numaralandırıcı temsil eden bir "ICorDebugThreadEnum" Nesne adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8245a-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8245a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8245a-107">Remarks</span></span>  
 <span data-ttu-id="8245a-108">Bir iş parçacığı sonra etkin olarak kabul edilir [Icordebugmanagedcallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) geri gönderilir ve önce [Icordebugmanagedcallback::exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) geri gönderilir .</span><span class="sxs-lookup"><span data-stu-id="8245a-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="8245a-109">Yönetilen iş parçacığı kendi yığınını üzerinde herhangi bir yönetilen çerçeve mutlaka olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8245a-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="8245a-110">İş parçacıkları numaralandırılan olsanız bile [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="8245a-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="8245a-111">Doğal olarak sabit listesi boş olur.</span><span class="sxs-lookup"><span data-stu-id="8245a-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8245a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8245a-112">Requirements</span></span>  
 <span data-ttu-id="8245a-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8245a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8245a-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8245a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8245a-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8245a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8245a-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8245a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8245a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8245a-117">See also</span></span>

