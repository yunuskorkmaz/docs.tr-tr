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
ms.openlocfilehash: d6ee36ac4d4510637e5f8240c3b8930a9bec7970
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123840"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="b829c-102">ICorDebugChain::GetRegisterSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b829c-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="b829c-103">Bu zincirin etkin bölümü için kayıt kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="b829c-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b829c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b829c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b829c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b829c-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="b829c-106">dışı Bu zincirin etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b829c-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b829c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b829c-107">Requirements</span></span>  
 <span data-ttu-id="b829c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b829c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b829c-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b829c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b829c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b829c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b829c-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b829c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
