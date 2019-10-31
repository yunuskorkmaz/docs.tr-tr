---
title: ICorDebugFrame::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: 843399b7e3de522e2c4574963897430aa60a5a50
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114790"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="7b82d-102">ICorDebugFrame::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="7b82d-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="7b82d-103">Bu çerçeveyi çağıran geçerli zincirde ICorDebugFrame nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="7b82d-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b82d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b82d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b82d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b82d-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="7b82d-106">dışı Çağırma çerçevesini temsil eden bir `ICorDebugFrame` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b82d-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="7b82d-107">Çağrılan çerçeve geçerli zincirde en dıştaki çerçevedir ise bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="7b82d-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b82d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b82d-108">Requirements</span></span>  
 <span data-ttu-id="7b82d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b82d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b82d-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b82d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b82d-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7b82d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b82d-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b82d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
