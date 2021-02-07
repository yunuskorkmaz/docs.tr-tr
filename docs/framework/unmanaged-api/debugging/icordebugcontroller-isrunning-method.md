---
description: ': ICorDebugController:: IsRunning yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6a0628cc39765d9cb295877d912d92dbb27937da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764586"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="d0d3e-103">ICorDebugController::IsRunning Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0d3e-103">ICorDebugController::IsRunning Method</span></span>

<span data-ttu-id="d0d3e-104">İşlemdeki iş parçacıklarının Şu anda serbestçe çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d0d3e-104">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d3e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0d3e-105">Syntax</span></span>  
  
```cpp  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d3e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0d3e-106">Parameters</span></span>  

 `pbRunning`  
 <span data-ttu-id="d0d3e-107">dışı `true` İşlemdeki iş parçacıkları serbestçe çalışıyorsa bir değere yönelik işaretçi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="d0d3e-107">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d3e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0d3e-108">Requirements</span></span>  

 <span data-ttu-id="d0d3e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d3e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d3e-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0d3e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0d3e-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0d3e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0d3e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d3e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d3e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0d3e-113">See also</span></span>
