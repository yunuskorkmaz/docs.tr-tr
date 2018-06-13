---
title: ICorDebugThread2::GetTaskID Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5690856b526bf0f7bc4527d04ae8044cda1f6e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417872"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="dc785-102">ICorDebugThread2::GetTaskID Metodu</span><span class="sxs-lookup"><span data-stu-id="dc785-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="dc785-103">Bu iş parçacığı üzerinde çalışan görev tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="dc785-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc785-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc785-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc785-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc785-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="dc785-106">[out] Bu Icordebugthread2 nesnesinin temsil ettiği iş parçacığı üzerinde çalışan görev tanımlayıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc785-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc785-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc785-107">Remarks</span></span>  
 <span data-ttu-id="dc785-108">Bir görev, yalnızca iş parçacığı bir bağlantı ile ilişkili ise iş parçacığı üzerinde çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc785-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="dc785-109">`GetTaskID` döndürür sıfır `pTaskId` iş parçacığı bir bağlantıyla ilişkili değilse.</span><span class="sxs-lookup"><span data-stu-id="dc785-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc785-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc785-110">Requirements</span></span>  
 <span data-ttu-id="dc785-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc785-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc785-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc785-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc785-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc785-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc785-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc785-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
