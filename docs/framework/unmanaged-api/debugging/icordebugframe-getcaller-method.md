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
ms.openlocfilehash: b29de0b70daa783197e78fe985d379d4124bc140
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205143"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="77937-102">ICorDebugFrame::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="77937-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="77937-103">Bu çerçeveyi çağıran geçerli zincirde ICorDebugFrame nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="77937-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77937-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77937-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77937-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77937-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="77937-106">dışı `ICorDebugFrame`Çağırma çerçevesini temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="77937-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="77937-107">Çağrılan çerçeve geçerli zincirde en dıştaki çerçevedir ise bu değer null olur.</span><span class="sxs-lookup"><span data-stu-id="77937-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77937-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77937-108">Requirements</span></span>  
 <span data-ttu-id="77937-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77937-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77937-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77937-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77937-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="77937-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77937-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77937-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
