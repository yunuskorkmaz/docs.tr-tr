---
title: ICorDebugThread::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 051491173bbcef3d87d9a3dbe854eece46c49e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468786"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="96097-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="96097-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="96097-103">Bir arabirim işaretçisini bu Icordebugthread nesne üzerinde etkin (en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="96097-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96097-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96097-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96097-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96097-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="96097-106">[out] Çerçeveyi temsil eden bir Icordebugframe arabirimi nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96097-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96097-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96097-107">Remarks</span></span>  
 <span data-ttu-id="96097-108">`ppFrame` Parametredir çerçeve şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="96097-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96097-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96097-109">Requirements</span></span>  
 <span data-ttu-id="96097-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96097-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96097-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96097-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96097-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96097-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96097-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96097-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
