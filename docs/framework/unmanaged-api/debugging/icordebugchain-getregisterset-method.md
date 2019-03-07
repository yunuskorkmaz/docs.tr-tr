---
title: ICorDebugChain::GetRegisterSet Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366a40e1e3cd196f480c5849c49419c7daeea9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480994"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="b7526-102">ICorDebugChain::GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7526-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="b7526-103">Bu zincir etkin parçası için kaydı alır.</span><span class="sxs-lookup"><span data-stu-id="b7526-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7526-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7526-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7526-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7526-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="b7526-106">[out] Adresine bir işaretçi bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) kasayı temsil eden nesne bu zincir etkin parçası için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7526-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7526-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7526-107">Requirements</span></span>  
 <span data-ttu-id="b7526-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7526-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7526-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7526-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7526-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7526-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7526-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7526-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
