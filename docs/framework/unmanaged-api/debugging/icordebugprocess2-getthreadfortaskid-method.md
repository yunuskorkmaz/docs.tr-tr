---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess2:: GetThreadForTaskID yöntemi'
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
ms.openlocfilehash: aafb1223f6e2e73aae600fd482c76b84c57dae52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650137"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="befe1-103">ICorDebugProcess2::GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="befe1-103">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="befe1-104">Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="befe1-104">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befe1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="befe1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="befe1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="befe1-106">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="befe1-107">'ndaki Görevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="befe1-107">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="befe1-108">dışı Alınacak iş parçacığını temsil eden bir ICorDebugThread2 nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="befe1-108">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="befe1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="befe1-109">Remarks</span></span>  

 <span data-ttu-id="befe1-110">Konak, [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) metodunu kullanarak görev tanımlayıcısını ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="befe1-110">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="befe1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="befe1-111">Requirements</span></span>  

 <span data-ttu-id="befe1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="befe1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="befe1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="befe1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="befe1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="befe1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="befe1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="befe1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
