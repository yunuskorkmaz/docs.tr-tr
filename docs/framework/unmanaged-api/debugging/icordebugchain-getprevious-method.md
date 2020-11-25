---
title: ICorDebugChain::GetPrevious Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: 326e170fa98c9e365f9b68bedb585f547ca207ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727711"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="43de2-102">ICorDebugChain::GetPrevious Metodu</span><span class="sxs-lookup"><span data-stu-id="43de2-102">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="43de2-103">İş parçacığı için önceki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="43de2-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43de2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="43de2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43de2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43de2-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="43de2-106">dışı Bu iş parçacığı için önceki çerçeve zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43de2-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="43de2-107">Bu zincir ilk zincirdir, `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="43de2-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43de2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43de2-108">Requirements</span></span>  

 <span data-ttu-id="43de2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43de2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43de2-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="43de2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43de2-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="43de2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43de2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43de2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
