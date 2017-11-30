---
title: "ICorDebugController::EnumerateThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.EnumerateThreads
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7575bf2b50f11fab1c14f8fb28dc65e079c21de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="93a97-102">ICorDebugController::EnumerateThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93a97-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="93a97-103">Bir numaralandırıcı etkin yönetilen iş parçacığı için işlem sırasında alır.</span><span class="sxs-lookup"><span data-stu-id="93a97-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93a97-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93a97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93a97-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="93a97-106">[out] Bir işaretçi adresine "ICorDebugThreadEnum" nesnenin işlemde etkin olan tüm yönetilen iş parçacığı için bir numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93a97-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93a97-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93a97-107">Remarks</span></span>  
 <span data-ttu-id="93a97-108">Bir iş parçacığı sonra etkin olarak kabul [Icordebugmanagedcallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) geri çağırma gönderilir ve önce [Icordebugmanagedcallback::exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) geri çağırma gönderilir .</span><span class="sxs-lookup"><span data-stu-id="93a97-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="93a97-109">Yönetilen iş parçacığı mutlaka herhangi bir yönetilen çerçeve kendi yığına sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="93a97-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="93a97-110">İş parçacığı numaralandırılan bile önce [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="93a97-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="93a97-111">Numaralandırma doğal olarak boş olur.</span><span class="sxs-lookup"><span data-stu-id="93a97-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a97-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93a97-112">Requirements</span></span>  
 <span data-ttu-id="93a97-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a97-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a97-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93a97-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a97-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93a97-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a97-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a97-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a97-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93a97-117">See Also</span></span>  
 
