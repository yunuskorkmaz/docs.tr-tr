---
title: ICorDebugChain::GetNext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 990786fbb3cc853f7f399d60fa686bb5d60018af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745703"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="2578c-102">ICorDebugChain::GetNext Metodu</span><span class="sxs-lookup"><span data-stu-id="2578c-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="2578c-103">Çerçeve sonraki zincirini iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="2578c-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2578c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2578c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2578c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2578c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="2578c-106">[out] İş parçacığı için çerçeve sonraki zincirini temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2578c-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="2578c-107">Bu zincir son zinciri ise `ppChain` null.</span><span class="sxs-lookup"><span data-stu-id="2578c-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2578c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2578c-108">Requirements</span></span>  
 <span data-ttu-id="2578c-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2578c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2578c-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2578c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2578c-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2578c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2578c-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2578c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
