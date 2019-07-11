---
title: ICorDebugProcess2::GetThreadForTaskID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85040a31966a92ead6ca4786f62852f17923056
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736926"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="28b2a-102">ICorDebugProcess2::GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28b2a-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="28b2a-103">Belirtilen tanımlayıcıya sahip görev yürütülmekte olan iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="28b2a-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28b2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28b2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28b2a-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="28b2a-106">[in] Görev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="28b2a-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="28b2a-107">[out] Alınacak iş parçacığını temsil eden bir Icordebugthread2 nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="28b2a-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28b2a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28b2a-108">Remarks</span></span>  
 <span data-ttu-id="28b2a-109">Ana bilgisayar kullanarak görev tanımlayıcısı ayarlayabilirsiniz [Iclrtask::settaskıdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28b2a-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28b2a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28b2a-110">Requirements</span></span>  
 <span data-ttu-id="28b2a-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b2a-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28b2a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28b2a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28b2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28b2a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28b2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
