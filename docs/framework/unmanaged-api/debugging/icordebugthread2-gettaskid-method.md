---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: getTaskId yöntemi'
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
ms.openlocfilehash: 5429daee9150d63834c747dd5ebb763dd6f0da6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658704"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="13467-103">ICorDebugThread2::GetTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13467-103">ICorDebugThread2::GetTaskID Method</span></span>

<span data-ttu-id="13467-104">Bu iş parçacığında çalışan görevin tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="13467-104">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13467-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13467-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13467-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13467-106">Parameters</span></span>  

 `pTaskId`  
 <span data-ttu-id="13467-107">dışı Bu ICorDebugThread2 nesnesi tarafından temsil edilen iş parçacığında çalışan görevin tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13467-107">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13467-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13467-108">Remarks</span></span>  

 <span data-ttu-id="13467-109">Bir görev iş parçacığı üzerinde yalnızca iş parçacığı bağlantıyla ilişkilendirildiğinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="13467-109">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="13467-110">`GetTaskID``pTaskId`iş parçacığı bir bağlantıyla ilişkilendirilmediği takdirde, içinde sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="13467-110">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13467-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13467-111">Requirements</span></span>  

 <span data-ttu-id="13467-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13467-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13467-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="13467-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13467-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="13467-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13467-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13467-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
