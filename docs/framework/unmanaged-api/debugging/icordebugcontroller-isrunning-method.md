---
title: ICorDebugController::IsRunning Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5eae9e14bcd0ca430f03a873818246896438463
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749273"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="3e76b-102">ICorDebugController::IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e76b-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="3e76b-103">İşlemdeki iş parçacıkları şu anda özgürce çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3e76b-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e76b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e76b-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e76b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e76b-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="3e76b-106">[out] Bir değer için bir işaretçi `true` serbestçe; Aksi takdirde, işlemdeki iş parçacıkları çalıştırıyorsanız, `false`.</span><span class="sxs-lookup"><span data-stu-id="3e76b-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e76b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e76b-107">Requirements</span></span>  
 <span data-ttu-id="3e76b-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e76b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e76b-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e76b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e76b-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e76b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e76b-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e76b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e76b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e76b-112">See also</span></span>
