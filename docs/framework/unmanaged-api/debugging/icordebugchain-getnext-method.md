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
ms.openlocfilehash: 132734dfb6ba9d70836638ab67564fc215e9bc40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192120"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="6ba89-102">ICorDebugChain::GetNext Metodu</span><span class="sxs-lookup"><span data-stu-id="6ba89-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="6ba89-103">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="6ba89-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ba89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ba89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ba89-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="6ba89-106">dışı İş parçacığı için bir sonraki çerçeve zincirini temsil eden ıcordebugzincirine ait adrese yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ba89-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="6ba89-107">Bu zincir son zincirdir `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="6ba89-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ba89-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ba89-108">Requirements</span></span>  
 <span data-ttu-id="6ba89-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ba89-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ba89-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ba89-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ba89-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ba89-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ba89-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba89-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
