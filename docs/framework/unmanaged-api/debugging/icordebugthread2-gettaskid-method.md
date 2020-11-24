---
title: ICorDebugThread2::GetTaskID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 9b17a179745af65bde05527bd0157f3ce06c12c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678681"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="22e08-102">ICorDebugThread2::GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22e08-102">ICorDebugThread2::GetTaskID Method</span></span>

<span data-ttu-id="22e08-103">Bu iş parçacığında çalışan görevin tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="22e08-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22e08-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="22e08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22e08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22e08-105">Parameters</span></span>  

 `pTaskId`  
 <span data-ttu-id="22e08-106">dışı Bu ICorDebugThread2 nesnesi tarafından temsil edilen iş parçacığında çalışan görevin tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22e08-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22e08-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22e08-107">Remarks</span></span>  

 <span data-ttu-id="22e08-108">Bir görev iş parçacığı üzerinde yalnızca iş parçacığı bağlantıyla ilişkilendirildiğinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="22e08-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="22e08-109">`GetTaskID``pTaskId`iş parçacığı bir bağlantıyla ilişkilendirilmediği takdirde, içinde sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="22e08-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22e08-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22e08-110">Requirements</span></span>  

 <span data-ttu-id="22e08-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22e08-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22e08-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22e08-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22e08-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22e08-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22e08-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
