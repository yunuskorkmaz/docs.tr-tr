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
ms.openlocfilehash: 75b97f4333f3e81533b1f10b8c3c7ba6197ac94a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730090"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="a56c1-102">ICorDebugChain::GetNext Metodu</span><span class="sxs-lookup"><span data-stu-id="a56c1-102">ICorDebugChain::GetNext Method</span></span>

<span data-ttu-id="a56c1-103">İş parçacığı için bir sonraki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="a56c1-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a56c1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a56c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a56c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a56c1-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="a56c1-106">dışı İş parçacığı için bir sonraki çerçeve zincirini temsil eden ıcordebugzincirine ait adrese yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a56c1-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="a56c1-107">Bu zincir son zincirdir, `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="a56c1-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a56c1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a56c1-108">Requirements</span></span>  

 <span data-ttu-id="a56c1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a56c1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a56c1-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a56c1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a56c1-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a56c1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a56c1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56c1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
