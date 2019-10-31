---
title: ICorDebugChain::GetReason Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: e51ee2e4d44af547c82a21a782121976d07118c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124724"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="1a9b0-102">ICorDebugChain::GetReason Metodu</span><span class="sxs-lookup"><span data-stu-id="1a9b0-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="1a9b0-103">Bu çağrı zincirinin Genesin nedenini alır.</span><span class="sxs-lookup"><span data-stu-id="1a9b0-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a9b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a9b0-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="1a9b0-106">dışı Bu çağrı zincirinin Genesin nedenini gösteren bir değer işaretçisi (bit düzeyinde bir bileşim).</span><span class="sxs-lookup"><span data-stu-id="1a9b0-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a9b0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a9b0-107">Requirements</span></span>  
 <span data-ttu-id="1a9b0-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9b0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9b0-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a9b0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a9b0-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a9b0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a9b0-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a9b0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
