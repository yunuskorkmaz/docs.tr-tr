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
ms.openlocfilehash: 390a2c64508bf407296d318a47bfd2972b7ef9d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762556"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="c3ecc-102">ICorDebugThread::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="c3ecc-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="c3ecc-103">Bir arabirim işaretçisini bu Icordebugthread nesne üzerinde etkin (en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="c3ecc-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ecc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3ecc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ecc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3ecc-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c3ecc-106">[out] Çerçeveyi temsil eden bir Icordebugframe arabirimi nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3ecc-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ecc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3ecc-107">Remarks</span></span>  
 <span data-ttu-id="c3ecc-108">`ppFrame` Parametredir çerçeve şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="c3ecc-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ecc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ecc-109">Requirements</span></span>  
 <span data-ttu-id="c3ecc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ecc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ecc-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3ecc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3ecc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3ecc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ecc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ecc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
