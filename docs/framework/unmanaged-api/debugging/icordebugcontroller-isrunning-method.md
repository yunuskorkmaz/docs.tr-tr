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
ms.openlocfilehash: 89ea9f221ad55063e4186cc27cc8038334d800d4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892872"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="40bbc-102">ICorDebugController::IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40bbc-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="40bbc-103">İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="40bbc-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40bbc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40bbc-104">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40bbc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40bbc-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="40bbc-106">dışı İşlemdeki iş parçacıkları serbestçe çalışıyorsa bir değere `true` yönelik işaretçi. Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="40bbc-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40bbc-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40bbc-107">Requirements</span></span>  
 <span data-ttu-id="40bbc-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40bbc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40bbc-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40bbc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40bbc-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40bbc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40bbc-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40bbc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bbc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40bbc-112">See also</span></span>
