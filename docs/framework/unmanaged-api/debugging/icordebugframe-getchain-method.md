---
title: ICorDebugFrame::GetChain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032c1e3dcfe50cd30953ca581ff9f0d83b78518d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488489"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="ee4fe-102">ICorDebugFrame::GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee4fe-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="ee4fe-103">Bu çerçeve parçasıdır zinciri için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ee4fe-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee4fe-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee4fe-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ee4fe-106">[out] Bu çerçeveyi içeren zincirini temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ee4fe-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4fe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee4fe-107">Requirements</span></span>  
 <span data-ttu-id="ee4fe-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee4fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4fe-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee4fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee4fe-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee4fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee4fe-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
