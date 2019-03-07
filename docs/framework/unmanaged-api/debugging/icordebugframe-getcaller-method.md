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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82902e6a395fe62464065ccea4cca5b52c960f0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492224"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="703c3-102">ICorDebugFrame::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="703c3-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="703c3-103">Bir işaretçi olarak adlandırılan bu çerçeveyi geçerli zincirinde Icordebugframe nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="703c3-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="703c3-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="703c3-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="703c3-106">[out] Adresine bir işaretçi bir `ICorDebugFrame` çağıran çerçeveyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="703c3-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="703c3-107">Bu değer, çağrılan çerçeveyi geçerli zincirindeki en dıştaki çerçeve ise null olur.</span><span class="sxs-lookup"><span data-stu-id="703c3-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703c3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="703c3-108">Requirements</span></span>  
 <span data-ttu-id="703c3-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703c3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703c3-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="703c3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="703c3-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="703c3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703c3-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703c3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
