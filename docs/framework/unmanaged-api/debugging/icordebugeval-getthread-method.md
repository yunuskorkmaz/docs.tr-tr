---
title: ICorDebugEval::GetThread Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64cc5b6e7c6fe44080b35dc07f029ad311b88ca7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489390"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="3d07d-102">ICorDebugEval::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="3d07d-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="3d07d-103">Bu değerlendirme yürütülüyor veya çalıştırır iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="3d07d-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d07d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d07d-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d07d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d07d-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="3d07d-106">[out] İş parçacığını temsil eden bir Icordebugthread nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d07d-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d07d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d07d-107">Requirements</span></span>  
 <span data-ttu-id="3d07d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d07d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d07d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d07d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d07d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d07d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d07d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d07d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
