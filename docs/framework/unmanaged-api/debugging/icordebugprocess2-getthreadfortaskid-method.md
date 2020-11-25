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
ms.openlocfilehash: 2b18289af460f64085fedd7b32387ebcb8c51715
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713554"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="296ce-102">ICorDebugProcess2::GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="296ce-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="296ce-103">Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="296ce-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296ce-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="296ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="296ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="296ce-105">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="296ce-106">'ndaki Görevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="296ce-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="296ce-107">dışı Alınacak iş parçacığını temsil eden bir ICorDebugThread2 nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="296ce-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="296ce-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="296ce-108">Remarks</span></span>  

 <span data-ttu-id="296ce-109">Konak, [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) metodunu kullanarak görev tanımlayıcısını ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="296ce-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296ce-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="296ce-110">Requirements</span></span>  

 <span data-ttu-id="296ce-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="296ce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="296ce-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="296ce-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="296ce-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="296ce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="296ce-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="296ce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
